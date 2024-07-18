<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do List</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1>To-Do List</h1>
    <input type="text" id="taskInput" placeholder="Add new Task"/>
    <button onclick="addTask()">Add Task</button>
    <ul id="taskList"></ul>

    <script>
        let tasks = []

        function addTask(){
            const taskInput = document.getElementById('taskInput');
            const taskText = taskInput.value.trim();

            if(taskText !== ''){
                tasks.push(taskText);
                displayTasks();
                taskInput.value = ''
            }
        }

        function displayTasks(){
            const taskList = document.getElementById('taskList')
            taskList.innerHTML=''
            tasks.forEach((task,index)=> {
                const li = document.createElement('li');
                li.textContent = task;

                const deleteButton = document.createElement('button')
                deleteButton.textContent = 'Delete'
                deleteButton.onclick = function(){
                    tasks.splice(index,1)
                    displayTasks()
                }

                const updateButton = document.createElement('button')
                updateButton.textContent = 'Update'
                updateButton.onclick=  function(){
                    const updatedTask = prompt('enter updated task:',task)
                    if(updatedTask !== null){
                        tasks[index] = updatedTask.trim()
                        displayTasks()
                    }
                }

                li.appendChild(deleteButton)
                li.appendChild(updateButton)

                taskList.appendChild(li)
            })
        }

        
    </script>
</body>
</html>
