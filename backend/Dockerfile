#FROM python:alpine
#EXPOSE 8000
#WORKDIR /app/backend
#COPY . .
#RUN pip3 install -r backend/requirements.txt

# Alterado de alpine para slim para compatibilidade com VS Code
FROM python:3.11-slim

ENV PYTHONUNBUFFERED 1
EXPOSE 8000
WORKDIR /app/backend

# Instala dependências do sistema necessárias para compilar pacotes Python (se necessário)
RUN apt-get update && apt-get install -y \
    gcc \
    python3-dev \
    libpq-dev \
    git \
    && rm -rf /var/lib/apt/lists/*

COPY . .
# Ajuste o caminho se o requirements estiver na raiz ou dentro de backend/
RUN pip3 install --no-cache-dir -r backend/requirements.txt