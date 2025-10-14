# Docker

**STEP 1 — Clone the Application**
 git clone https://github.com/spring-projects/spring-petclinic.git
 Downloads the Spring PetClinic repository from GitHub. 
 
 **STEP 2 — Navigate into the Project**
 cd spring-petclinic
 Switches your working directory to the project folder. 
 
 **STEP 3 — Build the Project with Maven
 Wrapper**
 ./mvnw clean package -DskipTests
 1. Wrapper downloads Maven if not installed.
 2. Cleans previous build artifacts.
 3. Compiles and packages Java source into JAR.
 4. Skips test execution for faster builds.
 Result: target/spring-petclinic-3.5.0-SNAPSHOT.jar 
 <img width="1920" height="1080" alt="Screenshot (815)" src="https://github.com/user-attachments/assets/519908c2-3f88-456e-8f79-89281e694fc2" />



 
 **STEP 4 — Verify the Build**
 Output
 dir target
 Check that the JAR file was created successfully. 
 <img width="1920" height="1080" alt="Screenshot (850)" src="https://github.com/user-attachments/assets/a765ea36-c843-47a6-a189-6c60f69ad437" />




 
**STEP 5 — Create Dockerfile**
 FROM openjdk:17-jdk-slim
 WORKDIR /app
 COPY target/*.jar app.jar
 EXPOSE 8080
 ENTRYPOINT ["java", "-jar", "app.jar"]
 Explanation:
 • FROM: Base image with Java 17.
 • WORKDIR: Sets working directory to /app.
 • COPY: Copies the built JAR into container.
 • EXPOSE: Documents port 8080.
 • ENTRYPOINT: Runs Java app inside container. 
 <img width="1920" height="1080" alt="Screenshot (847)" src="https://github.com/user-attachments/assets/4a7e8f3c-8cc7-41f8-b538-9aa54ed7c5fd" />



 
**STEP 6 — Build Docker Image**
 docker build -t spring-petclinic .
 Builds Docker image from Dockerfile. 
 <img width="1920" height="1080" alt="Screenshot (846)" src="https://github.com/user-attachments/assets/0cd00026-d763-4300-8a11-b60ecbc7c0be" />



 
 **STEP 7 — Run Container**
 docker run -d -p 8080:8080 --name petclinic spring-petclinic
 Runs app in container accessible at http://localhost:8080. 
 <img width="1920" height="1080" alt="Screenshot (849)" src="https://github.com/user-attachments/assets/38c06890-bbb2-48c2-a45e-aac812130346" />



 
 **STEP 8 — Useful Docker Commands**
 docker ps
 docker logs -f petclinic
 docker stop petclinic
 docker start petclinic
 docker rm petclinic
 docker images
 docker rmi spring-petclinic STEP 9 — Internal Process Summary
 1. Maven builds app into runnable JAR.
 2. Dockerfile defines how to package it into an image.
 3. Docker build creates immutable image layers.
 4. Docker run executes the container and maps ports.
 5. Application runs isolated, portable, and reproducible
