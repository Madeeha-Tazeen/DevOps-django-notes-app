# 📝 Django Notes App

A simple full-stack Notes application built with **React, Django REST Framework, and MySQL**.

The application is containerized using **Docker Compose**. **Nginx** is used as a reverse proxy, and **Gunicorn** is used to run the Django application.

## 🛠️ Tech Stack

* React
* Django REST Framework
* MySQL
* Gunicorn
* Nginx
* Docker & Docker Compose

---

## 📁 Project Structure

```text
CodeOrbit_django-notes-app-main/
│
├── api/                 # Django REST API
├── mynotes/             # React frontend
├── nginx/               # Nginx configuration
│   ├── Dockerfile
│   └── default.conf
│
├── Dockerfile           # Django Docker image
├── docker-compose.yml   # Runs all services
├── requirements.txt
└── manage.py
```

---

# 🚀 How to Run

## Prerequisites

Install **Docker Desktop** and make sure it is running.

Check that Docker is installed:

```bash
docker --version
```

Check Docker Compose:

```bash
docker compose version
```

You don't need to install Python, Django, MySQL, Gunicorn, or Nginx separately when using Docker.

---

## 1. Clone the Repository

```bash
git clone https://github.com/madeeha-tazeen/devops-django-notes-app.git
```

Go into the project:

```bash
cd devops-django-notes-app
cd CodeOrbit_django-notes-app-main
```

---

## 2. Build and Start the Application

Run:

```bash
docker compose up --build
```

Docker will build the required images and start:

* **Nginx**
* **Django + Gunicorn**
* **MySQL**

The first startup may take a little longer because Docker needs to download the required images and dependencies.

---

## 3. Open the Application

Once the containers are running, open:

**http://localhost**

The request flow is:

```text
Browser
   ↓
Nginx :80
   ↓
Django + Gunicorn :8000
   ↓
MySQL :3306
```

---

## 4. Check Running Containers

Open another terminal and run:

```bash
docker compose ps
```

You should see the project's services running.

---

# 🛑 Stop the Application

To stop the containers:

```bash
docker compose down
```

To start the application again later:

```bash
docker compose up -d
```

Then open:

```text
http://localhost
```

---

# 🔄 If You Make Changes

If you change the Dockerfile, dependencies, or Nginx configuration, rebuild the application:

```bash
docker compose up --build
```

---

# 🔍 Troubleshooting

If the application does not open, check the containers:

```bash
docker compose ps
```

Then check the logs:

```bash
docker compose logs
```

For continuous logs:

```bash
docker compose logs -f
```

If **port 80 is already in use**, stop the application using that port or change the Nginx host port in `docker-compose.yml`.

---

## 🐳 Docker Setup

The application uses three services connected through a Docker network:

```text
             ┌──────────────┐
             │    Nginx     │
             │    :80       │
             └──────┬───────┘
                    │
                    ▼
             ┌──────────────┐
             │ Django       │
             │ + Gunicorn   │
             │    :8000     │
             └──────┬───────┘
                    │
                    ▼
             ┌──────────────┐
             │    MySQL     │
             │    :3306     │
             └──────────────┘
```

Nginx receives requests from the browser and forwards them to the Django application. Django then communicates with MySQL for storing and retrieving notes.

---

## 👩‍💻 Author

**Madeeha Tazeen**

B.E. Computer Science and Engineering
