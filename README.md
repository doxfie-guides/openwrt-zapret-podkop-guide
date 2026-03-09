# Zapret Manager + Podkop на OpenWrt

Гайд по настройке **Zapret** и **Podkop** на роутере с OpenWrt для обхода DPI и гибкой маршрутизации трафика через VPN.

---

## 🔧 Предварительные условия

- Роутер на **OpenWrt**
- Доступ по **SSH** к роутеру
- Интернет работает **на самом роутере**

---

## 🧨 Установка Zapret через Zapret-Manager

**Zapret-Manager** — это умный скрипт, который сам поставит и настроит Zapret через удобное текстовое меню.

> [!WARNING]
> Если одна из стратегий **Zapret** не работает на **ПК с Windows**, выполните эту команду в **PowerShell**:
>
> ```powershell
> netsh int tcp set global timestamps=enabled
>```

### Запустить установщик Zapret-Manager

```sh
sh <(wget -O - https://raw.githubusercontent.com/StressOzz/Zapret-Manager/main/Zapret-Manager.sh)
```

После запуска появится меню. Дальнейшие шаги:

- выбрать нужный пункт, введя **цифру**
- нажать **Enter**
- следовать подсказкам скрипта

Полное описание и код проекта:  
https://github.com/StressOzz/Zapret-Manager

---

## 🌉 Установка / обновление Podkop

**Podkop** — утилита для маршрутизации трафика по доменам и подсетям через разные выходы  
(например, часть трафика — через VPN, часть — напрямую).

### 1. Установка или обновление Podkop

Выполнить на роутере:

```sh
sh <(wget -O - https://raw.githubusercontent.com/itdoginfo/podkop/refs/heads/main/install.sh)
```

- Если Podkop **ещё не установлен** — он будет установлен.
- Если Podkop **уже стоит** — скрипт обновит его до актуальной версии.

Официальный сайт проекта:  
https://podkop.net/  

GitHub проекта:  
https://github.com/itdoginfo/podkop

---

## 🌐 Наборы доменов для Podkop

Авторы Podkop ведут готовый набор списков доменов под разные сервисы. Их можно сразу подключать в конфиге Podkop, чтобы не собирать домены вручную.

Полный список наборов:  
https://github.com/itdoginfo/allow-domains

Например, там есть:

- YouTube
- Meta
- Cloudflare
- и другие сервисы

---

## 🧪 Проверка DPI-блокировок

Чтобы проверить, режет ли провайдер трафик (DPI), можно использовать онлайн-тест.

### Как проверить

1. Открыть в браузере:

   ```text
   https://hyperion-cs.github.io/dpi-checkers/ru/tcp-16-20/
   ```

2. На открывшейся странице нажать кнопку **Start**.
3. Дождаться окончания тестов и посмотреть результаты по разным режимам.

Это удобно запускать:

- **до** настройки Zapret / Podkop  
- и **после** — чтобы сравнить, стало ли лучше.

---

## 📎 Краткие команды

```sh
# Обновить пакеты OpenWrt
opkg update

# Установка / запуск Zapret-Manager
sh <(wget -O - https://raw.githubusercontent.com/StressOzz/Zapret-Manager/main/Zapret-Manager.sh)

# Установка / обновление Podkop
sh <(wget -O - https://raw.githubusercontent.com/itdoginfo/podkop/refs/heads/main/install.sh)
```
