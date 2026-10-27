# Точка Кода

Требования: Node.js 20+, PostgreSQL 14+.

## Запуск
1. `npm install`
2. `cp .env.example .env` и заполните переменные (`SESSION_SECRET`: `openssl rand -hex 32`).
3. PostgreSQL: `createdb tochka_koda`, затем укажите `DATABASE_URL`.
4. `npx prisma migrate dev --name init` (создаст миграции) — для production: `npm run db:deploy`.
5. Администратор: `npm run admin:create -- you@example.com "пароль-от-12-символов"`; вход: `/admin/login`.
6. `npm run dev` или `npm run build && npm start`.

## Telegram-уведомления
Создайте бота у @BotFather → `TELEGRAM_BOT_TOKEN`. Напишите боту, затем узнайте свой chat id (например, через getUpdates) → `TELEGRAM_ADMIN_CHAT_ID`. Токен используется только на сервере.

## Настройка
Контакты и реквизиты — `lib/config.ts` (сейчас заглушки). Тексты услуг — `lib/services.ts`.
Лимитер (`lib/ratelimit.ts`) хранится в памяти процесса: при нескольких инстансах замените на Redis.
