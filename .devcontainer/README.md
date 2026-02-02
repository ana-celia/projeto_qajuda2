# Dev Container - QAjuda

Ambiente de desenvolvimento containerizado com Python + Node.js + PostgreSQL.

## � Quick Start

### 1. Preparar Arquivo `.env`

```bash
# backend/compose/.env
POSTGRES_USER=postgres
POSTGRES_PASSWORD=sua_senha
POSTGRES_DB=qajuda_db
DEBUG=True
SECRET_KEY=sua-chave-secreta
```

### 2. Abrir em Dev Container

```
VS Code → Ctrl+Shift+P → "Dev Containers: Reopen in Container"
```

### 3. Instalar Dependências

```bash
# Terminal 1 - Backend
cd backend
pip install -r requirements.txt
python manage.py migrate

# Terminal 2 - Frontend
cd frontend/v2
npm install
```

### 4. Rodar Aplicação

```bash
# Terminal 1 - Backend
cd backend && python manage.py runserver 0.0.0.0:8000
# → http://localhost:8000

# Terminal 2 - Frontend
cd frontend/v2 && npm run dev
# → http://localhost:5173
```

## 📁 O que este setup faz

| Arquivo | Função |
|---------|--------|
| `devcontainer.json` | Configuração do VS Code para dev container |
| `docker-compose.override.yml` | Overrides para desenvolvimento |

**Reutiliza:**
- `backend/docker-compose.yml` - Orquestração original
- `backend/Dockerfile` - Imagem Python

## � Tecnologias

- **Python 3** + Django + PostgreSQL
- **Node.js 20** + React + Vite
- **VS Code** com extensões pré-configuradas

## 💻 Comandos Úteis

```bash
# Python
python manage.py runserver
python manage.py migrate
python manage.py shell
python manage.py test

# Node
npm install
npm run dev
npm run build
npm run lint

# Database
psql -h postgres -U postgres -d qajuda_db
```

## ❌ Troubleshooting

**P: "Port já em uso"**
```bash
lsof -i :8000 && kill -9 <PID>
```

**P: "pip não encontrado"**
```bash
source /opt/venv/bin/activate
pip install -r requirements.txt
```

**P: "PostgreSQL recusa conexão"**
```bash
docker-compose logs postgres
# Aguarde healthcheck ficar "UP"
```

**P: "npm ERR!"**
```bash
cd frontend/v2
rm -rf node_modules package-lock.json
npm install
```

## 📚 Referências

- [VS Code Dev Containers](https://code.visualstudio.com/docs/devcontainers/containers)
- [Docker Compose](https://docs.docker.com/compose/)

