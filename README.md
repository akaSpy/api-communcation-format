# Формат общения backend с frontend

## Request

```json
{
  "data": {
    "login": "login",
    "password": "123456"
  }
}
```

## Response

### Ok

Статусы 200.

Пустой успешный ответ:

```json
{
  "status": "ok",
  "data": null
}
```

Успешный ответ с данными:

```json
{
  "status": "ok",
  "data": {
    "exists": false
  }
}
```

### Fail

Статусы 400.

#### Ошибки логики

На стороне frontend можно использовать code для обработки ошибки. 

```json
{
  "status": "fail",
  "errors": [
    {
      "type": "logic",
      "code": "registration-is-not-confirmed",
      "message": "Вы не подтвердили регистрацию."
    }
  ]
}
```

#### Ошибки валидации

Если ошибка типа "type": "field", то добавляется ключ "field": "password", означающий, что ошибка относится к конкретному полю на форме.

```json
{
  "status": "fail",
  "errors": [
    {
      "type": "field",
      "code": "validation",
      "field": "password",
      "message": "Введите пароль.",
      "data": null
    }
  ]
}
```

### Error

Статусы 500.

```json
{
  "status": "error",
  "message": "Произошла ошибка, попробуйте позже."
}
```
