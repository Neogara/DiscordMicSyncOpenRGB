# 🎤✨ DiscordMicSyncOpenRGB

## 📌 Описание

**DiscordMicSyncOpenRGB** — это приложение, которое синхронизирует состояние микрофона в Discord с подсветкой устройств, управляемых через OpenRGB.  
Когда микрофон активен, подсветка изменяется, предоставляя визуальный индикатор активности.

## 🔧 Требования

Перед установкой убедитесь, что у вас установлены:

- **[Node.js](https://nodejs.org/en/download)** версии **22.9.0** или выше
- **[OpenRGB](https://openrgb.org/releases.html)** установленный и запущенный с **включенным SDK** скачать 
- **[Discord](https://discord.com/)** Клиент

## 🚀 Установка

### 1️⃣ Клонируйте репозиторий

```bash
git clone https://github.com/ваш_пользователь/DiscordMicSyncOpenRGB.git
cd DiscordMicSyncOpenRGB
```

### 2️⃣ Установите зависимости

```bash
npm install
```

## ⚙️ Настройка

### 1️⃣ Измените переменные окружения в `secrets.env`:

```env
CLIENT_ID=<YOUR_CLIENT_ID>
CLIENT_SECRET=<YOUR_CLIENT_SECRET>
```

Получить их можно, создав новое приложение в [Discord Developer Portal](https://discord.com/developers/docs/intro).

### 2️⃣ Проверьте конфигурацию в `DiscordMicSyncOpenRGB.js`

```js
const CONFIG = {
  REDIRECT_URI: 'http://localhost:3000', // Адрес редиректа для авторизации  
  
  OPENRGB_HOST: 'localhost', // IP-адрес OpenRGB SDK Server  
  OPENRGB_PORT: 6742,        // Порт OpenRGB SDK Server  
  
  KEYBOARD_DEVICE_ID: 0,  // ID устройства (как настроено в OpenRGB)  
  MIC_CONTROL_LED_INDEX: 15,  // Индекс LED (кнопки) для управления микрофоном  
  SOUND_CONTROL_LED_INDEX: 14, // Индекс LED (кнопки) для управления звуком  
};
```

- `OPENRGB_HOST` и `OPENRGB_PORT` должны соответствовать настройкам вашего OpenRGB сервера.
- `KEYBOARD_DEVICE_ID` можно узнать при первом запуске (в консоли будут выведены все доступные устройства).
- `REDIRECT_URI:` — URL, на котором будет временно поднят сервер для авторизации OAuth2.

## ▶️ Запуск

После настройки просто запустите приложение командой:
```bash
npm run start
```

## ❗ Частые ошибки ❗
#### Ошибка `Access Denied` при запросе к Discord API
	Причина: Неправильные `CLIENT_ID` или `CLIENT_SECRET`
	Решение: Проверьте их в secrets.env и попробуйте снова.

#### Ошибка подключения к `OpenRGB SDK`
	Причина: OpenRGB запущен без SDK или не запущен вообще.
	Решение: Убедитесь, что OpenRGB SKD server запущен
