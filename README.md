# LocalDockerServer for macOS

[![Latest Release](https://img.shields.io/github/v/release/nobless2/LocalDockerServer?label=Download&style=for-the-badge)](https://github.com/nobless2/LocalDockerServer/releases/latest)
![macOS 12+](https://img.shields.io/badge/macOS-12.0%2B-000000?style=for-the-badge&logo=apple)
![Apple Silicon](https://img.shields.io/badge/Apple%20Silicon-arm64-2563eb?style=for-the-badge)

[Русский](#русский) · [English](#english)

---

## Русский

**LocalDockerServer** — готовое нативное приложение для macOS (аналог OpenServer на базе Docker) для локальной веб-разработки на PHP, MariaDB, Redis и Nginx.

### Возможности

- **Готовое macOS-приложение (`LocalDockerServer.app`)** — нативный интерфейс со строкой меню (треем), встроенной веб-панелью управления и консолью логов.
- **Несколько версий PHP по требованию** — при первом запуске быстро разворачивается **PHP 8.4**, а **PHP 7.4, 8.1, 8.2 и 8.3** устанавливаются в один клик прямо из панели. В каждой версии уже есть `pdo_mysql`, `mysqli`, `pdo_pgsql`, `gd`, `intl`, `zip`, `bcmath`, `exif`, `sockets`, `pcntl`, `redis`, `xdebug` и `composer`.
- **Автоматические локальные домены (`*.loc`) и HTTPS** — создайте папку в `projects/` (например, `projects/mysite.loc`), и сайт сразу станет доступен по `http://mysite.loc` и `https://mysite.loc`. Wildcard DNS и доверенный локальный Root CA настраиваются автоматически.
- **Полный стек из коробки**:
  - **Nginx** — автоматическая генерация виртуальных хостов и настройка Document Root (`/`, `/public`, `/web` и др.);
  - **MariaDB 10.11** + управление базами данных и **phpMyAdmin** (`http://pma.loc`);
  - **Redis 7** — кэш и очереди;
  - **Mailpit** (`http://mail.loc`) — локальный перехват исходящей почты (`mail()` уже настроен);
  - **PHP / Composer CLI** — выполнение команд внутри нужного PHP-контейнера прямо из панели.

### Требования

- **macOS 12.0+** (Apple Silicon `arm64`)
- Установленный **Docker Desktop**, **OrbStack** или **Rancher Desktop**

### Быстрый доступ после запуска

| Сервис | Локальный домен | Прямой адрес |
|---|---|---|
| **Панель управления** | `http://panel.loc` | `http://localhost:8080` |
| **phpMyAdmin** | `http://pma.loc` | `http://localhost:8081` |
| **Mailpit (почта)** | `http://mail.loc` | `http://localhost:8025` |
| **Демо-сайт** | `http://example.loc` | — |

#### Подключение к БД и Redis из PHP

| Сервис | Хост из PHP (Docker) | Хост с Mac | Доступ |
|---|---|---|---|
| **MariaDB** | `db:3306` | `127.0.0.1:3306` | `dev` / `dev` или `root` / `root` |
| **Redis** | `redis:6379` | `127.0.0.1:6379` | без пароля |
| **Mailpit (SMTP)** | `mailpit:1025` | — | `mail()` работает из коробки |

---

## English

**LocalDockerServer** is a ready-to-use native macOS application (a Docker-based OpenServer alternative) for local web development with PHP, MariaDB, Redis, and Nginx.

### Features

- **Native macOS App (`LocalDockerServer.app`)** — native interface with a menu bar (tray) icon, built-in web control panel, and startup log console.
- **Multiple PHP Versions on Demand** — **PHP 8.4** is set up quickly on first launch, while **PHP 7.4, 8.1, 8.2, and 8.3** can be installed in one click directly from the control panel. Every version includes `pdo_mysql`, `mysqli`, `pdo_pgsql`, `gd`, `intl`, `zip`, `bcmath`, `exif`, `sockets`, `pcntl`, `redis`, `xdebug`, and `composer`.
- **Automatic Local Domains (`*.loc`) & HTTPS** — create a folder inside `projects/` (for example, `projects/mysite.loc`), and your site immediately becomes available at `http://mysite.loc` and `https://mysite.loc`. Wildcard DNS and a trusted local Root CA are configured automatically.
- **Full Stack Out of the Box**:
  - **Nginx** — automatic virtual host generation and Document Root configuration (`/`, `/public`, `/web`, etc.);
  - **MariaDB 10.11** + database management and **phpMyAdmin** (`http://pma.loc`);
  - **Redis 7** — caching and queues;
  - **Mailpit** (`http://mail.loc`) — local outgoing email catcher (`mail()` preconfigured);
  - **PHP / Composer CLI** — run commands inside any PHP container right from the panel.

### Requirements

- **macOS 12.0+** (Apple Silicon `arm64`)
- **Docker Desktop**, **OrbStack**, or **Rancher Desktop**

### Quick Access After Startup

| Service | Local Domain | Direct URL |
|---|---|---|
| **Control Panel** | `http://panel.loc` | `http://localhost:8080` |
| **phpMyAdmin** | `http://pma.loc` | `http://localhost:8081` |
| **Mailpit (Mail)** | `http://mail.loc` | `http://localhost:8025` |
| **Demo Site** | `http://example.loc` | — |

#### Connecting to MariaDB & Redis from PHP

| Service | Host from PHP (Docker) | Host from Mac | Credentials |
|---|---|---|---|
| **MariaDB** | `db:3306` | `127.0.0.1:3306` | `dev` / `dev` or `root` / `root` |
| **Redis** | `redis:6379` | `127.0.0.1:6379` | no password |
| **Mailpit (SMTP)** | `mailpit:1025` | — | `mail()` works out of the box |
