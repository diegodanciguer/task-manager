# Task Manager

![Task Manager](https://via.placeholder.com/800x400.png?text=Task+Manager)

## Description

**Task Manager** is a web application developed in Laravel and Vue.js to manage tasks. It allows you to create, edit, delete, and mark tasks as completed. Tasks are organized into two tabs: "Pending" and "Completed", making it easy to view and manage tasks.

## Features

- **Add Tasks:** Create new tasks with title, description, and due date.
- **Edit Tasks:** Edit existing task information.
- **Delete Tasks:** Remove tasks that are no longer needed.
- **Mark as Completed:** Mark tasks as completed and move them to the "Completed" tab.
- **Tab View:** View pending and completed tasks in separate tabs.

## Technologies Used

- **Backend:** Laravel
- **Frontend:** Vue.js
- **Styling:** Tailwind CSS
- **Animations:** Animate.css

## Installation

Follow the steps below to set up the project locally:

### Prerequisites

- PHP >= 7.3
- Composer
- Node.js
- NPM

### Step by Step

1. **Clone the repository:**

    ```bash
    git clone https://github.com/diodanciguer/task-manager
    cd <repository>
    ```

2. **Install PHP dependencies:**

    ```bash
    composer install
    ```

3. **Install Node.js dependencies:**

    ```bash
    npm install
    ```

4. **Copy the [`.env.example`](command:_github.copilot.openRelativePath?%5B%7B%22scheme%22%3A%22file%22%2C%22authority%22%3A%22%22%2C%22path%22%3A%22%2FC%3A%2FUsers%2Fdiego%2FDocuments%2FGitHub%2Ftask-manager%2F.env.example%22%2C%22query%22%3A%22%22%2C%22fragment%22%3A%22%22%7D%5D "c:\Users\diego\Documents\GitHub\task-manager\.env.example") file to [`.env`](command:_github.copilot.openRelativePath?%5B%7B%22scheme%22%3A%22file%22%2C%22authority%22%3A%22%22%2C%22path%22%3A%22%2FC%3A%2FUsers%2Fdiego%2FDocuments%2FGitHub%2Ftask-manager%2F.env%22%2C%22query%22%3A%22%22%2C%22fragment%22%3A%22%22%7D%5D "c:\Users\diego\Documents\GitHub\task-manager\.env") and configure your environment variables:**

    ```bash
    cp .env.example .env
    ```

5. **Generate the application key:**

    ```bash
    php artisan key:generate
    ```

6. **Run the database migrations:**

    ```bash
    php artisan migrate
    ```

7. **Compile the frontend assets:**

    ```bash
    npm run dev
    ```

8. **Start the development server:**

    ```bash
    php artisan serve
    ```

9. **Access the application in your browser:**

    ```
    http://127.0.0.1:8000
    ```

## Screenshots

### Pending Tasks Screen

![Pending Tasks](https://via.placeholder.com/800x400.png?text=Pending+Tasks)

### Completed Tasks Screen

![Completed Tasks](https://via.placeholder.com/800x400.png?text=Completed+Tasks)

## Contribution

Contributions are welcome! Feel free to open issues and pull requests.

## License

This project is licensed under the [MIT License](LICENSE).

---

Made with ❤️ by [Diego Danciguer](https://github.com/diegodanciguer)






## Portugues

# Task Manager

![Task Manager](https://via.placeholder.com/800x400.png?text=Task+Manager)

## Descrição

O **Task Manager** é uma aplicação web desenvolvida em Laravel e Vue.js para gerenciar tarefas. Ele permite criar, editar, excluir e marcar tarefas como concluídas. As tarefas são organizadas em duas abas: "Pending" e "Completed", facilitando a visualização e o gerenciamento das tarefas.

## Funcionalidades

- **Adicionar Tarefas:** Crie novas tarefas com título, descrição e data de vencimento.
- **Editar Tarefas:** Edite as informações das tarefas existentes.
- **Excluir Tarefas:** Remova tarefas que não são mais necessárias.
- **Marcar como Concluída:** Marque tarefas como concluídas e mova-as para a aba "Completed".
- **Visualização por Abas:** Visualize tarefas pendentes e concluídas em abas separadas.

## Tecnologias Utilizadas

- **Backend:** Laravel
- **Frontend:** Vue.js
- **Estilização:** Tailwind CSS
- **Animações:** Animate.css

## Instalação

Siga os passos abaixo para configurar o projeto localmente:

### Pré-requisitos

- PHP >= 7.3
- Composer
- Node.js
- NPM

### Passo a Passo

1. **Clone o repositório:**

    ```bash
    git clone https://github.com/diodanciguer/task-manager.git
    cd <repository>
    ```

2. **Instale as dependências do PHP:**

    ```bash
    composer install
    ```

3. **Instale as dependências do Node.js:**

    ```bash
    npm install
    ```

4. **Copie o arquivo `.env.example` para `.env` e configure suas variáveis de ambiente:**

    ```bash
    cp .env.example .env
    ```

5. **Gere a chave da aplicação:**

    ```bash
    php artisan key:generate
    ```

6. **Execute as migrações do banco de dados:**

    ```bash
    php artisan migrate
    ```

7. **Compile os assets do frontend:**

    ```bash
    npm run dev
    ```

8. **Inicie o servidor de desenvolvimento:**

    ```bash
    php artisan serve
    ```

9. **Acesse a aplicação no navegador:**

    ```
    http://127.0.0.1:8000
    ```

## Capturas de Tela

### Tela de Tarefas Pendentes

![Pending Tasks](https://via.placeholder.com/800x400.png?text=Pending+Tasks)

### Tela de Tarefas Concluídas

![Completed Tasks](https://via.placeholder.com/800x400.png?text=Completed+Tasks)

## Contribuição

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues e pull requests.

## Licença

Este projeto está licenciado sob a [MIT License](LICENSE).

---

Feito com ❤️ por [Diego Danciguer](https://github.com/diegodanciguer)
