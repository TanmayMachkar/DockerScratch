# Stage 1 - Build the JAR (Java Application Runtime)
FROM maven:3.8.3-openjdk-17 AS builder

WORKDIR /app

COPY . .

# Run the JAR file
RUN mvn clean install -DskipTests=true

# Stage 2 - Execute JAR file from the above stage
FROM openjdk:17-alpine

WORKDIR /app

COPY --from=builder /app/target/*.jar /app/expenseapp.jar

CMD ["java", "-jar", "expenseapp.jar"]
