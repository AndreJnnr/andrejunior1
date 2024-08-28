# andrejunior1

# Gerenciador de Tarefas

Este é um projeto simples de gerenciador de tarefas, onde você pode adicionar, visualizar, marcar como concluídas e remover tarefas.

## Como Rodar o Projeto

1. **Clone o Repositório:**
2. Navegue até o diretório do projeto cd task-manager
3. Abra o Arquivo index.html em um Navegador através dos comandos: open index.html  # Para macOS, start index.html # Para Windows, xdg-open index.html # Para Linux
4. Estrutura do projeto: index.html: O arquivo HTML principal que contém a estrutura da aplicação, styles.css: Arquivo CSS para estilização da aplicação,script.js: Arquivo JavaScript para lógica e interatividade da aplicação.
5. Funcionalidades:Adicionar novas tarefas, marcar tarefas como concluídas e remover tarefas.

```bash
git clone https://github.com/AndreJnnr/andrejunior1


TESTE
task-manager/
│
├── index.html
├── styles.css
├── script.js
└── README.md


<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gerenciador de Tarefas</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>Gerenciador de Tarefas</h1>
        <input type="text" id="taskInput" placeholder="Digite uma nova tarefa...">
        <button id="addTaskButton">Adicionar Tarefa</button>
        <ul id="taskList"></ul>
    </div>
    <script src="script.js"></script>
</body>
</html>


body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}

.container {
    background: #fff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
    width: 100%;
    max-width: 600px;
}

h1 {
    font-size: 24px;
    margin-bottom: 20px;
}

input[type="text"] {
    width: calc(100% - 110px);
    padding: 10px;
    margin-right: 10px;
    border: 1px solid #ddd;
    border-radius: 4px;
}

button {
    padding: 10px 15px;
    background-color: #28a745;
    border: none;
    color: #fff;
    border-radius: 4px;
    cursor: pointer;
}

button:hover {
    background-color: #218838;
}

ul {
    list-style: none;
    padding: 0;
}

li {
    padding: 10px;
    border-bottom: 1px solid #ddd;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

li.completed {
    text-decoration: line-through;
    color: #6c757d;
}

button.remove {
    background-color: #dc3545;
}

button.remove:hover {
    background-color: #c82333;
}


document.addEventListener('DOMContentLoaded', () => {
    const taskInput = document.getElementById('taskInput');
    const addTaskButton = document.getElementById('addTaskButton');
    const taskList = document.getElementById('taskList');

    // Função para adicionar tarefa
    function addTask() {
        const taskText = taskInput.value.trim();
        if (taskText === '') return;

        const li = document.createElement('li');
        li.innerHTML = `
            <span>${taskText}</span>
            <button class="complete">Concluir</button>
            <button class="remove">Remover</button>
        `;

        // Evento de concluir tarefa
        li.querySelector('.complete').addEventListener('click', () => {
            li.classList.toggle('completed');
        });

        // Evento de remover tarefa
        li.querySelector('.remove').addEventListener('click', () => {
            taskList.removeChild(li);
        });

        taskList.appendChild(li);
        taskInput.value = '';
    }

    addTaskButton.addEventListener('click', addTask);

    // Adiciona a tarefa com Enter
    taskInput.addEventListener('keypress', (e) => {
        if (e.key === 'Enter') {
            addTask();
        }
    });
});


