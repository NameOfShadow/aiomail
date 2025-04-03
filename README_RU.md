# aiomail — Асинхронная библиотека для отправки электронных писем

Простая и удобная библиотека для асинхронной отправки email через SMTP-сервер.

## Установка

Убедитесь, что у вас установлены зависимости:
```bash
pip install aiosmtplib
```

## Использование

### Инициализация отправителя
```python
from aiomail import EmailSender

email_sender = EmailSender(
    email_address="your_email@example.com",
    email_password="your_password",
    smtp_server="smtp.example.com",
    smtp_port=587,
    log_file_path="logs/email.log"
)
```

### Отправка письма
```python
import asyncio

async def main():
    await email_sender.send_email(
        subject="Тестовое письмо",
        body="Привет, это тестовое сообщение!",
        recipients=["recipient@example.com"]
    )

asyncio.run(main())
```

## Параметры класса `EmailSender`
- `email_address`: Ваш email-адрес
- `email_password`: Пароль или токен приложения
- `smtp_server`: Адрес SMTP-сервера (например, `smtp.gmail.com`)
- `smtp_port`: Порт SMTP (по умолчанию 587)
- `log_file_path`: Путь к файлу логов (необязательно)

## Логирование
- Логи сохраняются в указанный файл и выводятся в консоль.
- Уровень логирования: `INFO` для успешных отправок, `ERROR` для ошибок.

## Особенности
- Автоматическое использование STARTTLS для безопасного соединения
- Поддержка нескольких получателей
- Асинхронная работа через `aiosmtplib`

## Безопасность
⚠️ Никогда не храните пароли в коде! Используйте переменные окружения:
```python
import os

email_sender = EmailSender(
    email_address=os.getenv("EMAIL"),
    email_password=os.getenv("EMAIL_PASSWORD"),
    ...
)
```