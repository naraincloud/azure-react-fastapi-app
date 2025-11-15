# 🚀  Deploying a Full Stack React + FastAPI Application using Docker, Azure Container Registry (ACR), and Azure Virtual Machine (VM)



## 🧠 Introduction

This project demonstrates how I deployed a **full-stack web application** built with **React (frontend)** and **FastAPI (backend)** on **Microsoft Azure**, using **Docker**, **Azure Container Registry (ACR)**, and **Docker Compose**.

It’s a complete DevOps workflow from containerization and image management to cloud based deployment on an Azure Virtual Machine.

---

## ⚠️ Prerequisite 


Before you start, make sure you have the following prerequisites:

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

## 📁 Project Structure

```
azure-react-fastapi-app/
├── React/                 # Frontend application
├── FastAPI/               # Backend API
├── docker-compose.yml     # Multi-container orchestration
├── Dockerfile.frontend    # React container setup
└── Dockerfile.backend     # FastAPI container setup
```
---
## 🪜 Steps Summary

Step 1: Open & Navigate to Project

Open your terminal or VS Code and navigate to your project folder:

```bash
cd Documents
cd azure-react-fastapi-app
```
This folder contains both your frontend (React) and backend (FastAPI) applications

Step 2: Create a Dockerfile for the FastAPI Backend

```Create backend/Dockerfile:

# FastAPI Backend Dockerfile

FROM python:3.10-slim
WORKDIR /app
COPY ./requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
EXPOSE 8000
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", 8000"]
```

Step 3: Create a Dockerfile for the React Frontend

```
Create frontend/Dockerfile:

# React Frontend Dockerfile

FROM node:18-alpine

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

RUN npm install -g serve

EXPOSE 3000

CMD ["serve", "-s", "build", "-l", "3000"]
```

Step 4: Azure Container Registry
log into your azure 

· Create ACR: publicareg.azurecr.io
· Configured authentication and access policies

Step 5: Build & Push Images

```bash
docker build -t publicareg.azurecr.io/react-frontend:latest .
docker build -t publicareg.azurecr.io/fastapi-backend:latest .
docker push publicareg.azurecr.io/react-frontend:latest
docker push publicareg.azurecr.io/fastapi-backend:latest
```

Step 6: Azure Infrastructure

· Resource Group: rest-fastapi
· Virtual Machine: Ubuntu 22.04
· Network Security Groups configured
· Public IP: 52.226.72.138


Step 7: Docker Compose Deployment

```yaml
services:
  frontend:
    image: publicareg.azurecr.io/react-frontend:latest
    ports: ["3000:80"]
    
  backend:
    image: publicareg.azurecr.io/fastapi-backend:latest  
    ports: ["8000:8000"]
```


Step 8: Application Access

· Frontend: http://52.226.72.138:3000
· Backend API: http://52.226.72.138:8000

---
## 🔗 Live Demo

· Frontend: http://52.226.72.138:3000
· Backend API: http://52.226.72.138:8000

---
