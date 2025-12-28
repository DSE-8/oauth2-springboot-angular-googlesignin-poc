# ===============================
#   Etapa 1 – Build con Maven
# ===============================
FROM maven:3.9.6-eclipse-temurin-17 AS build

WORKDIR /app

# Copiar todo el repo
COPY . .

# Construir solo el módulo authorization-server
RUN mvn -pl authorization-server -am clean package -DskipTests


# ===============================
#   Etapa 2 – Runtime con JDK 17
# ===============================
FROM eclipse-temurin:17-jdk

WORKDIR /app

# Copiar el JAR resultante
COPY --from=build /app/authorization-server/target/*.jar app.jar

EXPOSE 8080

CMD ["java", "-jar", "app.jar"]
