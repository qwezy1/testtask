Пользование:
В консоль "node server.js"
http://localhost:5000/tasks/ ссылка для использвания

Управление идет через консоль  браузера "F12"
На всех кроме POST нужен id, он выдается сам в Mongo, все данные которые были добавлены можно увидеть в Mongo, сейчас менять может пользователь с любого IP

Чтобы создать (POST) используется:
fetch('http://localhost:5000/tasks', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    title: 'Новая задача', //ваша информация
    description: 'Описание задачи', //ваша информация
    status: 'todo', // или 'done'
  }),
})
  .then(response => response.json())
  .then(data => console.log('New task created:', data))
  .catch(error => console.error('Error:', error)); //вывод

Чтобы получить все данные(GET)
fetch('http://localhost:5000/tasks')
  .then(response => response.json())
  .then(data => console.log('Tasks:', data))
  .catch(error => console.error('Error:', error));

Чтобы получитьб все данные по ID(GET)
fetch('http://localhost:5000/tasks/67cd33dc68db24e16abeceec')  //id меняется на любой существующий
  .then(response => response.json())
  .then(data => console.log('Task:', data))
  .catch(error => console.error('Error:', error));

Чтобы обновить (PUT)
fetch('http://localhost:5000/tasks/67cd33dc68db24e16abeceec', {
  method: 'PUT',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    title: 'Обновленная задача', //ваша информация
    description: 'Описание обновленной задачи', //ваша информация
    status: 'done',
  }),
})
  .then(response => response.json())
  .then(data => console.log('Task updated:', data))
  .catch(error => console.error('Error:', error));

Чтобы удалить задачу (DELETE)
fetch('http://localhost:5000/tasks/67cd33dc68db24e16abeceec', {
  method: 'DELETE',
})
  .then(response => response.json())
  .then(data => console.log('Task deleted:', data))
  .catch(error => console.error('Error:', error));
