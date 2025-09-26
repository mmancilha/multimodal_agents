# 🤖 Agente Multimodal OpenAI

<p align="center">
  <strong>Desenvolvido com 💙 por Maycon Mancilha</strong>
  <br />
  <a href="https://github.com/mmancilha"><img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white" /></a>
  <a href="https://www.linkedin.com/in/mayconmancilha//"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" /></a>
</p>

> **🚀 Projeto de Especialização:** API REST multimodal desenvolvida durante aprimoramento profissional em **IA & Machine Learning** pela IT Valley School.

### 👨‍💻 **Sobre o Desenvolvedor**
🔗 **[Visite meu GitHub completo →](https://github.com/mmancilha)** para ver mais projetos, tecnologias e experiência profissional!

## 📋 Sobre o Projeto

API REST robusta que integra múltiplas capacidades de IA da OpenAI em uma interface unificada, incluindo processamento de texto, áudio e visão computacional.

### ✨ Funcionalidades

- **💬 Chat:** Conversação com GPT-4o e moderação de conteúdo
- **🎵 Áudio:** Text-to-Speech (TTS) e transcrição com Whisper
- **🖼️ Visão:** Geração de imagens com DALL-E 3
- **📊 Business:** Endpoints para gestão de clientes, funcionários e vendas

### 🛠️ Stack Técnica

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi" />
  <img src="https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white" />
</p>

## 🚀 Instalação e Uso

### 1. Configuração

```bash
# Clone o repositório
git clone https://github.com/mmancilha/multimodal_agents.git
cd "Agente Multimodal OpenAI"

# Instale as dependências
pip install -r requirements.txt

# Configure as variáveis de ambiente
cp .env.example .env
# Edite o .env com sua OPENAI_API_KEY
```

### 2. Execução

```bash
# Inicie o servidor
uvicorn main:app --reload --host 0.0.0.0 --port 8000

# Acesse a documentação interativa
# http://localhost:8000/docs
```

## 📡 Endpoints Principais

| Endpoint | Método | Descrição |
|----------|--------|-----------|
| `/api/text/chat` | POST | Chat com GPT-4o |
| `/api/text/moderations` | POST | Moderação de conteúdo |
| `/api/audio/tts` | POST | Conversão texto-para-fala |
| `/api/audio/whisper` | POST | Transcrição de áudio |
| `/api/vision/imggeneration` | POST | Geração de imagens |

## ⚙️ Configuração

### Variáveis de Ambiente (.env)

```env
OPENAI_API_KEY=sua_chave_openai_aqui
CORS_ORIGINS=http://localhost:8000,http://127.0.0.1:8000
```

## 🔧 Solução de Problemas

### Erros Comuns

- **401 Unauthorized:** Verifique sua `OPENAI_API_KEY`
- **CORS Error:** Configure `CORS_ORIGINS` no `.env`
- **File too large:** Limite de 25MB para áudio (Whisper)
- **Timeout:** Geração de imagens pode levar até 30s

### Logs e Debug

```bash
# Logs detalhados
uvicorn main:app --log-level debug

# Status da OpenAI API
curl https://status.openai.com/api/v2/status.json
```
## 📄 Licença

Este projeto está sob a licença MIT.

---