FROM registry.redhat.io/ubi8/ubi:latest

WORKDIR /app

RUN dnf install -y java-21-openjdk-devel maven && \
    dnf clean all

COPY . .

RUN mvn clean package -DskipTests

EXPOSE 8080

CMD ["java", "-jar", "target/*.jar"]
