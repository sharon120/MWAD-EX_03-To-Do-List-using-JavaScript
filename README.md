# MWAD-EX_03-To-Do-List-using-JavaScript
## Date:09-09-2025

## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM
### STEP 1
Build the HTML structure (index.html).

### STEP 2
Style the App (style.css).

### STEP 3
Plan the features the To-Do App should have.

### STEP 4
Create a To-do application using Javascript.

### STEP 5
Add functionalities.

### STEP 6
Test the App.

### STEP 7
Open the HTML file in a browser to check layout and functionality.

### STEP 8
Fix styling issues and refine content placement.

### STEP 9
Deploy the website.

### STEP 10
Upload to GitHub Pages for free hosting.

## PROGRAM:
## index.html:
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Todo Application</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="app-container">
    <h1>Todo Application</h1>
    <div class="input-section">
      <input type="text" id="taskInput" placeholder="Enter your task...">
      <button id="addBtn">Add Task</button>
    </div>
    <ul id="taskList"></ul>
  </div>
  <footer>
    <p>Developed by <strong>Your Name</strong> | Reg.No: <strong>123456</strong></p>
  </footer>
  <script src="script.js"></script>
</body>
</html>

```
## styles.css:
```
body {
  font-family: Arial, sans-serif;
  background: #f1f3f6;
  margin: 0;
  padding: 0;
}

.app-container {
  width: 400px;
  margin: 50px auto;
  background: white;
  padding: 20px;
  border-radius: 12px;
  box-shadow: 0px 4px 12px rgba(0,0,0,0.1);
}

h1 {
  text-align: center;
  color: #333;
}

.input-section {
  display: flex;
  gap: 10px;
}

#taskInput {
  flex: 1;
  padding: 10px;
  border: 1px solid #aaa;
  border-radius: 8px;
}

#addBtn {
  padding: 10px 15px;
  background: #28a745;
  border: none;
  border-radius: 8px;
  color: white;
  cursor: pointer;
}

#addBtn:hover {
  background: #218838;
}

#taskList {
  list-style: none;
  padding: 0;
  margin-top: 20px;
}

.task-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #f8f9fa;
  margin-bottom: 10px;
  padding: 10px;
  border-radius: 8px;
}

.task-item.completed span {
  text-decoration: line-through;
  color: gray;
}

.btn {
  border: none;
  padding: 5px 10px;
  border-radius: 6px;
  cursor: pointer;
  margin-left: 5px;
}

.complete-btn {
  background: #007bff;
  color: white;
}

.delete-btn {
  background: #dc3545;
  color: white;
}

.edit-btn {
  background: #ffc107;
  color: black;
}

footer {
  text-align: center;
  margin-top: 30px;
  padding: 10px;
  background: #333;
  color: white;
  font-size: 14px;
}

```
## script.js:
```
const taskInput = document.getElementById("taskInput");
const addBtn = document.getElementById("addBtn");
const taskList = document.getElementById("taskList");

document.addEventListener("DOMContentLoaded", loadTasks);
addBtn.addEventListener("click", addTask);

function addTask() {
  const taskText = taskInput.value.trim();
  if (taskText === "") {
    alert("Please enter a task!");
    return;
  }
  const taskItem = createTaskElement(taskText);
  taskList.appendChild(taskItem);
  saveTaskToLocal(taskText);
  taskInput.value = "";
}

function createTaskElement(taskText) {
  const li = document.createElement("li");
  li.className = "task-item";

  const span = document.createElement("span");
  span.textContent = taskText;

  const completeBtn = document.createElement("button");
  completeBtn.textContent = "Complete";
  completeBtn.className = "btn complete-btn";
  completeBtn.onclick = () => {
    li.classList.toggle("completed");
    updateLocalStorage();
  };

  const editBtn = document.createElement("button");
  editBtn.textContent = "Edit";
  editBtn.className = "btn edit-btn";
  editBtn.onclick = () => {
    const newTask = prompt("Edit your task:", span.textContent);
    if (newTask) {
      span.textContent = newTask;
      updateLocalStorage();
    }
  };

  const deleteBtn = document.createElement("button");
  deleteBtn.textContent = "Delete";
  deleteBtn.className = "btn delete-btn";
  deleteBtn.onclick = () => {
    li.remove();
    updateLocalStorage();
  };

  li.appendChild(span);
  li.appendChild(completeBtn);
  li.appendChild(editBtn);
  li.appendChild(deleteBtn);

  return li;
}

function saveTaskToLocal(task) {
  let tasks = JSON.parse(localStorage.getItem("tasks")) || [];
  tasks.push({ text: task, completed: false });
  localStorage.setItem("tasks", JSON.stringify(tasks));
}

function loadTasks() {
  let tasks = JSON.parse(localStorage.getItem("tasks")) || [];
  tasks.forEach(t => {
    const li = createTaskElement(t.text);
    if (t.completed) li.classList.add("completed");
    taskList.appendChild(li);
  });
}

function updateLocalStorage() {
  const tasks = [];
  document.querySelectorAll(".task-item").forEach(li => {
    tasks.push({
      text: li.querySelector("span").textContent,
      completed: li.classList.contains("completed")
    });
  });
  localStorage.setItem("tasks", JSON.stringify(tasks));
}

```
## OUTPUT

<img width="1915" height="1133" alt="image" src="https://github.com/user-attachments/assets/4744b5c1-0bab-48e3-bb28-c8247253b9c5" />

## RESULT
The program for creating To-do list using JavaScript is executed successfully.
