<script setup>
import 'animate.css';
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
            task.animation = 'animate__animated animate__fadeOut';
            setTimeout(() => {
                task.animation = ''; // Remove a classe de animação
                props.pendingTasks = props.pendingTasks.filter(t => t.id !== task.id);
                props.completedTasks.push({ ...task, animation: '' }); // Adiciona a tarefa sem animação
            }, 1000); // Tempo da animação
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
                    <div class="p-6 text-gray-900">
                        <div class="flex justify-between items-center mb-6">
                            <h3 class="text-lg font-semibold">Task List</h3>
                            <Link href="/tasks/create" class="px-4 py-2 bg-blue-600 text-white rounded-md">Create Task</Link>
                        </div>
                        <div class="mb-4">
                            <button @click="activeTab = 'pending'" :class="{'bg-gray-200': activeTab === 'pending'}" class="px-4 py-2 mr-2">Pending</button>
                            <button @click="activeTab = 'completed'" :class="{'bg-gray-200': activeTab === 'completed'}" class="px-4 py-2">Completed</button>
                        </div>
                        <table class="min-w-full bg-white" v-if="activeTab === 'pending'">
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
                                <tr v-for="task in pendingTasks" :key="task.id" :class="task.animation">
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
                        <table class="min-w-full bg-white" v-if="activeTab === 'completed'">
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
                                <tr v-for="task in completedTasks" :key="task.id">
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