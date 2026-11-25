# LocalDockerServer for macOS

**LocalDockerServer** — готовое нативное приложение для macOS (аналог OpenServer на базе Docker) для локальной веб-разработки на PHP, MariaDB, Redis и Nginx.

[![Latest Release](https://img.shields.io/github/v/release/nobless2/LocalDockerServer?label=Download&style=for-the-badge)](https://github.com/nobless2/LocalDockerServer/releases/latest)
![macOS 12+](https://img.shields.io/badge/macOS-12.0%2B-000000?style=for-the-badge&logo=apple)
![Apple Silicon](https://img.shields.io/badge/Apple%20Silicon-arm64-2563eb?style=for-the-badge)

---

## Возможности

- **Готовое macOS-приложение (`LocalDockerServer.app`)** — нативный интерфейс со строкой меню (треем), встроенной веб-панелью управления и консолью логов.
- **Несколько версий PHP по требованию** — при первом запуске быстро разворачивается **PHP 8.4**, а **PHP 7.4, 8.1, 8.2 и 8.3** устанавливаются в один клик прямо из панели. В каждой версии уже есть `pdo_mysql`, `mysqli`, `pdo_pgsql`, `gd`, `intl`, `zip`, `bcmath`, `exif`, `sockets`, `pcntl`, `redis`, `xdebug` и `composer`.
- **Автоматические локальные домены (`*.loc`) и HTTPS** — создайте папку в `projects/` (например, `projects/mysite.loc`), и сайт сразу станет доступен по `http://mysite.loc` и `https://mysite.loc`. Wildcard DNS и доверенный локальный Root CA настраиваются автоматически.
- **Полный стек из коробки**:
  - **Nginx** — автоматическая генерация виртуальных хостов и настройка Document Root (`/`, `/public`, `/web` и др.);
  - **MariaDB 10.11** + управление базами данных и **phpMyAdmin** (`http://pma.loc`);
  - **Redis 7** — кэш и очереди;
  - **Mailpit** (`http://mail.loc`) — локальный перехват исходящей почты (`mail()` уже настроен);
  - **PHP / Composer CLI** — выполнение команд внутри нужного PHP-контейнера прямо из панели.
- **Настройки приложения**:
  - переключение языка интерфейса (**Русский / English**);
  - выбор и смена рабочей папки;
  - редактирование портов и параметров `.env` прямо из интерфейса;
  - управление Wildcard DNS, доверием HTTPS (Root CA) и `/etc/hosts`.
- **Автоматические обновления** — приложение проверяет новые релизы раз в день и позволяет проверить и установить обновление вручную из меню или окна настроек.

---

## Требования

- **macOS 12.0+** (Apple Silicon `arm64`)
- Установленный **Docker Desktop**, **OrbStack** или **Rancher Desktop**

---

## Установка и запуск

1. Перейдите на страницу **[Releases](https://github.com/nobless2/LocalDockerServer/releases/latest)** и скачайте **`LocalDockerServer.dmg`**.
2. Откройте `LocalDockerServer.dmg` и перетащите **`LocalDockerServer.app`** в папку **`Applications`** (`Программы`).
3. Запустите **LocalDockerServer**:
   > Если macOS предупредит о неподписанном разработчике после скачивания из интернета — нажмите по приложению **правой кнопкой мыши → «Открыть»**, либо выполните в терминале:
   > ```bash
   > xattr -cr /Applications/LocalDockerServer.app
   > ```
4. Нажмите **«▶ Запустить LocalDockerServer»** — приложение само развернёт Docker-стек в рабочую папку (по умолчанию `~/LocalDockerServer`, можно изменить в **Настройках**), настроит домены `*.loc` и HTTPS и откроет панель управления.

---

## Быстрый доступ после запуска

| Сервис | Локальный домен | Прямой адрес |
|---|---|---|
| **Панель управления** | `http://panel.loc` | `http://localhost:8080` |
| **phpMyAdmin** | `http://pma.loc` | `http://localhost:8081` |
| **Mailpit (почта)** | `http://mail.loc` | `http://localhost:8025` |
| **Демо-сайт** | `http://example.loc` | — |

### Подключение к БД и Redis из PHP

| Сервис | Хост из PHP (Docker) | Хост с Mac | Доступ |
|---|---|---|---|
| **MariaDB** | `db:3306` | `127.0.0.1:3306` | `dev` / `dev` или `root` / `root` |
| **Redis** | `redis:6379` | `127.0.0.1:6379` | без пароля |
| **Mailpit (SMTP)** | `mailpit:1025` | — | `mail()` работает из коробки |

---

## Обновление приложения

LocalDockerServer автоматически проверяет наличие новых версий в этом репозитории **1 раз в день**. Также можно проверить обновления вручную через **LocalDockerServer → Проверить обновления…**, меню в строке состояния или раздел **Настройки**.

---

## English Overview

**LocalDockerServer** is a standalone native macOS Docker-based local web development environment (OpenServer alternative) featuring on-demand PHP versions (`7.4`, `8.1`, `8.2`, `8.3`, `8.4`), automatic `*.loc` wildcard domains & local HTTPS, Nginx, MariaDB, phpMyAdmin, Redis, Mailpit, full Russian/English UI, built-in Settings, and automatic daily updates.

1. Download **`LocalDockerServer.dmg`** from the **[Latest Release](https://github.com/nobless2/LocalDockerServer/releases/latest)**.
2. Drag **`LocalDockerServer.app`** into `/Applications`.
3. Make sure **Docker Desktop** or **OrbStack** is running, then launch **LocalDockerServer** and click **Start**.
