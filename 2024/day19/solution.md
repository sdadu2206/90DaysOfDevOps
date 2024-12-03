# Day 19 Solution: Docker for DevOps Engineers  
**Objective:** Learn and implement Docker Compose, Docker Volumes, and Docker Networks.  

---

## 🐳 **Task 1: Create a Multi-Container `docker-compose.yml` File**

### Step 1: Create a `docker-compose.yml` file  
This file will define two services:  
1. **web** – A simple web application (e.g., Nginx).  
2. **db** – A database service (e.g., MySQL).

```yaml
version: '3.9'

services:
  app:
    image: nginx:latest
    ports:
      - "8080:80"
    networks:
      - app-network
    depends_on:
      - db
    volumes:
      - app-data:/usr/share/nginx/html

  db:
    image: mysql:latest
    environment:
      MYSQL_ROOT_PASSWORD: rootpassword
      MYSQL_DATABASE: appdb
    networks:
      - app-network
    volumes:
      - db-data:/var/lib/mysql

networks:
  app-network:

volumes:
  app-data:
  db-data:
```

---

### Step 2: Run the Application  

Start the multi-container application using Docker Compose:  

```bash
docker-compose up -d
```

---

### Step 3: Scale the Web Service  

To scale the web service to 3 replicas:  

```bash
docker-compose up -d --scale app=3
```

---

### Step 4: Check the Status of Containers  

Use the following commands to monitor your containers:  

- **List running containers:**  
  ```bash
  docker-compose ps
  ```

- **View logs for the `web` service:**  
  ```bash
  docker-compose logs app
  ```

---

### Step 5: Shut Down the Application  

To stop and remove all containers, networks, and volumes:  

```bash
docker-compose down -v
```

---

## 📦 **Task 2: Use Docker Volumes to Share Data Between Containers**

### Step 1: Create a Named Volume  

Create a volume named `shared_data`:  

```bash
docker volume create shared_data
```

---

### Step 2: Run Containers with Shared Volume  

Run two containers (`container1` and `container2`) that share the `shared_data` volume:  

```bash
docker run -d --name container1 --mount source=shared-data,target=/data nginx
docker run -d --name container2 --mount source=shared-data,target=/data httpd
```

---

### Step 3: Write Data to the Volume  

Write a file in `container1` and check if it appears in `container2`:  

1. **Write a file in `container1`:**  
   ```bash
   docker exec container1 bash -c "echo 'Hello from Container 1' > /data/hello.txt"
   ```

2. **Read the file from `container2`:**  
   ```bash
   docker exec container2 cat /data/hello.txt
   ```

---

### Step 4: Verify Volumes  

List all Docker volumes:  

```bash
docker volume ls
```

---

### Step 5: Clean Up  

Remove the containers and the volume:  

```bash
docker rm -f container1 container2
docker volume rm shared_data
```

---

## 📋 **Summary**  

- You created a multi-container `docker-compose.yml` file to manage application and database services.  
- You scaled the web service, viewed logs, and managed the application lifecycle using Docker Compose commands.  
- You shared data between multiple containers using Docker Volumes and verified data consistency.

Keep going strong with your #90DaysOfDevOps challenge! 🚀

[LinkedIn](https://www.linkedin.com/posts/sdadu2206_docker-volume-network-day-19-guide-activity-7269372185557766144-tDo7?utm_source=share&utm_medium=member_desktop)
