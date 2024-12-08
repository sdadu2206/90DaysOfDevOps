# **Node.js To-Do App with CI/CD Pipeline** 🚀

This document provides a detailed solution for setting up a CI/CD pipeline for a Node.js To-Do app using Jenkins, Docker, Docker Compose, and GitHub Webhooks. It's a practical DevOps guide! 🎯

---

## **Table of Contents**
1. [Project Overview](#1-project-overview)
2. [Prerequisites](#2-prerequisites)
3. [Setup Instructions](#3-setup-instructions)
   - [Clone Repository](#step-1-clone-the-repository-📁)
   - [Connect Jenkins with GitHub](#step-2-connect-jenkins-with-github-🔌)
   - [Add Webhooks](#step-3-add-webhooks-🔔)
4. [Running the Application Using Docker Compose](#4-running-the-application-using-docker-compose-🐳)
5. [Testing the CI/CD Pipeline](#5-test-the-pipeline)
6. [Known Issues](#6-known-issues)
7. [Contributing](#7-contributing)
8. [License](#8-license)

---

### **1. Project Overview**

This repository is designed to:
- Deploy a **Node.js To-Do application** 📝.
- Implement a **CI/CD pipeline** using:
  - **Jenkins** for automation.
  - **Docker Compose** for container orchestration.
  - **GitHub Webhooks** for build triggers.

---

### **2. Prerequisites**

Before starting, ensure you have:
- **Jenkins** installed and running.
- **Docker** and **Docker Compose** installed.
- A **GitHub Account**.
- **Node.js** (optional for local testing).

---

### **3. Setup Instructions**

#### **Step 1: Clone the Repository** 📁
Run the following commands:
```bash
git clone https://github.com/<your-username>/node-todo-cicd.git
cd node-todo-cicd
```

---

#### **Step 2: Connect Jenkins with GitHub** 🔌

1. **Install the GitHub Plugin in Jenkins**:
   - Navigate to `Manage Jenkins → Manage Plugins → Available`.
   - Search for **GitHub Plugin** and install it.

2. **Create a New Jenkins Job**:
   - In Jenkins, click `New Item` → Select **Freestyle Project** → Name the job (e.g., **Node-Todo-CI/CD**).
   - Under **Source Code Management**, select **Git** and add:
     - **Repository URL:** Your forked repo's URL.
     - **Credentials:** GitHub username and personal access token.
   - In **Build Triggers**, enable **GitHub hook trigger for GITScm polling**.

---

#### **Step 3: Add Webhooks** 🔔

1. Go to your GitHub repository: `Settings → Webhooks → Add Webhook`.
2. Configure the webhook:
   - **Payload URL:** `http://<jenkins-server>/github-webhook/`
   - **Content type:** `application/json`.
   - **Trigger Event:** Select **Just the push event**.
3. Save the webhook.

---

### **4. Running the Application Using Docker Compose** 🐳

1. **Create a `docker-compose.yml` File**:
   Add the following content in the root directory:

```yaml
version: '3.8'

services:
  app:
    image: node:16
    container_name: node-todo-app
    working_dir: /app
    volumes:
      - .:/app
    command: npm install && npm start
    ports:
      - "3000:3000"
    networks:
      - app-network

networks:
  app-network:
    driver: bridge
```

2. **Configure Jenkins to Use Docker Compose**:
   - Add a build step in Jenkins: `Execute Shell`.
   - Include the following command:
     ```bash
     docker-compose -f /path/to/your/docker-compose.yml up --build -d
     ```

---

### **5. Test the Pipeline**

1. **Trigger the Build**:
   - Manually trigger the Jenkins job or push changes to the GitHub repo.
2. **Verify Jenkins Dashboard**:
   - Check the build logs for success or failure.
3. **Test the Application**:
   - Open a browser and navigate to **http://localhost:3000** to access the running app! 🎉

---

### **6. Known Issues**

- **Webhook Errors**:
  - Ensure Jenkins is accessible from the public internet (e.g., via a reverse proxy).
- **Docker Build Fails**:
  - Check file permissions or syntax in the `docker-compose.yml` file.

---

### **7. Contributing**

Contributions are welcome! Feel free to:
- Fork this repository.
- Submit pull requests with improvements or fixes. 😊

---

### **8. License**

This project is licensed under the **MIT License**.

---

By following these steps, you can successfully deploy the Node.js To-Do app with a robust CI/CD pipeline. 🚀

[LinkedIn](https://www.linkedin.com/posts/sdadu2206_90daysofdevops2024day25solutionmd-at-activity-7271348514117316608-MSJA?utm_source=share&utm_medium=member_desktop)
Project Link: [Node.js To-Do App with CI/CD Pipeline](https://github.com/sdadu2206/90DaysOfDevOps/blob/master/2024/day25/solution.md)
