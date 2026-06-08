# Docker Basics — Class Activity Log

**Platform:** [KodeKloud Docker Lab](https://kodekloud.com/studio/labs/docker)  
**Topic:** Introduction to Docker  


## 📌 What I Learned

### 1. Docker Basic Commands

These are the foundational commands I practiced during the lab:

| Command | Description |
|--------|-------------|
| `docker ps` | List all **running** containers |
| `docker ps -a` | List **all** containers (running + stopped) |
| `docker images` | List all available images on the host |
| `docker pull <image>` | Download an image from Docker Hub |
| `docker stop <container>` | Stop a running container |
| `docker rm <container>` | Remove a stopped container |
| `docker rmi <image>` | Remove/delete an image |
| `docker system prune -a` | Remove all unused containers, images, and networks |
| `docker info` | Display system-wide Docker information |

![](screenshots/Screenshot%202026-05-21%20170521.png)

### 2. Docker Run

The `docker run` command is used to create and start a container from an image.

**Basic syntax:**
```bash
docker run <image>
```

**Flags I learned:**

| Flag | Description |
|------|-------------|
| `-d` | Run container in **detached** (background) mode |
| `--name` | Assign a custom name to the container |
| `-p <host>:<container>` | Map a host port to a container port |

**Examples I practiced:**

```bash
# Run a Redis container in the background
docker run -d --name redis-container redis

# Run a web app with port mapping and a custom name
docker run -d --name blue-app -p 38282:8080 kodekloud/simple-webapp:blue
```

![](screenshots/Screenshot%202026-05-21%20171858.png)

## Key Concepts

- **Image** — A read-only blueprint/template used to create containers (e.g. `redis`, `alpine`)
- **Container** — A running instance of an image
- **Port Mapping** — Connects a port on your host machine to a port inside the container so you can access the app from outside
- **Detached Mode** — Running a container in the background so your terminal stays free


## Cleanup Commands

```bash
# Stop all running containers
docker stop $(docker ps -q)

# Remove all containers
docker rm $(docker ps -aq)

# Remove all images
docker rmi -f $(docker images -q)
```


## Takeaways

- Docker makes it easy to run applications in isolated environments without installing them directly on the host.
- Images don't "run" — containers do. You stop/remove containers, and delete images separately.
- Port mapping (`-p`) is essential for accessing containerized web apps from a browser.
- Always remove containers before removing the images they were built from.

---

## What is Jenkins?
Jenkins automates the repetitive tasks involved in building, testing, and deploying software. Whenever a developer pushes code, Jenkins can automatically pick it up, run tests, and ship it — without manual intervention.

## Key Concepts
Concept                Description
Pipeline               A series of automated steps defined in Jenkinsfile
Job / ProjectAn        individual task Jenkins can run
Agent / NodeA          machine where Jenkins executes the work
Plugin                 Extensions to integrate with external tools (1,800+ available)
Build                  A single execution of a job

## Common Integrations

Source Control — GitHub, GitLab, Bitbucket
Build Tools — Maven, Gradle, npm, Make
Containers — Docker, Kubernetes
Cloud — AWS, Azure, GCP
Notifications — Slack, Email, PagerDuty
Testing — JUnit, Selenium, SonarQube

## Why Use Jenkins?

- Free and open-source
- Self-hosted (full control over your environment)
- Massive plugin ecosystem
- Supports any language or platform
- Active community and enterprise support (CloudBees)

# Run Jenkins with Docker
docker run -p 8080:8080 -p 50000:50000 jenkins/jenkins:lts