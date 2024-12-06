# 

## Task 1: Build and Run Your App Using Docker in Jenkins

### Step 1: Create an Agent for Your App
1. Open Jenkins and navigate to **Manage Jenkins** > **Manage Nodes and Clouds**.
2. Add a new agent (a machine where Jenkins will run your jobs).
3. Connect this agent to your app's Docker environment.

### Step 2: Create a New Freestyle Project
1. Go to the Jenkins Dashboard and click **New Item**.
2. Choose **Freestyle Project**, and give it a name (e.g., `DockerAppBuild`).

### Step 3: Add Docker Build and Run Steps
1. In the **Build** section, click **Add Build Step** > **Execute Shell**.
2. Add the following Docker build command:
    ```bash
    docker build -t <your-dockerhub-username>/my-web-app:1.0 .
    ```
3. Add another build step to run the Docker container:
    ```bash
    docker run -d -p 8080:80 <your-dockerhub-username>/my-web-app:1.0
    ```
   This command will start your app on port `8080`.

### Step 4: Test It Out!
1. Save the project and click **Build Now**.
2. Jenkins will:
    - Build your Docker image 🛠️.
    - Run the container in seconds 🐳.

---

## Task 2: Manage Multiple Containers with Docker Compose

### Step 1: Create a New Jenkins Project
1. Create another **Freestyle Project** (e.g., `Docker Compose Project` or `MultiContainerApp`).

### Step 2: Add Docker-Compose Commands
1. In the **Build** section, add a shell step to start your containers:
    ```bash
    docker-compose up -d
    ```
    This command will start all services (e.g., web app and database) defined in your `docker-compose.yml` file.

2. Add another step to clean up after the job is done:
    ```bash
    docker-compose down
    ```
    This will stop and remove the containers defined in the compose file. 🧹

### Step 3: Use the Hint!
Use the Docker Compose file from the previous task that includes both your application and database services.

#### Example `docker-compose.yml`:
```yaml
version: '3'
services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"  # Expose port 8080 on your machine to access the web service
    environment:
      ENV: production
    volumes:
      - .:/app
  db:
    image: mysql:latest
    environment:
      MYSQL_ROOT_PASSWORD: mypassword123  # Set environment variables
```

By completing these tasks, you’ve successfully:

Built and deployed a Docker app using Jenkins.
Managed multiple containers using Docker Compose in Jenkins.
Jenkins now automates the build and deployment of your Docker containers, saving time and effort. 🚀


[LinkedIn](https://www.linkedin.com/posts/sdadu2206_jenkins-freestyle-project-setup-guide-activity-7270823804744929281-9bhW?utm_source=share&utm_medium=member_desktop)

