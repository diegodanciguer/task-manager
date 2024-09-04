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
