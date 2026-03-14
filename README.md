# 🐘 PostgreSQL Dev Stack

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
![Docker](https://img.shields.io/badge/docker-compose-blue?logo=docker)
![PostgreSQL](https://img.shields.io/badge/postgres-16.2-336791?logo=postgresql)
![Grafana](https://img.shields.io/badge/grafana-10.2.2-orange?logo=grafana)

**Готовый Docker Compose шаблон для запуска PostgreSQL с мониторингом (Prometheus, Grafana, pgAdmin) в средах разработки и тестирования.**  

---

## 📦 Требования

- **Docker Engine** версии 20.10 или новее
- **Docker Compose V2** (встроен в Docker Desktop, либо установлен отдельно)
- **Git** (для клонирования)

---

## ⚡ Быстрый старт

1. **Клонируйте репозиторий:**
   ```bash
   git clone https://github.com/rda83/postgres-dev-stack.git
   cd postgres-dev-stack

2. **Создайте файл .env из шаблона и отредактируйте его:** 
    - cp .env.example .env
    - Откройте .env в редакторе и укажите свои значения (параметры, пути к данным и т.д.)

3. **Создайте директории для данных (укажите абсолютные пути из .env):**
    ```bash 
    mkdir -p /absolute/path/to/postgres/data
    mkdir -p /absolute/path/to/pgadmin/data
    mkdir -p /absolute/path/to/prometheus/data
    mkdir -p /absolute/path/to/grafana/data

4. **Запустите стек (по умолчанию только PostgreSQL):**
    ```bash
    docker compose up -d

5. **Проверьте статус:**
    - docker compose ps

Теперь PostgreSQL доступен на порту, указанном в .env (по умолчанию 
5432).

---

## 🎛️ Примеры команд

1. **Запустить только PostgreSQL** (без мониторинга и pgAdmin)
   ```bash
   docker compose up -d

2. **Запустить PostgreSQL + мониторинг** (Prometheus, экспортер, Grafana)
   ```bash
   docker compose --profile monitoring up -d

3. **Запустить PostgreSQL + pgAdmin**
   ```bash
   docker compose --profile tools up -d

4. **Запустить всё сразу** (PostgreSQL + мониторинг + pgAdmin)
   ```bash
   docker compose --profile monitoring --profile tools up -d

---

## 🔁 Множественные инстансы

Если вам нужно запустить несколько независимых стеков на одной машине (например, для разных проектов или окружений), используйте один из двух подходов.

**Вариант 1: Полное клонирование репозитория**
    ```bash
    git clone <url> ~/project-dev1
    cd ~/project-dev1
    cp .env.example .env
    # отредактируйте .env (порты, пути к данным)
    docker compose up -d

    cd ..
    git clone <url> ~/project-dev2
    cd ~/project-dev2
    # аналогично, но с другими портами и путями
    docker compose up -d

**Вариант 2: Одна папка, разные .env файлы и имена проектов**  
    Создайте несколько файлов `.env`, например:

    - `.env.dev1`
    - `.env.dev2`

    В каждом укажите уникальные порты и пути к данным.

    Запустите инстансы с флагом `-p` (имя проекта):

    ```bash
    docker compose --env-file .env.dev1 -p dev1 up -d
    docker compose --env-file .env.dev2 -p dev2 up -d

---    