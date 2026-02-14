## Docker Adhoc Commands

Adhoc commands = day-to-day operational commands you use for debugging, monitoring, testing, and managing containers in real environments.

## 1️⃣ Container Lifecycle Commands
▶ Run Container
docker run nginx


Detached mode + Port mapping:

docker run -d -p 8080:80 nginx


Run with name:

docker run -d --name mynginx nginx

📋 List Containers
docker ps        # Running
docker ps -a     # All

⛔ Stop / Start / Restart
docker stop container_id
docker start container_id
docker restart container_id

❌ Remove Container
docker rm container_id
docker rm -f container_id   # Force remove


Image Related Commands
📥 Pull Image
docker pull nginx

📦 List Images
docker images

🏷 Tag Image
docker tag nginx myrepo/nginx:v1

🚀 Push to Registry
docker push myrepo/nginx:v1


Push to:

Docker Hub

Amazon Elastic Container Registry

🗑 Remove Image
docker rmi image_id

## 🟠 3️⃣ Debugging & Troubleshooting Commands (Very Important)
📜 Check Logs
docker logs container_id
docker logs -f container_id

🖥 Enter Running Container
docker exec -it container_id bash


If Alpine:

docker exec -it container_id sh

🔍 Inspect Container (Deep Info)
docker inspect container_id


Used to check:

IP address

Mount points

Environment variables

Network settings

📊 Check Resource Usage
docker stats


Shows:

CPU

Memory

Network

Block I/O

## 🔵 4️⃣ Networking Commands
📡 List Networks
docker network ls

🔎 Inspect Network
docker network inspect bridge

🔗 Connect Container to Network
docker network connect mynetwork container_id

## 🟣 5️⃣ Volume Commands
📂 List Volumes
docker volume ls

🔍 Inspect Volume
docker volume inspect volume_name

🗑 Remove Volume
docker volume rm volume_name

## 🔴 6️⃣ Cleanup Commands (Production Maintenance)
Remove All Stopped Containers
docker container prune

Remove Unused Images
docker image prune

Remove Everything Unused
docker system prune -a


⚠ Be careful in production.

## 🟤 7️⃣ Build & Run Adhoc Testing
Build Image
docker build -t myapp .

Run with Environment Variables
docker run -e ENV=prod myapp

Run with Volume Mount
docker run -v /host/path:/container/path myapp

## 🧠 Real DevOps Scenario Examples
### 🚨 Scenario 1: Container Keeps Restarting

Check:

docker logs container_id
docker inspect container_id

### 🚨 Scenario 2: Port Already in Use

Check:

netstat -tulpn
docker ps

### 🚨 Scenario 3: High Memory Usage

Check:

docker stats

🏗 CI/CD Usage Example

In pipelines like:

Jenkins

GitLab CI

GitHub Actions

Typical flow:

docker build -t app:v1 .
docker tag app:v1 repo/app:v1
docker push repo/app:v1

