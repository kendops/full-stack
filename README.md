**README.md** file for your** ** **full-stack application using Docker on RHEL 8** . This guide provides installation instructions, usage, and troubleshooting.

---

### **📘 Full-Stack Application (React + Spring Boot + MySQL)**

A** ****containerized full-stack application** using:

* **Frontend** : Node.js 22, React 19, Next.js, Gatsby, Material UI, Vite
* **Backend** : Java 21, Spring Boot 3.4.1, Maven 3.9.5, MySQL Connector
* **Database** : MySQL 8.0
* **Containerization** : RHEL 8 UBI + Docker + Docker Compose

---

## **📂 Project Structure**

fullstack-app
  ├── backend/             # Spring Boot backend
  │   ├── src/
  │   ├── pom.xml
  │   ├── Dockerfile
  │   └── .env
  ├── frontend/            # React / Next.js / Gatsby frontend
  │   ├── src/
  │   ├── package.json
  │   ├── yarn.lock
  │   ├── Dockerfile
  │   └── .env
  ├── docker-compose.yml   # Docker Compose for full-stack setup
  ├── .dockerignore
  ├── README.md

---

## **Prerequisites**

Ensure you have the following installed on your system:

1. **Docker** (>= 20.10)
   sudo dnf install -y docker
2. **Docker Compose** (>= 1.29)
   sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$$(uname -m)" -o /usr/local/bin/docker-compose
   sudo chmod +x /usr/local/bin/docker-compose
3. **Enable & Start Docker Service**
   sudo systemctl** **enable** **--now docker
   sudo systemctl** **enable** **--now docker

---

## **How to Build & Run**

### **1. Build Docker Containers**

docker-compose build

### **2. Run Full-Stack Application**

docker-compose up -d

### **3. Verify Running Containers**

docker ps

### **4. Access the Application**

* **Frontend (React/Next.js/Gatsby UI):**
  👉** **`http://localhost:3000`
* **Backend (Spring Boot API):**
  👉** **`http://localhost:8080`
* **Database (MySQL):**
  Connect using** **`localhost:3306` with** ** **backenduser/backendpass** .

---

## **Configuration**

### **Backend Environment Variables**

Located in** ** **`backend/.env`** :

PRING_DATASOURCE_URL=jdbc:mysql://db:3306/backenddb
SPRING_DATASOURCE_USERNAME=backenduser
SPRING_DATASOURCE_PASSWORD=backendpass

### **Frontend Environment Variables**

Located in** ** **`frontend/.env`** :

REACT_APP_API_BASE_URL=http://localhost:8080

---

## **🛠️ Troubleshooting**

### **1. Containers Not Starting?**

Check logs:

docker-compose logs -f

### **2. Check Running Containers**

docker ps -a

### **3. Restart Services**

docker-compose restart

### **4. Stop and Remove Containers**

docker-compose down

### **5. Remove All Docker Images & Containers**

docker system prune -a

## **✅ Summary**

* **Frontend:** Installs** ****Node.js 22** and required** ****React, Next.js, Gatsby, Material UI, axios** libraries.
* **Backend:** Installs** ** **Java 22, Maven 3.9.5, MySQL Connector** , and** ** **Spring Boot dependencies** .
* **Docker Compose:** Manages frontend, backend, and database in** ** **one command** .
* **Fully Automated Deployment** with Docker.

Now your full-stack application is containerized and ready to deploy!

### Sample

https://github.com/NerminKarapandzic/spring-boot-nextjs-starter-kit.git



### Status (WIP)

[](https://github.com/ahstn/docker-spring-react#status-wip)

* API (Java - Spring Boot)
  * [X] CRUD Endpoints
  * [ ] Tests
  * [X] Dockerised
  * [ ] Postgres Integration (Uses in-memory db for now)
* Frontend (Javascript - React Redux)
  * [ ] CRUD Endpoints
  * [ ] Tests
  * [ ] Styling
  * [X] Dockerised
* Database (PostgreSQL)
  * [X] Dockerised (For quick development)
  * [ ] Updated employees schema
* Docker Compose
  * [ ] All services running and tested
