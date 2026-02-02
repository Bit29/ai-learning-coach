FROM eclipse-temurin:21-jre
WORKDIR /app
COPY build/libs/*.jar /app/
RUN ls -al /app && \
    rm -f /app/*-plain.jar && \
    mv /app/*.jar /app/app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","/app/app.jar"]
