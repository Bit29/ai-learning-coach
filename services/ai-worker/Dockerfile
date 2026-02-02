FROM python:3.11-slim
WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

# main.py가 uvicorn으로 띄우는 FastAPI 앱이면 아래처럼
# CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]

# 그냥 python 스크립트면
CMD ["python", "main.py"]
