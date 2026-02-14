1️⃣ Docker Introduction – Interview Questions
Q1: What is Docker?

Docker is an open-source platform that enables developers to build, package, and run applications inside containers.

Docker was originally released by Docker, Inc. in 2013.

A container packages:

Application code

Runtime

Libraries

Dependencies

System tools

So the application runs the same in:

Dev

Test

Staging

Production

Q2: What is Containerization?

Containerization is a lightweight virtualization method where applications run in isolated user spaces using the host OS kernel.

It uses:

Linux namespaces

cgroups

2️⃣ Why Containerization Takes the Lead?
🔥 Interview Answer (Short Version)

Containerization became popular because it is:

Lightweight

Faster startup

Portable

Resource efficient

Ideal for microservices

🔍 Detailed Explanation
Feature	Virtual Machines	Containers
OS	Each VM has full OS	Share host OS
Boot Time	Minutes	Seconds
Size	GBs	MBs
Resource Usage	High	Low
Portability	Limited	High

Containers solve the classic:

“It works on my machine” problem.

3️⃣ Containerization vs Virtualization
Q: Difference between Virtualization and Containerization?
🔹 Virtualization

Uses Hypervisor:

Type 1 (Bare Metal)

Type 2 (Hosted)

Example:

VMware

Oracle Corporation (VirtualBox)

Architecture:

Hardware
Hypervisor
Guest OS
App

🔹 Containerization

Architecture:

Hardware
Host OS
Docker Engine
Containers


No separate guest OS.

🎯 Interview One-Liner

Containers virtualize at OS level, VMs virtualize at hardware level.

4️⃣ Problems Docker Solves
Q: What problems does Docker solve?
1️⃣ Environment Inconsistency

Dev ≠ QA ≠ Prod
Docker ensures same environment everywhere.

2️⃣ Dependency Conflicts

Different apps need different versions of libraries.

Docker isolates dependencies per container.

3️⃣ Scalability Issues

Containers start in seconds → easier horizontal scaling.

4️⃣ Resource Waste

VMs consume:

Full OS memory

Separate kernel

Docker shares kernel → less memory usage.

5️⃣ Slow CI/CD

With Docker:

Build once

Run anywhere

Perfect for DevOps pipelines (Jenkins, GitLab CI, etc.)

5️⃣ Docker Architecture
🔷 High-Level Architecture

Docker follows Client-Server architecture.

Docker Client  →  Docker Daemon  →  Containers

1️⃣ Docker Engine

Docker Engine is the core component.

It consists of:

Docker Daemon

REST API

CLI

It is responsible for:

Building images

Running containers

Managing networks

Managing volumes

2️⃣ Docker Client

Command-line interface:

docker build
docker run
docker pull
docker push


It communicates with Docker Daemon using REST API.

Example:

docker run nginx


Here:
Client → sends request → Daemon → creates container.

3️⃣ Docker Daemon (dockerd)

The background service that:

Listens to Docker API requests

Builds images

Runs containers

Manages volumes & networks

It runs on host machine.

🔥 Important Interview Question

Q: Does Docker Client and Docker Daemon run on same machine?

Answer:

By default → Yes

But can run on remote machine using TCP socket

6️⃣ Docker Installation (Linux – Interview Explanation)
Q: How do you install Docker on Linux?
Example: Ubuntu
# Remove old versions
sudo apt remove docker docker-engine docker.io containerd runc

# Install dependencies
sudo apt update
sudo apt install ca-certificates curl gnupg

# Add Docker GPG key
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

# Add repo
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Install Docker
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io

Post Installation
sudo systemctl start docker
sudo systemctl enable docker
sudo docker run hello-world


To avoid sudo:

sudo usermod -aG docker $USER

7️⃣ Scenario-Based Interview Questions
Q1: What happens when you run docker run nginx?

Answer:

Client sends request to daemon

Daemon checks local image

If not present → pulls from Docker Hub

Creates container

Assigns network

Starts container process

Q2: Where are Docker images stored?

Default path:

/var/lib/docker

Q3: What is Docker Hub?

Docker Hub is a public image registry maintained by Docker, Inc..

8️⃣ Advanced Interview Bonus (For Senior Role)
Q: How does Docker achieve isolation?

Using:

Namespaces (PID, NET, MNT, IPC, UTS)

cgroups (CPU, memory limits)

Union File System (OverlayFS)

Q: What is containerd?

containerd is the container runtime used internally by Docker Engine.
