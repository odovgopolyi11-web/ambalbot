# 🚀 ІНСТРУКЦІЯ: Розгортання Telegram-бота на Render.com

## ✅ ЩО ГОТОВО:
- ✅ Код бота з усіма командами
- ✅ Підключення до Firebase
- ✅ Автоматичні сповіщення

---

## 📋 КРОК 1: Підготовка Firebase Service Account

1. Відкрий: https://console.firebase.google.com/project/dolg-74757/settings/serviceaccounts/adminsdk

2. Натисни **"Створити новий приватний ключ"** (Generate new private key)

3. Завантажиться файл JSON (наприклад, `dolg-74757-firebase-adminsdk-xxxxx.json`)

4. **ЗБЕРЕЖИ ЦЕЙ ФАЙЛ!** Він нам потрібен.

---

## 📋 КРОК 2: Створення GitHub репозиторію

### Варіант А: Через GitHub веб-інтерфейс

1. Зайди на https://github.com
2. Натисни **"New repository"**
3. Назва: `finance-telegram-bot`
4. Зроби **Public**
5. Натисни **"Create repository"**

6. **Завантаж файли:**
   - Натисни **"uploading an existing file"**
   - Перетягни файли: `bot.js` та `package.json`
   - Натисни **"Commit changes"**

### Варіант Б: Через командний рядок (якщо вмієш)

```bash
git init
git add bot.js package.json
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/твій-нік/finance-telegram-bot.git
git push -u origin main
```

---

## 📋 КРОК 3: Реєстрація на Render.com

1. Відкрий: https://render.com
2. Натисни **"Get Started"** або **"Sign Up"**
3. **Увійди через GitHub** (це найпростіше)
4. Дай дозвіл Render доступ до твого GitHub

---

## 📋 КРОК 4: Створення Web Service на Render

1. На дашборді Render натисни **"New +"** → **"Web Service"**

2. Підключи свій GitHub репозиторій `finance-telegram-bot`

3. **Налаштування:**
   - **Name:** `finance-bot` (або будь-яке інше)
   - **Region:** `Frankfurt (EU Central)` (найближче до України)
   - **Branch:** `main`
   - **Runtime:** `Node`
   - **Build Command:** `npm install`
   - **Start Command:** `npm start`
   - **Instance Type:** `Free` ⭐

4. **Environment Variables** (змінні середовища):
   
   Натисни **"Add Environment Variable"** і додай:
   
   ```
   GOOGLE_APPLICATION_CREDENTIALS=/etc/secrets/firebase-key.json
   ```

5. **Secret Files** (секретні файли):
   
   Прокрути вниз до розділу **"Secret Files"**
   
   Натисни **"Add Secret File"**
   
   - **Filename:** `/etc/secrets/firebase-key.json`
   - **Contents:** Відкрий файл JSON з кроку 1 та скопіюй ВЕСЬ вміст сюди
   
6. Натисни **"Create Web Service"**

---

## 📋 КРОК 5: Очікування деплою

1. Render почне встановлювати залежності та запускати бота
2. Це займе **2-5 хвилин**
3. Дивися логи у вкладці **"Logs"**
4. Коли побачиш:
   ```
   🤖 Telegram bot started!
   ✅ Bot is ready and listening for commands!
   ```
   **ВСЕ ГОТОВО!** 🎉

---

## 📋 КРОК 6: Перевірка роботи

1. Відкрий Telegram
2. Знайди свого бота (той що створював у BotFather)
3. Напиши `/start`
4. Повинно прийти привітальне повідомлення!

5. **Протестуй команди:**
   - `/balance` - баланс
   - `/debts` - список боргів
   - `/add Тест 100` - додати борг
   - `/help` - всі команди

---

## 🎯 ГОТОВО! Бот працює 24/7!

### 📱 Що тепер можна робити:

**З боту:**
- Дивитись баланс та борги
- Додавати нові борги
- Оплачувати борги
- Видаляти борги
- Отримувати звіти

**З веб-додатку:**
- Те саме + візуальний інтерфейс
- Всі зміни синхронізуються автоматично!

**Сповіщення:**
- Будь-яка зміна в боті → сповіщення всім підписаним
- Будь-яка зміна у веб-додатку → сповіщення всім підписаним

---

## ⚠️ ВАЖЛИВО:

1. **Безкоштовний план Render:**
   - Сервіс "засинає" після 15 хвилин неактивності
   - При новому повідомленні "прокидається" за 30-60 секунд
   - Це нормально для безкоштовного плану!

2. **Якщо щось не працює:**
   - Подивись логи в Render (вкладка Logs)
   - Переконайся, що Firebase ключ правильно вставлений
   - Напиши мені - допоможу!

---

## 🎉 ВСІ КОМАНДИ БОТА:

### 📊 Інформація:
- `/start` - Підписатись на сповіщення
- `/balance` - Поточний баланс
- `/debts` - Список всіх боргів
- `/total` - Загальна сума
- `/progress` - Прогрес у відсотках

### 🔧 Управління:
- `/add Назва Сума` - Додати борг
- `/pay Назва Сума` - Оплатити частину
- `/delete Назва` - Видалити борг

### 📈 Аналітика:
- `/report` - Повний звіт
- `/stats` - Статистика

### ⚙️ Налаштування:
- `/stop` - Відписатись
- `/help` - Довідка

---

## 🔗 КОРИСНІ ПОСИЛАННЯ:

- Render Dashboard: https://dashboard.render.com
- Firebase Console: https://console.firebase.google.com/project/dolg-74757
- BotFather (управління ботом): https://t.me/BotFather

---

## 💡 ПІДКАЗКИ:

1. **Декілька користувачів:**
   - Кожен пише боту `/start`
   - Всі отримують сповіщення

2. **Зміна команд бота:**
   - Редагуй файл `bot.js` в GitHub
   - Render автоматично перезапустить бот

3. **Перегляд логів:**
   - Render Dashboard → твій сервіс → вкладка "Logs"

---

Успіхів! 🚀