# aiomail — Asynchronous Email Sending Library

A simple and lightweight library for asynchronous email sending via SMTP.

## Installation

Ensure you have the dependencies installed:
```bash
pip install aiosmtplib
```

## Quick Start

### Initialize the sender
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

### Send an email
```python
import asyncio

async def main():
    await email_sender.send_email(
        subject="Test Email",
        body="Hello, this is a test message!",
        recipients=["recipient@example.com"]
    )

asyncio.run(main())
```

## `EmailSender` Parameters
- `email_address`: Your email address
- `email_password`: Application password or token
- `smtp_server`: SMTP server address (e.g., `smtp.gmail.com`)
- `smtp_port`: SMTP port (default 587)
- `log_file_path`: Path to log file (optional)

## Logging
- Logs are saved to the specified file and printed to the console.
- Log levels: `INFO` for successful sends, `ERROR` for failures.

## Features
- Automatic STARTTLS for secure connections
- Multiple recipients support
- Asynchronous operations via `aiosmtplib`

## Security
⚠️ Never store credentials in code! Use environment variables:
```python
import os

email_sender = EmailSender(
    email_address=os.getenv("EMAIL"),
    email_password=os.getenv("EMAIL_PASSWORD"),
    ...
)
```