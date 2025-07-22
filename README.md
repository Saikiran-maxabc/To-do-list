# To-do-list
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>My Interactive Site</title>
  <style>
    :root {
      --main-color: #4caf50;
      --background-color: #f0f0f0;
    }

    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background-color: var(--background-color);
      color: #333;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 20px;
    }

    header {
      text-align: center;
      margin-bottom: 30px;
    }

    h1 {
      color: var(--main-color);
    }

    .controls {
      margin-bottom: 20px;
    }

    input[type="text"], button, select {
      padding: 10px;
      margin: 5px;
      border-radius: 5px;
      border: 1px solid #ccc;
    }

    button {
      background-color: var(--main-color);
      color: white;
      border: none;
      cursor: pointer;
    }

    ul {
      list-style-type: none;
      padding: 0;
    }

    li {
      padding: 8px;
      margin: 5px 0;
      background: white;
      border-radius: 5px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    li button {
      background-color: crimson;
    }
  </style>
</head>
<body>

  <header>
    <h1 id="greeting">Welcome!</h1>
    <div class="controls">
      <label for="nameInput">Your Name:</label>
      <input type="text" id="nameInput" placeholder="Enter name" />
      <button onclick="updateGreeting()">Set Name</button>
    </div>

    <div class="controls">
      <label for="themeSelect">Choose Theme:</label>
      <select id="themeSelect" onchange="changeTheme()">
        <option value="light">Light</option>
        <option value="dark">Dark</option>
        <option value="blue">Blue</option>
      </select>
    </div>
  </header>

  <section>
    <h2>My To-Do List</h2>
    <input type="text" id="todoInput" placeholder="New task..." />
    <button onclick="addTodo()">Add</button>
    <ul id="todoList"></ul>
  </section>

  <script>
    function updateGreeting() {
      const name = document.getElementById('nameInput').value || 'Friend';
      document.getElementById('greeting').innerText = `Welcome, ${name}!`;
    }

    function changeTheme() {
      const theme = document.getElementById('themeSelect').value;
      switch (theme) {
        case 'light':
          document.documentElement.style.setProperty('--main-color', '#4caf50');
          document.documentElement.style.setProperty('--background-color', '#f0f0f0');
          break;
        case 'dark':
          document.documentElement.style.setProperty('--main-color', '#ffffff');
          document.documentElement.style.setProperty('--background-color', '#121212');
          break;
        case 'blue':
          document.documentElement.style.setProperty('--main-color', '#2196f3');
          document.documentElement.style.setProperty('--background-color', '#e3f2fd');
          break;
      }
    }

    function addTodo() {
      const input = document.getElementById('todoInput');
      const task = input.value.trim();
      if (task === '') return;

      const li = document.createElement('li');
      li.innerHTML = `${task} <button onclick="removeTodo(this)">Remove</button>`;
      document.getElementById('todoList').appendChild(li);
      input.value = '';
    }

    function removeTodo(button) {
      button.parentElement.remove();
    }
  </script>
</body>
</html>
