<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>To-Do List</title>
  <style>
    body {
      font-family: "Poppins", sans-serif;
      background: #f8f9fa;
      display: flex;
      justify-content: center;
      align-items: flex-start;
      min-height: 100vh;
      margin: 0;
      padding-top: 50px;
    }
    .todo-container {
      background: white;
      width: 350px;
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    }
    h1 {
      text-align: center;
      color: #333;
    }
    .input-section {
      display: flex;
      gap: 10px;
      margin-bottom: 15px;
    }
    input {
      flex: 1;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 8px;
      font-size: 14px;
    }
    button {
      background: #007bff;
      color: white;
      border: none;
      border-radius: 8px;
      padding: 10px 15px;
      cursor: pointer;
      transition: 0.3s;
    }
    button:hover {
      background: #0056b3;
    }
    ul {
      list-style: none;
      padding: 0;
    }
    li {
      display: flex;
      justify-content: space-between;
      align-items: center;
      background: #f1f1f1;
      margin-bottom: 8px;
      padding: 10px;
      border-radius: 8px;
      font-size: 15px;
    }
    li.completed {
      text-decoration: line-through;
      color: gray;
    }
    .delete-btn {
      background: #dc3545;
      border: none;
      color: white;
      padding: 5px 10px;
      border-radius: 5px;
      cursor: pointer;
    }
    .delete-btn:hover {
      background: #b02a37;
    }
  </style>
</head>
<body>
  <div class="todo-container">
    <h1>To-Do List</h1>
    <div class="input-section">
      <input type="text" id="taskInput" placeholder="Add new task..." />
      <button onclick="addTask()">Add</button>
    </div>
    <ul id="taskList"></ul>
  </div>

  <script>
    const taskInput = document.getElementById("taskInput");
    const taskList = document.getElementById("taskList");

    function addTask() {
      const taskText = taskInput.value.trim();
      if (taskText === "") return alert("Please enter a task!");

      const li = document.createElement("li");
      li.textContent = taskText;

      li.addEventListener("click", () => {
        li.classList.toggle("completed");
      });

      const deleteBtn = document.createElement("button");
      deleteBtn.textContent = "Delete";
      deleteBtn.className = "delete-btn";
      deleteBtn.addEventListener("click", (e) => {
        e.stopPropagation();
        li.remove();
      });

      li.appendChild(deleteBtn);
      taskList.appendChild(li);
      taskInput.value = "";
    }
  </script>
</body>
</html>
