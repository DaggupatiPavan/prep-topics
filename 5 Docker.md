### **Docker Interview Preparation Guide**  

Docker is a key skill in DevOps interviews, as it is widely used for containerization and microservices deployment. Below is a structured guide on Docker topics you should focus on for your interviews.

---

## **1. Docker Basics**  
Before diving into advanced topics, make sure you have a strong understanding of the fundamentals.

### **1.1 What is Docker?**
- Explanation of **containerization** vs. traditional virtualization.  
- **Why use Docker?** (Lightweight, portability, faster deployment, etc.)  
- Differences between **VMs and Containers**.  

> **Example Question:** What are the advantages of using Docker over traditional VMs?

---

## **2. Core Docker Components**
### **2.1 Docker Architecture**
- **Docker Daemon** – Runs on the host system and manages containers.  
- **Docker CLI** – Used to interact with Docker.  
- **Docker Registry** – Stores Docker images (e.g., **Docker Hub, AWS ECR, GCR, Azure ACR**).  
- **Docker Objects** – Containers, images, volumes, networks.  

> **Example Question:** Can you explain the Docker architecture and its components?

---

### **2.2 Docker Images & Containers**
- **Docker Images** – Read-only templates used to create containers.  
- **Containers** – Running instances of Docker images.  
- **Layers in Docker Images** – How images are built using layers.  
- **Union File System (UFS)** – How Docker images store data efficiently.  

#### **Basic Commands**
```sh
# Pull an image
docker pull nginx

# Run a container
docker run -d --name my-container nginx

# List running containers
docker ps

# List all containers
docker ps -a

# Stop a container
docker stop my-container

# Remove a container
docker rm my-container

# Remove an image
docker rmi nginx
```
> **Example Question:** What happens when you run `docker run -d nginx`?

---

## **3. Dockerfile & Image Creation**
### **3.1 Writing a Dockerfile**
- How to create a **Dockerfile**.  
- Common **Dockerfile Instructions**:
  - `FROM` – Base image.
  - `RUN` – Execute commands.
  - `COPY` / `ADD` – Copy files.
  - `CMD` vs. `ENTRYPOINT` – Differences.
  - `WORKDIR` – Set working directory.
  - `ENV` – Set environment variables.
  - `EXPOSE` – Define ports.

#### **Example Dockerfile**
```dockerfile
# Use official Nginx image
FROM nginx:latest

# Copy custom index.html
COPY index.html /usr/share/nginx/html/

# Expose port 80
EXPOSE 80

# Start Nginx server
CMD ["nginx", "-g", "daemon off;"]
```
```sh
# Build and run the container
docker build -t my-nginx .
docker run -d -p 8080:80 my-nginx
```

> **Example Question:** What is the difference between `CMD` and `ENTRYPOINT` in a Dockerfile?

---

## **4. Docker Networking**
### **4.1 Networking Modes**
- **Bridge** (default) – Used for communication between containers on the same host.  
- **Host** – Shares the host’s network.  
- **None** – No networking.  
- **Overlay** – Used in **Swarm Mode**.  

#### **Networking Commands**
```sh
# List networks
docker network ls

# Create a network
docker network create my-network

# Run a container with a network
docker run -d --name my-container --network my-network nginx

# Inspect a network
docker network inspect my-network
```

> **Example Question:** What are the different types of Docker networks, and when would you use each?

---

## **5. Data Persistence in Docker**
### **5.1 Volumes vs. Bind Mounts**
- **Volumes** – Managed by Docker (`docker volume create`).  
- **Bind Mounts** – Directly maps a host folder.  

#### **Volume Commands**
```sh
# Create a volume
docker volume create my-volume

# Use a volume in a container
docker run -d -v my-volume:/app/data nginx

# List volumes
docker volume ls
```

> **Example Question:** What is the difference between volumes and bind mounts in Docker?

---

## **6. Docker Compose**
### **6.1 What is Docker Compose?**
- Used to define multi-container applications in **YAML**.  
- Simplifies container orchestration.  

#### **Example `docker-compose.yml`**
```yaml
version: '3'
services:
  web:
    image: nginx
    ports:
      - "8080:80"
  database:
    image: mysql
    environment:
      MYSQL_ROOT_PASSWORD: root
```
```sh
# Start the services
docker-compose up -d

# Stop the services
docker-compose down
```
> **Example Question:** How does Docker Compose help in multi-container deployments?

---

## **7. Docker Security**
### **7.1 Security Best Practices**
- **Use official images** from trusted registries.  
- **Run as a non-root user** inside containers.  
- **Scan images for vulnerabilities** using tools like **Trivy or Docker Scout**.  
- **Limit container privileges** (`--cap-drop ALL`).  

> **Example Question:** How would you ensure security in a Dockerized environment?

---

## **8. Docker Swarm (Basic Overview)**
- **Swarm Mode** – Docker’s built-in container orchestration tool.  
- **Managers & Workers** – Swarm architecture.  
- **Deploying services** using `docker service create`.  

> **Example Question:** How is Docker Swarm different from Kubernetes?

---

## **9. Debugging & Troubleshooting**
### **9.1 Common Issues**
- **Container not starting?** → Check logs (`docker logs container_id`).  
- **Network issues?** → Inspect network (`docker network inspect`).  
- **High resource usage?** → Monitor with `docker stats`.  
- **File permission errors?** → Check volumes (`docker inspect container_id`).  

#### **Useful Debugging Commands**
```sh
# View logs
docker logs my-container

# Inspect container details
docker inspect my-container

# Check resource usage
docker stats
```

> **Example Question:** How do you debug a failing container in production?

---

## **10. Real-World Scenarios**
### **Scenario-Based Questions**
- **How would you migrate a legacy application into Docker?**  
- **How do you ensure zero-downtime deployment using Docker?**  
- **How do you handle containerized applications running out of disk space?**  

---

## **Next Steps**
Would you like hands-on exercises or **real-world project ideas** to strengthen your Docker skills? 🚀
