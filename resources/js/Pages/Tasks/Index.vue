<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head, Link } from '@inertiajs/vue3';
import { ref } from 'vue';
import axios from 'axios';

const props = defineProps({
    pendingTasks: Array,
    completedTasks: Array,
});

const activeTab = ref('pending');

const markAsComplete = async (task) => {
    try {
        const response = await axios.post(`/tasks/${task.id}/complete`);
        if (response.data.success) {
            task.completed = true;
            // Remova a tarefa da lista de tarefas pendentes
            const index = props.pendingTasks.findIndex(t => t.id === task.id);
            if (index !== -1) {
                props.pendingTasks.splice(index, 1);
            }
            // Adicione a tarefa à lista de tarefas concluídas
            props.completedTasks.push(task);
        }
    } catch (error) {
        console.error('Error marking task as complete:', error);
    }
};
</script>

<template>
    <Head title="Tasks" />
    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">Tasks</h2>
        </template>
        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
                    <div class="p-6 bg-white border-b border-gray-200">
                        <div class="mb-4">
                            <button @click="activeTab = 'pending'" :class="{'bg-gray-200': activeTab === 'pending'}" class="px-4 py-2">Pending</button>
                            <button @click="activeTab = 'completed'" :class="{'bg-gray-200': activeTab === 'completed'}" class="px-4 py-2">Completed</button>
                        </div>
                        <table class="min-w-full">
                            <thead>
                                <tr>
                                    <th class="py-2 px-4 border-b">Title</th>
                                    <th class="py-2 px-4 border-b">Description</th>
                                    <th class="py-2 px-4 border-b">Due Date</th>
                                    <th class="py-2 px-4 border-b">Status</th>
                                    <th class="py-2 px-4 border-b">Actions</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr v-for="task in (activeTab === 'pending' ? props.pendingTasks : props.completedTasks)" :key="task.id">
                                    <td class="py-2 px-4 border-b">{{ task.title }}</td>
                                    <td class="py-2 px-4 border-b">{{ task.description }}</td>
                                    <td class="py-2 px-4 border-b">{{ task.due_date }}</td>
                                    <td class="py-2 px-4 border-b">{{ task.completed ? 'Completed' : 'Pending' }}</td>
                                    <td class="py-2 px-4 border-b">
                                        <Link :href="`/tasks/${task.id}/edit`" class="px-4 py-2 bg-yellow-500 text-white rounded-md mr-2">Edit</Link>
                                        <form :action="`/tasks/${task.id}`" method="POST" class="inline">
                                            <input type="hidden" name="_method" value="DELETE">
                                            <input type="hidden" name="_token" :value="csrfToken">
                                            <button type="submit" class="px-4 py-2 bg-red-600 text-white rounded-md">Delete</button>
                                        </form>
                                        <button @click="markAsComplete(task)" class="px-4 py-2 bg-green-600 text-white rounded-md" :disabled="task.completed">Complete</button>
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>