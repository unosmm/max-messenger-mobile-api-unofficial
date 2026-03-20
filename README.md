# Unofficial Max Messenger Private Mobile API SDK

**Неофициальная библиотека / SDK для Max Messenger**  
на основе reverse-engineered мобильного private API

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python](https://img.shields.io/badge/python-3.9%2B-blue)](https://www.python.org/)
[![Node.js](https://img.shields.io/badge/node.js-18%2B-green)](https://nodejs.org/)

**Важное предупреждение**  
Это **неофициальная** библиотека, созданная путём reverse engineering протокола мобильного приложения Max Messenger.  
Она **не связана** с VK Group, разработчиками Max Messenger и не является официальным продуктом.  
Используйте на свой страх и риск. Возможны блокировки аккаунта, изменения протокола и другие риски.

## Возможности

- Авторизация по номеру телефона + код из приложения
- Отправка и получение текстовых сообщений
- Поддержка медиафайлов (фото, видео, документы, голосовые)
- Чтение и отправка статусов / сторис
- Работа с чатами, группами, каналами
- Multi-device режим (подключение нескольких устройств)
- Получение и отправка реакций, упоминаний, цитирований
- Работа с контактами и синхронизация
- Обработка входящих звонков (сигнализация)
- Высокая стабильность за счёт эмуляции мобильного клиента

## Для кого эта библиотека

- Разработчики чат-CRM и омниканальных платформ
- Создатели автоматизаций и рассылок
- Авторы ботов и userbot-систем
- Компании, которым нужен полный доступ к функционалу Max без ограничений официального Bot API

## Установка

```bash
# Python (рекомендуемый способ)
pip install max-private-api

# или из исходников
git clone https://github.com/ВАШ_НИК/max-private-api.git
cd max-private-api
pip install -e .

## Быстрый старт (Python)

```python
from max_private_api import MaxClient

client = MaxClient()

# Авторизация (первый запуск — код придёт в приложение Max)
await client.login(phone="+79991234567")

# Отправить сообщение
await client.send_message(
    chat_id="123456789",
    text="Привет! Это сообщение отправлено через неофициальный private API 😎"
)

# Получать события в реальном времени
@client.on("message")
async def on_message(event):
    print(f"Новое сообщение от {event.sender}: {event.text}")

await client.run_polling()
```

## Документация

Полная документация и примеры → [docs/README.md](docs/README.md)

Основные модули:
- `auth` — авторизация и сессии
- `messages` — работа с сообщениями
- `media` — загрузка/скачивание файлов
- `chats` — управление чатами и группами
- `events` — обработка реального времени (WebSocket-подобный протокол)

## Статус проекта (март 2026)

✅ Работает на текущей версии приложения Max (Android/iOS)  
⚠️ Протокол может меняться — следите за обновлениями  
🔄 Планируется поддержка: голосовые/видео сообщения, звонки, каналы

## Contribute

Приветствуются pull request'ы:
- фиксы после апдейтов протокола
- новые возможности
- улучшение стабильности
- документация на английском/русском

## Лицензия

MIT License — используйте свободно, но без гарантий.

---

<small>
Ключевые слова для поиска:  
max messenger, max messenger api, max api, max sdk, max bot, max userbot, max private api, max unofficial, max reverse, max reversed api, max mobile api, макс мессенджер, макс апи, неофициальный макс, макс юзербот, reverse max, max ru api, vk max api, макс мессенджер апи, неофициальный апи макс, макс мессенджер реверс, приватный апи макс, юзербот макс, макс мессенджер sdk, библиотека макс мессенджер, макс апи без ботов, реверс инженеринг макс, макс мессенджер мобильный апи, неофициальный клиент макс, макс мессенджер интеграция crm, макс юзербот python, отправка сообщений макс неофициально, reverse-engineering, reverse-engineered, unofficial-api, private-api, userbot, mobile-reverse, protocol-reverse, messaging-api, chat-api, messenger-sdk, max-messenger, vk-max, ru-messenger, multi-device
</small>
```
