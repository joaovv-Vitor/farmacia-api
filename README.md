# 💊 SiHealth -- API de Gestão Farmacêutica

API RESTful desenvolvida para o gerenciamento de estoque de farmácias,
especialmente para UBS/Unidades de Saúde, permitindo controlar
medicamentos, lotes, validades e toda a movimentação de entrada e saída.

A arquitetura segue os princípios da Clean Architecture, garantindo
desacoplamento entre regras de negócio, persistência e camada de API.

## 🚀 Tecnologias Utilizadas

-   Python 3.10+
-   FastAPI
-   SQLAlchemy
-   PostgreSQL
-   Pydantic v2
-   Psycopg 3
-   Passlib (bcrypt)

## ⚙️ Funcionalidades

### Módulo Medicamentos

-   Cadastro, listagem, leitura e edição
-   Associação com lotes

### Lotes e Validade

-   Criação e controle de lotes
-   Impede criação de lotes vencidos
-   Indica quantidade total disponível

### Movimentação de Estoque

-   Entrada: incrementa quantidade disponível no lote
-   Saída: baixa estoque para paciente
-   Valida ausência de estoque

### Administração

-   Cadastro de usuários (farmacêuticos)
-   Cadastro de pacientes com validação de CNS
-   Senhas armazenadas com hashing seguro

## 🛠️ Como Rodar o Projeto

### 1. Pré-requisitos

-   Python 3.12+
-   PostgreSQL
-   Git

### 2. Clonar e Configurar o Ambiente

    git clone https://github.com/seu-usuario/sihealth-api.git
    cd sihealth-api

    python -m venv venv
    source venv/bin/activate  # Linux/Mac
    # .\venv\Scripts\activate  # Windows

    pip install -r requirements.txt

### 3. Configurar o Banco de Dados (.env)

Crie um arquivo `.env` na raiz:

    DATABASE_URL=postgresql+psycopg://casaos:casaos@100.72.228.40:5432/SiHealth
    APP_TITLE=SiHealth API
    API_V1_STR=/api/v1

### 4. Executar a API

    uvicorn main:app --reload

Acesse: http://127.0.0.1:8000

## 📚 Documentação da API

Swagger UI: http://127.0.0.1:8000/docs\
ReDoc: http://127.0.0.1:8000/redoc

## 📂 Estrutura do Projeto

    sihealth-api/
    ├── app/
    │   ├── api/
    │   ├── core/
    │   ├── db/
    │   ├── models/
    │   ├── schemas/
    │   └── services/
    ├── main.py
    ├── requirements.txt
    └── .env

## 🧪 Fluxo de Teste Sugerido

1.  POST /api/v1/admin/usuarios
2.  POST /api/v1/admin/pacientes
3.  POST /api/v1/medicamentos
4.  POST /api/v1/lotes
5.  POST /api/v1/movimentacao/entrada
6.  POST /api/v1/movimentacao/saida
