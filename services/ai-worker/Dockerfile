FROM python:3.11-slim
WORKDIR /app

# 필요한 패키지
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .
ENV PYTHONUNBUFFERED=1

# worker는 보통 "consumer loop" 실행
CMD ["python", "-m", "app.worker"]
