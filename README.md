
# Unofficial Max Messenger Private API SDK (Reverse-Engineered Mobile Client)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python](https://img.shields.io/badge/python-3.9%2B-blue)](https://www.python.org/)
[![Node.js](https://img.shields.io/badge/node.js-18%2B-green)](https://nodejs.org/)

**Reverse-engineered mobile private API** мессенджера **Max** (от VK) на базе официального Android-приложения (пакет `ru.oneme.app`).

Это **не WebSocket/Web-версия** (как в браузерных клиентах), а именно **мобильный API**, эмулирующий поведение официального приложения для Android/iOS.

Это **неофициальная** библиотека, созданная путём reverse engineering протокола мобильного приложения Max Messenger.  
Она **не связана** с VK Group, разработчиками Max Messenger и не является официальным продуктом.  
**Официальная документация Bot API** (рекомендуем для стабильных ботов):  
https://dev.max.ru/ui — там полная поддержка, но это строго для ботов с токеном (ограничения по функционалу, нет multi-device как у пользователя).

Наш SDK даёт **полный user-level доступ** без ограничений Bot API: авторизация по номеру телефона, multi-account, полный набор сообщений/медиа/статусов/звонков.

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

Приветствуются issues / pull request'ы:
- фиксы после апдейтов протокола
- новые возможности
- улучшение стабильности
- документация на английском/русском

## Лицензия

MIT License — используйте свободно, но без гарантий.


## Другие репозитории (официальные Bot API wrappers — без reverse и недокументированных функций)

| Категория          | Репозиторий                                      | Последний коммит (примерно)     |
|--------------------|--------------------------------------------------|---------------------------------|
| Mobile API        | https://github.com/unosmm/max-messenger-mobile-api-unofficial | ~март 2026 (2 коммита всего, низкая активность) |
| WebSocket API     | https://github.com/mochensky/max-user-api       | ~2025–2026 (низкая активность) |
| WebSocket API     | https://github.com/arsrus721/maxclientapi-go    | ~2025 (низкая активность)      |
| WebSocket API     | https://github.com/weristvlad/max-fuck          | Неизвестно / низкая активность |
| WebSocket API     | https://github.com/arsrus721/maxclientapi       | ~2025–2026                     |
| Official Web API  | https://github.com/genixg/MAX.Messenger.API     | Устаревший                     |
| Official Web API  | https://github.com/MaxApiTeam/PyMax             | 11 февраля 2026 (архив)        |
| Official Bot API  | https://github.com/BushlanovDev/max-bot-api-client-php | 13 марта 2026                  |
| Official Bot API  | https://github.com/love-apples/maxapi           | 19 марта 2026                  |
| Official Bot API  | https://github.com/KayumovRu/maxgram            | ~2025–2026                     |
| Official Bot API  | https://github.com/nepobo/max-api               | ~2025–2026                     |


### Кратко по категориям
- **WebSocket API** — браузерные reverse на базе WebSocket (Web-версия Max).
- **Official Web API** — неофициальные клиенты внутренней Web-версии (не Bot API).
- **Official Bot API** — официальные wrappers по https://dev.max.ru/ (самые стабильные).
- **Mobile API** — reverse мобильного приложения (Android/iOS, пакет ru.oneme.app).

Если нужно добавить столбец (например, язык программирования) или уточнить даты — дай знать! 🚀
Если проект использует **официальный токен Bot API** — он стабильнее и не требует реверса.

---

<small>
Ключевые слова для поиска:  
max messenger, max messenger api, max api, max sdk, max bot, max userbot, max private api, max unofficial, max reverse, max reversed api, max mobile api, макс мессенджер, макс апи, неофициальный макс, макс юзербот, reverse max, max ru api, vk max api, макс мессенджер апи, неофициальный апи макс, макс мессенджер реверс, приватный апи макс, юзербот макс, макс мессенджер sdk, библиотека макс мессенджер, макс апи без ботов, реверс инженеринг макс, макс мессенджер мобильный апи, неофициальный клиент макс, макс мессенджер интеграция crm, макс юзербот python, отправка сообщений макс неофициально, reverse-engineering, reverse-engineered, unofficial-api, private-api, userbot, mobile-reverse, protocol-reverse, messaging-api, chat-api, messenger-sdk, max-messenger, vk-max, ru-messenger, multi-device
</small>
```
