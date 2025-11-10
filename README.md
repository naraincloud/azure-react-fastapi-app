# 🚀  Deploying a Full Stack React + FastAPI Application using Docker, Azure Container Registry (ACR), and Azure Virtual Machine (VM)



## 🧠 Introduction

This project demonstrates how I deployed a **full-stack web application** built with **React (frontend)** and **FastAPI (backend)** on **Microsoft Azure**, using **Docker**, **Azure Container Registry (ACR)**, and **Docker Compose**.

It’s a complete DevOps workflow from containerization and image management to cloud based deployment on an Azure Virtual Machine.

---

## ⚠️ Before You Start

Make sure you have the following prerequisites:

- ✅ An **Azure account**  
- ✅ A running Azure Virtual Machine
- ✅ **Docker** and
- ✅**Docker Compose** installed on your VM  
- ✅ Basic knowledge of **Docker containers**

---

## 🧩 Tech Stack Overview

| Component | Technology |
|------------|-------------|
| Frontend | React |
| Backend | FastAPI |
| Containerization | Docker |
| Container Registry | Azure Container Registry (ACR) |
| Hosting | Azure Virtual Machine |
| Orchestration | Docker Compose |

---

🪜 Steps Summary

Step 1: Open & Navigate to Project

Open your terminal or VS Code and navigate to your project folder:

cd Documents
cd react-fastapi-app

Step 2: Write Dockerfiles

Create separate Dockerfiles for both the React frontend and FastAPI backend.

Step 3: Create Azure Container Registries

Public ACR: for frontend images

Private ACR: for backend images


Step 4: Build and Tag Docker Images

docker build -t frontend:latest ./frontend
docker build -t backend:latest ./backend

Step 5: Login & Push to ACR

az acr login --name yourregistry
docker tag frontend:latest yourregistry.azurecr.io/frontend:v1
docker tag backend:latest yourregistry.azurecr.io/backend:v1
docker push yourregistry.azurecr.io/frontend:v1
docker push yourregistry.azurecr.io/backend:v1

Step 6: Create Azure VM

Provision an Ubuntu VM, connect via SSH, and install Docker & Docker Compose.

Step 7: Run with Docker Compose

Deploy both containers together:

sudo docker-compose up -d

Step 8: Access the App

Visit your VM’s public IP in the browser to confirm deployment.
