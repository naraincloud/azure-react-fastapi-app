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

