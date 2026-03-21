# Images for Java applications, you can choose one of the following base images depending on your requirements and preferences. Each image has its own advantages and may be suitable for different use cases. Here are some popular options:
#adoptopenjdk/openjdk15:alpine-jre
#openjdk:17-alpine
#openjdk:17.0.1-jdk-slim
#openjdk:17.0.2-jdk
#eclipse-temurin:8-jre-alpine
#eclipse-temurin:17_35-jdk-alpine
#eclipse-temurin:11-jre-alpine
#eclipse-temurin:17-jre-alpine
#eclipse-temurin:17.0.8.1_1-jre-ubi9-minimal
#eclipse-temurin:17-jre-jammy
#eclipse-temurin:17.0.8.1_1-jre-focal
#eclipse-temurin:17.0.8.1_1-jre-alpine
#eclipse-temurin:21-jre-alpine
#amazoncorretto:17.0.0-alpine
#amazoncorretto:8u382-al2023
#

##### Dockerfile for java applications #####
## Build stage: Compile the Java application using Maven
FROM maven:3.8.3-openjdk-17 as build
WORKDIR ./src
COPY . .
RUN mvn install -DskipTests=true
#
### Runtime stage: Use a lightweight JRE image to run the compiled application
FROM eclipse-temurin:17.0.8.1_1-jre-ubi9-minimal 
## thay tương ứng các image đề xuất ở trên nếu không chạy

RUN unlink /etc/localtime;ln -s  /usr/share/zoneinfo/Asia/Ho_Chi_Minh /etc/localtime
COPY --from=build src/target/filename.jar /run/filename.jar

# Expose the port that your application will run on (if applicable)
EXPOSE 8888
# Set the Java options (you can adjust these based on your application's requirements)
ENV JAVA_OPTIONS="-Xmx2048m -Xms256m"
# Set the entry point to run your Java application
ENTRYPOINT java -jar $JAVA_OPTIONS /run/filename.jar