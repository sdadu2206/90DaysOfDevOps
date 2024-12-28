# Jenkins Declarative Pipeline with Docker

This guide walks you through integrating Docker with Jenkins using declarative pipelines. We will cover building and running Docker containers in Jenkins and how to avoid common errors when re-running jobs.

## 📋 Prerequisites

Before diving into the tasks, make sure the following setup is ready:

1. **Jenkins Installed** - Ensure Jenkins is installed and running. If you need help, check out my [Jenkins Installation Guide](https://drops.hashnode.dev/jenkins-setup-simple-installation-steps).

2. **Docker Installed** - Docker must be installed and running on your Jenkins server, check out my [Docker Installation Guide](https://drops.hashnode.dev/docker-for-devops-engineers-dive-into-container-magic). Verify it by running the following command:
   ```bash
   docker --version
   ```

3. **Jenkins Docker Plugin** - Install the Jenkins Docker Pipeline plugin:
   - Navigate to **Manage Jenkins > Plugins > Available Plugins**.
   - Search for **Pipeline Plugin** and **Docker Pipeline** and install them.

4. **Docker Permissions** - The Jenkins user must have Docker permissions:
   ```bash
   sudo usermod -aG docker jenkins
   ```

5. **Basic Docker Knowledge** - Familiarity with `docker build` and `docker run` commands.

6. **Declarative Pipeline Basics** - If you're new to Jenkins Declarative Pipelines, check out [Day 26](https://drops.hashnode.dev/jenkins-declarative-pipeline-a-step-by-step-guide-for-day-26) for a refresher.

---

## 🛠️ Task 1: Docker Integrated Declarative Pipeline with Shell Commands

Let’s start by building a Docker image and running it using shell commands inside Jenkins pipeline stages.

### Pipeline Syntax:
```groovy
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t trainwithshubham/django-app:latest .'
            }
        }

        stage('Run') {
            steps {
                sh 'docker run -d trainwithshubham/django-app:latest'
            }
        }
    }
}
```

### 🧩 Key Points:
- **Build Stage**: Uses the `docker build` command to create a Docker image tagged as `latest`.
- **Run Stage**: Launches the container in **detached mode**.

⚠️ **Note**: If you re-run the pipeline without cleaning up, you may face errors due to existing containers. **Task 2** will solve this problem! 🛠️

---

## 🧰 Task 2: Avoid Errors with Docker Groovy Syntax

To avoid errors when re-running the job, we'll use the Docker Groovy syntax. This syntax automatically manages container lifecycles, making the process more robust.

### Pipeline Syntax:
```groovy
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    def customImage = docker.build("trainwithshubham/django-app:latest")
                }
            }
        }

        stage('Run') {
            steps {
                script {
                    customImage.run("-d")
                }
            }
        }
    }
}
```

### 📝 Explanation:
- **docker.build()** 🛠️: Builds the Docker image.
- **.run('-d')** 🏃: Runs the container in detached mode.

With this approach, Jenkins handles Docker builds and runs without conflicts. **No more errors** – just smooth sailing! 🚢

---

## 🔥 Final Thoughts

🎊 **Congratulations!** You’ve just leveled up your CI/CD skills by integrating Docker with Jenkins Declarative Pipelines. This setup allows for faster, error-free building, testing, and deployment of your applications. 💯

---

[LinkedIn](https://www.linkedin.com/posts/sdadu2206_jenkins-pipeline-with-docker-integration-activity-7278773541905354752-Q9-k?utm_source=share&utm_medium=member_desktop)
