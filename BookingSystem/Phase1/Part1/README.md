# 🔨 Application deployment

## ⛓️ The application to docker - Client side

**1. Download the file from (if it doesn't exists): [Docker-compose](https://raw.githubusercontent.com/vheikkiniemi/CybersecurityAndDataPrivacyAutumn2025/refs/heads/main/BookingSystem/Phase1/Part1/docker-compose.yml)**

**OR COPY THIS docker-compose.yml file**

```
services:
  database:
    image: vheikkiniemi/cybersec-db-phase1:v1.1
    restart: always
    container_name: cybersec-db-phase1
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: Secret1234!
      POSTGRES_DB: postgres
    ports:
      - "5432:5432"
    volumes:
      - postgres_data:/var/lib/postgresql/data
  web:
    image: vheikkiniemi/cybersec-web-phase1:v1.1
    container_name: cybersec-web-phase1
    restart: always
    ports:
      - "8000:8000"
    depends_on:
      - database
    environment:
      DATABASE_URL: "postgres://postgres:Secret1234!@host.docker.internal:5432/postgres"
    extra_hosts:
      - "host.docker.internal:host-gateway"

volumes:
  postgres_data:
```

**2. Try to build and run: `docker compose up --build -d`**  
**3. If something doesn't work, try: `docker compose logs`**  
**4. If you want to stop all, try: `docker compose stop`**  
**5. If you want to delete all, try: `docker compose down --volumes`**