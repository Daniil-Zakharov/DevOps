# Use the OpenJDK 21 image
FROM ubuntu:latest

# Update the package list and install necessary dependencies
RUN apt-get update && \
    apt-get install -y wget git && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
RUN wget https://download.oracle.com/java/21/latest/jdk-21_linux-x64_bin.deb
RUN apt install ./jdk-21_linux-x64_bin.deb

# Cloning frontend repository
RUN git clone https://github.com/Daniil-Zakharov/mvc_frontend.git ./frontend

# Build your application using Gradle
RUN cd frontend && chmod +x /frontend/gradlew && /frontend/gradlew build "-Pvaadin.productionMode"

# Set the working directory
WORKDIR /app

# Copy your application code into the container
COPY . /app

# Specify the command to run your application
CMD ["java", "-jar", "/frontend/build/libs/Git-0.0.1-SNAPSHOT.jar"]
