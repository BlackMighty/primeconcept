# PrimeConcept

PrimeConcept - это приложение для управления пользователями и их статусами. Оно позволяет обновлять статус пользователя и перераспределять открытые запросы, когда пользователь становится оффлайн.

## Содержание

- [Установка](#установка)
- [Использование](#использование)
- [Структура проекта](#структура-проекта)
- [API](#api)
- [Обработка исключений](#обработка-исключений)
- [Авторы](#авторы)
- [Лицензия](#лицензия)

## Установка

1. Клонируйте репозиторий:

    ```sh
    git clone https://github.com/BlackMighty/primeconcept
    ```

2. Перейдите в директорию проекта:

    ```sh
    cd primeconcept
    ```

3. Установите зависимости и соберите проект с помощью Maven:

    ```sh
    mvn clean install
    ```

## Использование

1. Запустите приложение:

    ```sh
    mvn spring-boot:run
    ```

2. Приложение будет доступно по адресу `http://localhost:8080`.

## Структура проекта

```plaintext
src/main/java/com/example/primeconcept
|-- controllers
|   |-- UserController.java
|-- enums
|   |-- Status.java
|-- exceptions
|   |-- GlobalExceptionHandler.java
|   |-- ResourceNotFoundException.java
|-- model
|   |-- User.java
|-- repository
|   |-- UserRepository.java
|-- service
|   |-- RequestService.java
|   |-- UserService.java
|   |-- impl
|       |-- RequestServiceImpl.java
|       |-- UserServiceImpl.java
```
## API
```plaintext
Обновление статуса пользователя
URL: /users/{userId}/status
Метод: PUT
Параметры пути:
userId (Long): ID пользователя
Параметры запроса:
status (Status): Новый статус пользователя (например, ONLINE, OFFLINE)
Пример запроса:
curl -X PUT "http://localhost:8080/users/123/status?status=ONLINE"
```
## Обработка исключений
```plaintext
GlobalExceptionHandler
Глобальный обработчик исключений обрабатывает исключения, возникающие в приложении, и возвращает соответствующие HTTP статусы и сообщения об ошибках.
ResourceNotFoundException: Возвращает статус 404 и сообщение об ошибке, когда ресурс не найден.
@ExceptionHandler(ResourceNotFoundException.class)
@ResponseStatus(HttpStatus.NOT_FOUND)
public String handleResourceNotFoundException(ResourceNotFoundException ex) {
    return ex.getMessage();
}
IllegalArgumentException: Возвращает статус 400 и сообщение об ошибке, когда переданы некорректные параметры.
@ExceptionHandler(IllegalArgumentException.class)
@ResponseStatus(HttpStatus.BAD_REQUEST)
public String handleIllegalArgumentException(IllegalArgumentException ex) {
    return ex.getMessage();
}
```

## Автор
```aidl
Андрей Золотарев
```

