FROM eclipse-temurin:21-jdk AS builder
WORKDIR /app

# 전체 복사 먼저
COPY . .

# ✅ 여기서 실행권한 + CRLF 제거 (COPY 이후에 해야 덮어쓰기 안 당함)
RUN chmod +x gradlew \
 && sed -i 's/\r$//' gradlew

# ✅ 권한 이슈 방지로 bash로 실행(temurin에는 bash 있음)
RUN bash ./gradlew clean bootJar -x test

FROM eclipse-temurin:21-jre
WORKDIR /app
COPY --from=builder /app/build/libs/*.jar app.jar

EXPOSE 8080
ENTRYPOINT ["java","-jar","/app/app.jar"]
