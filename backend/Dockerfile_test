# Use Red Hat UBI 8 minimal image
FROM registry.redhat.io/ubi8/ubi:latest

# Set working directory
WORKDIR /app

# Install Java 21, Maven, and required dependencies
RUN dnf install -y java-21-openjdk-devel maven && \
    dnf clean all

# Set Java environment variables
ENV JAVA_HOME=/usr/lib/jvm/java-21-openjdk
ENV PATH=$JAVA_HOME/bin:$PATH

# Copy Maven configuration
COPY pom.xml ./

# Install Spring Boot & dependencies
RUN mvn dependency:go-offline

# Copy backend source code
COPY src/ ./src/

# Install MySQL Connector & other Spring Boot dependencies
RUN mvn install:install-file -DgroupId=mysql \
    -DartifactId=mysql-connector-java -Dversion=8.0.33 \
    -Dpackaging=jar -Dfile=libs/mysql-connector-java-8.0.33.jar

# Build Spring Boot JAR
RUN mvn clean package -DskipTests

# Expose backend port
EXPOSE 8080

# Start the backend
CMD ["java", "-jar", "target/*.jar"]
