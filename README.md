# RG ZAMAX API

API Flask do assistente RG ZAMAX. Guia o microempreendedor brasileiro pela configuração do registro do negócio dele na internet.

## Deploy no Render (gratuito)

### 1. Criar conta
- Acesse render.com
- Faça login com GitHub

### 2. Criar Web Service
- New → Web Service
- Conecte o repositório `rg-zamax-api`
- Configure:
  - **Name:** rg-zamax-api
  - **Runtime:** Python 3
  - **Build Command:** `pip install -r requirements.txt`
  - **Start Command:** `gunicorn --timeout 60 app:app`

### 3. Variáveis de ambiente
- **GEMINI_API_KEY** = sua chave do Google AI Studio

### 4. Deploy
- Clique em Deploy
- Aguarde 2-5 minutos

### 5. Uptime Robot
- Criar conta em uptimerobot.com
- New Monitor → HTTP(s)
- URL: `https://seu-app.onrender.com/health`
- Intervalo: 14 minutos

## Endpoints

- `GET /health` — status da API
- `POST /api/chat` — conversa com o assistente
- `POST /api/reset` — limpa a sessão

## Regras

- NUNCA armazena CPF, CNPJ ou senhas (LGPD)
- CORS restrito a zamaxia.com.br
- Modo offline se Gemini falhar