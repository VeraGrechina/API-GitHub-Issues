# API-GitHub-Issues
## Информация об использовании (запуску) коллекции для работы с API GitHub Issues: 
### 🌿1. Сгенерировать API ключ для GitHub: 
Для начала работы с коллекцией в Postman, необходимо сгенерировать API-ключ для GitHub (токен доступа). Это способ аутентификации, который позволяет пользователям взаимодействовать с GitHub через программы, используя API GitHub; 
### 🌿2. Создать коллекцию в Postman:
Под названием "Issue" 
### 🌿3. Запрос на создание issue: 
✅ POST на адрес: https://api.github.com/repos/VeraGrechina/API-GitHub-Issues/issues; <br>
✅ Во вкладке Authorization выбрать Type: Bearer и вставить ранее сгенерированный токен;<br>
✅ Тело запроса: <br>
```json
{
    "title": "Issue 1",
    "body": "Something went wrong",
    "labels": ["bug"],
"assignees": ["VeraGrechina"]
}
```
Полученный в ответе номер задачи записываем в переменные коллекции с помощью скрипта JS (вкладка Tests, скрипт выполнится после запроса):<br>
```
var key = "isseu_number"
var value = pm.response.json().number
pm.collectionVariables.set(key, value) 
```
### 🌿4. Запрос на получение списка issues:
✅ GET на адрес: https://api.github.com/repos/VeraGrechina/API-GitHub-Issues/issues; <br>
✅ Во вкладке Authorization выбрать Type: Bearer и вставить ранее сгенерированный токен;<br>
✅ Тело запроса: отсутствует;<br>

### 🌿5. Запрос на изменение названия issue:
✅ PATCH на адрес:https://api.github.com/repos/VeraGrechina/API-GitHub-Issues/issues/{{isseu_number}}, где: <br>
{{isseu_number}}- сохраненная ранее переменная - номер задачи; <br>
✅ Во вкладке Authorization выбрать Type: Bearer и вставить ранее сгенерированный токен;<br>
✅ Тело запроса:<br>
```
{
    "title": "Issue 2"
    
}
```
### 🌿6. Запрос на закрытие issue:
✅ PUT на адрес: https://api.github.com/repos/VeraGrechina/API-GitHub-Issues/{{isseu_number}}/lock, где: <br>
{{isseu_number}}- сохраненная ранее переменная - номер задачи; <br>
✅ Во вкладке Authorization выбрать Type: Bearer и вставить ранее сгенерированный токен;<br>
✅ Тело запроса:<br>
```
{
    "lock_reason": "off-topic"
}
```
