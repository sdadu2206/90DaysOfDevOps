# CI/CD Pipeline Solution for Node.js Application 🚀

## Task 1: Set Up Your Repository and Connect Jenkins with GitHub 📂🔗

### Step 1: Fork the Repository 📁
1. Go to the GitHub repository: [node-todo-cicd](https://github.com/sdadu2206/node-todo-cicd).
2. Click the **Fork** button in the top-right corner of the page.
3. Now, you have your own copy of the repository! 🎉

### Step 2: Connect Jenkins with GitHub 🔌

1. **Install GitHub Integration Plugin in Jenkins**:
   - Go to **Jenkins → Manage Jenkins → Manage Plugins → Available**.
   - Search for "**GitHub Plugin**" and install it.

2. **Create a New Jenkins Job**:
   - In Jenkins, click on **New Item**.
   - Enter a name for your job (e.g., "Node-Todo-CI-CD").
   - Select **Freestyle project**.
   
3. **Configure Source Code Management**:
   - Under **Source Code Management**, select **Git**.
   - In the **Repository URL**, paste your forked repository URL.
   
4. **Add Credentials**:
   - Add your GitHub credentials (username and personal access token).

5. **Configure Build Triggers**:
   - Under **Build Triggers**, check the **GitHub hook trigger for GITScm polling**.

### Step 3: Set Up GitHub Webhook 🔔

1. Go to your **GitHub repository** and click on **Settings** → **Webhooks** → **Add webhook**.
2. In the **Payload URL**, enter your Jenkins server’s URL followed by `/github-webhook/` (e.g., `http://your-jenkins-server/github-webhook/`).
3. Set **Content type** to `application/json`.
4. Select **Just the push event** for the webhook.
5. Leave the other settings as default and click **Add webhook**.

Now, your Jenkins job will trigger automatically on every push to GitHub! 🎉

---

## Task 2: Run the Application Using Docker Compose 🐳

### Step 1: Create a Docker Compose File 📄

Create a `docker-compose.yml` file in your repository's root folder with the following content:

```
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

This docker-compose.yml file does the following:

- Uses the official Node.js 16 Docker image.
- Mounts your current project folder to the container’s working directory.
- Runs npm install and npm start to set up and start your Node.js app.
- Maps port 3000 from your container to the host machine, making the app accessible in the browser.
  
### Step 2: Configure Jenkins to Use Docker Compose 🐳
In your Jenkins job, go to the Build section and click Add Build Step → Execute Shell.

Add the following command to run Docker Compose:

```
docker-compose -f /path/to/your/docker-compose.yml up --build -d
```
This will build and start your Node.js app in the background. 🏃‍♂️

### Step 3: Test Your Pipeline 🔍
1. Trigger the Jenkins job manually or push a change to your GitHub repository.
2. Jenkins will pull the latest code from GitHub, build the Docker image, and start the Node.js application using Docker Compose.
3. Go to your Jenkins dashboard to check the build status.
4. Once successful, open your browser and go to http://localhost:3000 to see the app in action! 🚀

---

🎉 Congratulations! You’ve successfully set up a CI/CD pipeline using Jenkins, GitHub, and Docker Compose for your Node.js application. 🎉

Happy coding! 👨‍💻

[LinkedIn]()
