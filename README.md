# VK API

## About
Этот пакет выполняет абстракцию работы с API ВКонтакте на языке PHP.
Он позволяет строить запросы прямо из кода, а также включает в себя 
обработку полученных ответов, позволяя, например, управлять количеством 
попыток отправки запроса при использовании того или иного метода.

## Usage
Установка:
```
composer require mggflow/vk-api
```
Пример получения данных о текущем пользователе:
```
$token = "...access_token....";
$apiVersion = 5.131;
// Создаём объект АПИ для определённого токена и версии.
$api = new API($token, $apiVersion);
// Отправляем запрос к АПИ ВК, указывая, что даём 3 попытки для успешного получения ответа с возможностью ожидания.
$users = $api->users->get()->explore(true,3,true);
// Если запрос будет неудачным, вернёт false, иначе блок response.
var_dump($users);
```