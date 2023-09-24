# API-GitHub-Issues
## Информация об использовании (запуску) коллекции для работы с API GitHub Issues: 
### 1. Сгенерировать API ключ для GitHub: 
Для начала работы с коллекцией в Postman, необходимо сгенерировать API-ключ для GitHub (токен доступа). Это способ аутентификации, который позволяет пользователям взаимодействовать с GitHub через программы, используя API GitHub; 
### 2. Создать коллекцию в Postman:
Под названием "Issue" 
### 3. Запрос на создание задачи: 
✅ POST на адрес: https://api.github.com/repos/VeraGrechina/API-GitHub-Issues/issues; <br>
✅ Во вкладке Authorization выбрать Type: Bearer и вставить ранее сгенерированный токен;
✅ Тело запроса: <br>
```json
{
    "title": "Issue 1",
    "body": "Something went wrong",
    "labels": ["bug"],
"assignees": ["VeraGrechina"]
}
```
<br>
Полученный в ответе номер задачи записываем в переменные коллекции с помощью скрипта JS (вкладка Tests, скрипт выполнится после запроса):<br>
var key = "isseu_number"
var value = pm.response.json().number
pm.collectionVariables.set(key, value) 
