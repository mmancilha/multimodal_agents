# 🤖 Agente Multimodal OpenAI

> **📚 Projeto Acadêmico:** Este repositório faz parte da jornada de especialização em **Inteligência Artificial & Machine Learning** pela IT Valley School. Para ver todos os projetos relacionados e a documentação completa da especialização, visite o [repositório principal](https://github.com/mmancilha/it-valley-school).

## 📋 Visão Geral do Projeto

### Objetivos e Metas Principais

Este projeto implementa um **Agente Multimodal OpenAI** que oferece uma API REST completa para interação com diferentes modalidades de IA, incluindo texto, áudio e visão computacional. O sistema foi desenvolvido como parte da especialização em **Inteligência Artificial & Machine Learning** pela IT Valley School, demonstrando a aplicação prática de tecnologias de IA em um ambiente de produção.

**Principais Objetivos:**
- 🎯 Fornecer uma interface unificada para múltiplas capacidades de IA
- 🔄 Demonstrar integração eficiente com APIs da OpenAI
- 🏗️ Implementar arquitetura modular e escalável
- 📊 Servir como base para desenvolvimento de aplicações multimodais

### Escopo do Projeto

**✅ O que está incluído:**
- API REST para processamento de texto (chat e moderação)
- Geração de imagens com DALL-E 3
- Conversão texto-para-fala (TTS)
- Transcrição de áudio com Whisper
- Sistema de roteamento modular
- Configuração CORS para desenvolvimento web
- Endpoints para gestão de clientes, funcionários e vendas

**❌ O que não está incluído:**
- Interface de usuário (frontend)
- Banco de dados persistente
- Sistema de autenticação/autorização
- Cache de respostas
- Monitoramento e logs avançados

### Público-Alvo e Personas

**👨‍💻 Desenvolvedores:**
- Profissionais buscando integrar IA em suas aplicações
- Estudantes de IA/ML que querem exemplos práticos
- Arquitetos de software interessados em APIs multimodais

**🏢 Empresas:**
- Startups desenvolvendo produtos com IA
- Empresas buscando automatizar processos com IA
- Organizações implementando chatbots e assistentes virtuais

## 🏗️ Arquitetura do Sistema

### Componentes Principais e suas Funções

#### 🎯 **Core Application (main.py)**
- **Função:** Ponto de entrada principal da aplicação
- **Responsabilidades:**
  - Configuração do servidor FastAPI
  - Gerenciamento de middleware CORS
  - Registro de rotas modulares
  - Carregamento de variáveis de ambiente

#### 🗣️ **Text Router (textRouter.py)**
- **Função:** Processamento de texto com IA
- **Endpoints:**
  - `POST /api/text/chat` - Chat conversacional com GPT-4o
  - `POST /api/text/moderations` - Moderação de conteúdo

#### 🎵 **Audio Router (audioRouter.py)**
- **Função:** Processamento de áudio bidirecional
- **Endpoints:**
  - `POST /api/audio/tts` - Conversão texto-para-fala
  - `POST /api/audio/whisper` - Transcrição de áudio

#### 👁️ **Vision Router (visionRouter.py)**
- **Função:** Geração de imagens
- **Endpoints:**
  - `POST /api/vision/imggeneration` - Geração de imagens com DALL-E 3

#### 📊 **Business Routers**
- **customerRouter.py:** Gestão de clientes
- **employeeRouter.py:** Gestão de funcionários  
- **salesRouter.py:** Gestão de vendas

### Tecnologias Utilizadas

| Categoria | Tecnologia | Versão | Propósito |
|-----------|------------|--------|-----------|
| **Framework Web** | FastAPI | 0.115.4 | API REST moderna e rápida |
| **IA/ML** | OpenAI | 1.54.0 | Integração com modelos de IA |
| **Servidor ASGI** | Uvicorn | 0.32.0 | Servidor de aplicação assíncrono |
| **Configuração** | python-dotenv | 1.0.1 | Gerenciamento de variáveis de ambiente |
| **HTTP Client** | httpx | 0.27.2 | Cliente HTTP assíncrono |
| **Validação** | Pydantic | 2.9.2 | Validação de dados |

## 🔄 Fluxos de Trabalho

### Processos-Chave do Sistema

#### 1. **Fluxo de Chat Conversacional**
```
Cliente → POST /api/text/chat → GPT-4o → Resposta Processada → Cliente
```

#### 2. **Fluxo de Geração de Imagem**
```
Cliente → POST /api/vision/imggeneration → DALL-E 3 → URL da Imagem → Cliente
```

#### 3. **Fluxo de Transcrição de Áudio**
```
Cliente → Upload de Arquivo → POST /api/audio/whisper → Whisper → Texto → Cliente
```

### Integrações com Outros Sistemas

- **OpenAI API:** Integração principal para todos os serviços de IA
- **CORS:** Configurado para permitir requisições de diferentes origens
- **Streaming:** Suporte para streaming de áudio em tempo real

## ⚙️ Configuração do Ambiente

#### Arquivo `.env`
```env
OPENAI_API_KEY=sua_chave_openai_aqui
CORS_ORIGINS=http://127.0.0.1:8000,https://127.0.0.1:8000,http://localhost:8000
```

## 🚀 Instalação e Implantação

### Passo a Passo para Configuração Local

#### 1. **Clone do Repositório**
```bash
git clone https://github.com/mmancilha/it-valley-school.git
cd "Agente Multimodal OpenAI"
```

#### 2. **Criação do Ambiente Virtual**
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# macOS/Linux
python3 -m venv venv
source venv/bin/activate
```

#### 3. **Instalação das Dependências**
```bash
pip install -r requirements.txt
```

#### 4. **Configuração das Variáveis de Ambiente**
```bash
# Crie o arquivo .env na raiz do projeto
echo "OPENAI_API_KEY=sua_chave_aqui" > .env
echo "CORS_ORIGINS=http://localhost:8000" >> .env
```

#### 5. **Execução da Aplicação**
```bash
uvicorn main:app --reload --host 0.0.0.0 --port 8000
```

### Instruções para Deploy em Produção

#### **Deploy com Docker**
```dockerfile
FROM python:3.11-slim

WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .
EXPOSE 8000

CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
```

#### **Deploy na Nuvem (Heroku/Railway/Render)**
```bash
# Procfile para Heroku
web: uvicorn main:app --host 0.0.0.0 --port $PORT
```

### Considerações sobre Ambientes Diferentes

- **Desenvolvimento:** Use `--reload` para hot-reload
- **Produção:** Remova `--reload` e configure logs apropriados
- **Staging:** Use variáveis de ambiente específicas para testes

## 📖 Guia de Utilização

### Funcionalidades Principais com Exemplos

#### 🗣️ **Chat Conversacional**
```bash
curl -X POST "http://localhost:8000/api/text/chat" \
  -H "Content-Type: application/json" \
  -d '{"message": "Olá, como você pode me ajudar?"}'
```

**Resposta:**
```json
{
  "response": "Olá! Sou um assistente de IA e posso ajudá-lo com diversas tarefas..."
}
```

#### 🎨 **Geração de Imagens**
```bash
curl -X POST "http://localhost:8000/api/vision/imggeneration" \
  -H "Content-Type: application/json" \
  -d '{"prompt_image": "Um gato astronauta no espaço, estilo cartoon"}'
```

**Resposta:**
```json
{
  "url": "https://oaidalleapiprodscus.blob.core.windows.net/private/..."
}
```

#### 🎵 **Conversão Texto-para-Fala**
```bash
curl -X POST "http://localhost:8000/api/audio/tts" \
  -H "Content-Type: application/json" \
  -d '{"text": "Olá, este é um teste de conversão de texto para fala"}' \
  --output audio.mp3
```

#### 🎤 **Transcrição de Áudio**
```bash
curl -X POST "http://localhost:8000/api/audio/whisper" \
  -F "file_upload=@audio.mp3"
```

### Casos de Uso Comuns

#### **1. Chatbot para Atendimento ao Cliente**
```python
import requests

def chat_with_ai(message):
    response = requests.post(
        "http://localhost:8000/api/text/chat",
        json={"message": message}
    )
    return response.json()

# Exemplo de uso
resposta = chat_with_ai("Como posso cancelar meu pedido?")
print(resposta)
```

#### **2. Geração de Conteúdo Visual**
```python
def gerar_imagem(prompt):
    response = requests.post(
        "http://localhost:8000/api/vision/imggeneration",
        json={"prompt_image": prompt}
    )
    return response.json()["url"]

# Exemplo de uso
url_imagem = gerar_imagem("Logo moderno para empresa de tecnologia")
```

#### **3. Transcrição de Reuniões**
```python
def transcrever_audio(arquivo_audio):
    with open(arquivo_audio, 'rb') as f:
        response = requests.post(
            "http://localhost:8000/api/audio/whisper",
            files={"file_upload": f}
        )
    return response.text

# Exemplo de uso
transcricao = transcrever_audio("reuniao.mp3")
```

### Documentação Interativa da API

Após iniciar o servidor, acesse:

- **Swagger UI:** http://localhost:8000/docs
- **ReDoc:** http://localhost:8000/redoc

## 🔧 Solução de Problemas

### FAQ - Perguntas Frequentes

#### **Q: Como obter uma chave da API OpenAI?**
**A:** Acesse https://platform.openai.com/api-keys, crie uma conta e gere uma nova chave de API.

#### **Q: O servidor não inicia, erro "ModuleNotFoundError"**
**A:** Certifique-se de que o ambiente virtual está ativado e as dependências foram instaladas:
```bash
pip install -r requirements.txt
```

#### **Q: Erro "Import string must be in format '<module>:<attribute>'"**
**A:** Use o comando correto: `uvicorn main:app` em vez de apenas `uvicorn main`

#### **Q: Como configurar CORS para meu frontend?**
**A:** Adicione a URL do seu frontend no arquivo `.env`:
```env
CORS_ORIGINS=http://localhost:3000,http://localhost:8000
```

### Erros Comuns e Como Resolvê-los

#### **1. Erro 401 - Unauthorized**
```json
{"error": "Invalid API key"}
```
**Solução:** Verifique se a chave da OpenAI está correta no arquivo `.env`

#### **2. Erro 429 - Rate Limit**
```json
{"error": "Rate limit exceeded"}
```
**Solução:** Aguarde alguns minutos ou upgrade seu plano da OpenAI

#### **3. Erro de Upload de Arquivo**
```json
{"error": "File too large"}
```
**Solução:** Reduza o tamanho do arquivo de áudio (máximo 25MB para Whisper)

#### **4. Timeout na Geração de Imagem**
**Solução:** A geração pode demorar até 30 segundos, aguarde ou implemente timeout maior

### Logs e Debugging

#### **Ativar Logs Detalhados**
```bash
uvicorn main:app --log-level debug
```

#### **Verificar Status da API OpenAI**
```bash
curl https://status.openai.com/api/v2/status.json
```

### Contatos para Suporte Adicional

- **GitHub Issues:** https://github.com/mmancilha/it-valley-school/issues
- **Documentação OpenAI:** https://platform.openai.com/docs
- **FastAPI Docs:** https://fastapi.tiangolo.com/

---

## 📊 Métricas e Performance

### Benchmarks de Performance

| Endpoint | Tempo Médio | Throughput |
|----------|-------------|------------|
| `/api/text/chat` | 2-5s | 10 req/min |
| `/api/vision/imggeneration` | 10-30s | 2 req/min |
| `/api/audio/tts` | 3-8s | 5 req/min |
| `/api/audio/whisper` | 5-15s | 3 req/min |

### Limitações Conhecidas

- **Rate Limits:** Dependem do plano da OpenAI
- **Tamanho de Arquivo:** Máximo 25MB para áudio
- **Concurrent Requests:** Limitado pela OpenAI API
- **Timeout:** 30s para geração de imagens

---

## 🔮 Roadmap Futuro

### Próximas Funcionalidades
- [ ] Interface web responsiva
- [ ] Sistema de autenticação JWT
- [ ] Cache Redis para respostas
- [ ] Suporte a múltiplos modelos
- [ ] Análise de sentimentos
- [ ] Integração com bancos de dados
- [ ] Monitoramento com Prometheus
- [ ] Deploy automatizado com CI/CD

### Contribuições

Contribuições são bem-vindas! Por favor:
1. Fork o repositório
2. Crie uma branch para sua feature
3. Commit suas mudanças
4. Abra um Pull Request

---

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.

---

**Desenvolvido por:** Maycon Mancilha <mcreference link="https://github.com/mmancilha/it-valley-school" index="0">0</mcreference>  
**Especialização:** IA & Machine Learning - IT Valley School  
**Versão:** 1.0.0  
**Última Atualização:** Janeiro 2025