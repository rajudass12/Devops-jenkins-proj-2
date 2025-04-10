# Use an official Maven runtime as a parent image
FROM maven:3.8.6-openjdk-11

# Set the working directory
WORKDIR /usr/src/app

# Copy the local code to the container
COPY . .

# Build the application
RUN mvn clean install

# Define the command to run the application
CMD ["mvn", "spring-boot:run"]
