# ---------- build stage ----------
FROM eclipse-temurin:21-jdk AS builder
WORKDIR /app

COPY gradlew .
COPY gradle gradle
COPY build.gradle settings.gradle ./
RUN chmod +x gradlew

# 소스 복사
COPY . .

# jar 생성
RUN ./gradlew clean bootJar -x test

# ---------- run stage ----------
FROM eclipse-temurin:21-jre
WORKDIR /app

# ✅ 여기 경로가 핵심: /app/build/libs
COPY --from=builder /app/build/libs/*.jar app.jar

EXPOSE 8080
ENTRYPOINT ["java","-jar","/app/app.jar"]
