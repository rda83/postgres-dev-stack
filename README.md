# 🐘 PostgreSQL Dev Stack

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
![Docker](https://img.shields.io/badge/docker-compose-blue?logo=docker)
![PostgreSQL](https://img.shields.io/badge/postgres-16.2-336791?logo=postgresql)
![Grafana](https://img.shields.io/badge/grafana-10.2.2-orange?logo=grafana)

**Готовый Docker Compose шаблон для запуска PostgreSQL с мониторингом (Prometheus, Grafana, pgAdmin) в средах разработки и тестирования.**  
Оптимизированные настройки PostgreSQL, изоляция данных на хосте, гибкое управление через профили и поддержка множественных инстансов.

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

Теперь PostgreSQL доступен на порту, указанном в .env (по умолчанию 5432).