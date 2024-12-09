# Jenkins Pipeline

## What is a Jenkins Pipeline? 🤔

Think of a pipeline like an assembly line in a factory. It's a sequence of steps (or jobs) that get executed one after the other. Each step builds on the previous one. For Jenkins, a pipeline automates the entire process of building, testing, and deploying your code.

There are two types of pipelines:

- **Declarative Pipeline**: This is the new, easier way to define your pipeline using a clear structure and syntax.
- **Scripted Pipeline**: The traditional way, using Groovy code, which is more flexible but can be a bit complicated.

---

## Why Should You Use a Pipeline? 🤔

By defining your Jenkins pipeline in a file (called a Jenkinsfile), you get several advantages:

- **Version Control**: You can track your pipeline like any other code, making it easier to collaborate and review.
- **Automation**: Pipelines can automatically run for every change (like creating new branches or pull requests), reducing manual work and ensuring consistency.

---

## Pipeline Syntax Explained

Here's the basic syntax for a Jenkins Declarative Pipeline:

```groovy
pipeline {
    agent any  // Can run on any available agent
    stages {    // Collection of stages (jobs)
        stage('Build') {
            steps {
                // Define steps for build (e.g., compile, package, etc.)
            }
        }
        stage('Test') {
            steps {
                // Define steps for tests (e.g., unit tests, integration tests)
            }
        }
        stage('Deploy') {
            steps {
                // Define deployment steps (e.g., push to server, cloud)
            }
        }
    }
}
```
Explanation of Syntax:
- `pipeline`: Top-level block defining the whole pipeline.
- `agent any`: Specifies that the pipeline can run on any available Jenkins agent.
- `stages`: A collection of `stage` blocks, each representing a job in the pipeline.
  - `stage('Build')`: The first stage where code is compiled or built.
  - `stage('Test')`: The second stage where tests are executed.
  - `stage('Deploy')`: The last stage where the code is deployed.

---

## Task-01: Creating Your First Jenkins Pipeline

Let’s create a Jenkins Pipeline Job using the Declarative pipeline! 🎉

### Steps to Follow:

#### 1. Create a New Jenkins Job:
   - Go to Jenkins Dashboard.
   - Click on **New Item**.
   - Choose **Pipeline** (not Freestyle project).
   - Enter a name for your job (e.g., `MyFirstPipeline`).
   - Click **OK**.

#### 2. Configure the Pipeline:
   - Scroll down to the **Pipeline** section.
   - In the **Definition** dropdown, select **Pipeline script**.
   - Copy-paste the following Declarative pipeline code into the script section:

```groovy
/* Requires the Docker Pipeline plugin */
pipeline {
    agent { docker { image 'node:22.12.0-alpine3.20' } }
    stages {
        stage('build') {
            steps {
                sh 'node --version'
            }
        }
    }
}
```

#### 3. Run the Pipeline:
   - Save your configuration and click on **Build Now**.
   - Watch your first Pipeline run.

---

### 🎉 Congratulations! 

You've just created your first Jenkins pipeline using Declarative syntax! Now you can automate the entire process of building, testing, and deploying your code.

---

[LinkedIn](https://www.linkedin.com/posts/sdadu2206_jenkins-declarative-pipeline-day-26-guide-activity-7271898125756211200-JAMH?utm_source=share&utm_medium=member_desktop)
