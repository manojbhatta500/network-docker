# Docker & Kubernetes: Netwroks and volumes

This project is part of my learning journey through the "Docker & Kubernetes: The Practical Guide [2025 Edition]" course. Below, I document the concepts and practices I have implemented while working on this project.

## Chapter 4: Docker Volumes and Networking

### Docker Volumes
I explored the different types of Docker volumes and practiced using them in this project:
- **Anonymous Volumes**: Used for temporary storage that is automatically managed by Docker.
- **Named Volumes**: Created and managed explicitly, allowing data persistence across container restarts.
- **Bind Mounts**: Used to map specific host directories to container directories for development purposes.

### Docker Networking
I learned how to inspect and manage Docker container networks:
- **Inspecting Containers**: Used `docker container inspect <container_name>` to view detailed information about containers, including their IP addresses.
- **Creating Docker Networks**: Created custom Docker networks using `docker network create <network_name>` to enable communication between containers.

### MongoDB Integration
To practice networking, I:
1. Created a new MongoDB container.
2. Added the MongoDB container to the same network as the server container.
3. Configured the server to communicate with MongoDB using the network.

This setup allowed the server to store and retrieve data from MongoDB seamlessly.

## How to Run This Project
1. Build the Docker image:
   ```bash
   docker build -t docker-complete .
   ```
2. Create a custom Docker network:
   ```bash
   docker network create sw-network
   ```
3. Run a MongoDB container and attach it to the network:
   ```bash
   docker run -d --name mongodb --network sw-network mongo
   ```
4. Run the server container and attach it to the same network:
   ```bash
   docker run -d --name server --network sw-network -p 3000:3000 docker-complete
   ```

## Features
- REST API for managing "favorites" (movies and characters).
- Integration with MongoDB for data persistence.
- Fetching data from external APIs using Axios.

## Technologies Used
- Node.js
- Express.js
- MongoDB
- Docker

## Future Plans
- Explore Kubernetes for container orchestration.
- Implement advanced Docker Compose configurations.

Feel free to clone this repository and experiment with the setup!