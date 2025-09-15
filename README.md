<div align="center">
  <img width="420" height="634" alt="blackmirror(2)" src="https://github.com/user-attachments/assets/1a0b4f11-0b7d-4f2b-94ca-b0f5865fc347" />
</div>

---

# 🛡️🔍 Sistema de Modelagem de Ameaças

![Python](https://img.shields.io/badge/python-v3.8+-blue.svg)
![License](https://img.shields.io/badge/license-MIT-blue.svg)

---

## 📋 - Descrição 

Uma aplicação desenvolvida com FastAPI e Azure OpenAI para geração automática de modelos de ameaças baseados na metodologia STRIDE.
O sistema recebe informações da aplicação (tipo, autenticação, acesso à internet, dados sensíveis e descrição), além de um arquivo opcional de imagem, e gera um relatório em formato JSON estruturado com cenários de ameaça e sugestões de melhoria.

---

## 🎯 - Sobre o Projeto de modelagem de ameaças

Este projeto implementa um serviço de análise de riscos e ameaças cibernéticas que combina FastAPI, integração com LLMs (Azure OpenAI) e boas práticas de cibersegurança.

1- Coleta de Dados da Aplicação
  * O usuário envia dados via formulário (tipo de aplicação, métodos de autenticação, presença de dados sensíveis, etc.).
  * Opcionalmente, é possível anexar uma imagem para complementar o contexto.

2- Construção de Prompt Inteligente
  * As informações recebidas são estruturadas em um prompt detalhado.
  * O prompt orienta o modelo a aplicar a metodologia STRIDE, cobrindo as categorias:
    * Spoofing (Falsificação de Identidade)
    * Tampering (Violação de Integridade)
    * Repudiation (Repúdio)
    * Information Disclosure (Divulgação de Informações)
    * Denial of Service (Negação de Serviço)
    * Elevation of Privilege (Elevação de Privilégio)

3- Geração Automática de Modelo de Ameaças
  * O modelo de IA retorna um JSON com:
    * threat_model → lista de ameaças categorizadas com cenário e impacto.
    * improvement_suggestions → lacunas de informação que, se preenchidas, permitiriam uma análise mais completa.

4- API REST
  * O endpoint /analisar_ameacas expõe esse fluxo como um serviço REST.
  * A resposta é entregue em JSON pronto para integração com outras ferramentas de segurança ou dashboards.

---

## 🚀 Funcionalidades

  * ✅ Upload de Arquivos: recebe imagem opcional para complementar o contexto da análise.
  * ✅ Formulário de Entrada: coleta tipo da aplicação, autenticação, acesso à internet, dados sensíveis e descrição detalhada.
  * ✅ Criação de Prompt Inteligente: estrutura as informações no formato da metodologia STRIDE.
  * ✅ Análise Automática de Ameaças: utiliza modelo de linguagem (Azure OpenAI) para gerar cenários de risco em JSON estruturado.
  * ✅ Classificação STRIDE: organiza as ameaças nas categorias Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service e Elevation of Privilege.
  * ✅ Sugestões de Melhoria: identifica lacunas nas informações fornecidas e sugere quais dados extras poderiam refinar a análise.
  * ✅ API REST: endpoint /analisar_ameacas disponível via FastAPI para integração com outros sistemas.

---

## 📁 Instrução de Uso Google Collab

1- Preparar Ambiente
  * Subir o arquivo do código .py para o Colab.
  * Criar e configurar um arquivo .env com as chaves:
    * AZURE_OPENAI_API_KEY
    * AZURE_OPENAI_ENDPOINT
    * AZURE_OPENAI_API_VERSION
    * AZURE_OPENAI_DEPLOYMENT_NAME

2- Instalar Dependências

3- Rodar a API no Colab

4- Testar Endpoint
  * Usar um cliente como curl, Postman ou requests no Python para enviar um POST para:
  * Preencher os campos obrigatórios do formulário e enviar opcionalmente uma imagem.

5- Receber Resultado
  * O retorno será um JSON estruturado com:
    * threat_model (lista de ameaças categorizadas)
    * improvement_suggestions (sugestões de informações adicionais)

---

## 🛠️ Tecnologias Utilizadas

  * Python 3 – linguagem principal do projeto.
  * FastAPI – framework para construção de APIs modernas.
  * Uvicorn – servidor ASGI rápido para executar a aplicação.
  * dotenv – para carregar variáveis de ambiente de forma segura.
  * Azure OpenAI – modelo de linguagem para geração automática de cenários STRIDE.
  * base64 & tempfile – manipulação de imagens e arquivos temporários.
  * CORS Middleware – permite integração com aplicações externas.

---

## 📁 Estrutura do Projeto

```

projeto
├── app_threats_face_recognition.py        # Script principal com a API FastAPI
│   ├── criar_prompt_modelo_ameacas_face() # Monta prompt no formato STRIDE com descrição e regras de saída JSON
│   ├── chamar_modelo_openai()             # Função auxiliar para enviar requisição ao Azure OpenAI
│   ├── analisar_ameacas()                 # Endpoint POST /analisar_ameacas para processar entrada do usuário
│   │                                      # - Recebe formulário (tipo aplicação, autenticação, etc.)
│   │                                      # - Opcional: recebe imagem, converte para base64 e inclui no prompt
│   │                                      # - Envia prompt ao modelo e retorna resposta JSON
│   └── Configuração FastAPI               # Inicialização da API, middleware CORS e carregamento das variáveis .env
│
├── .env                                   # Arquivo de variáveis de ambiente (chaves Azure OpenAI)
│
└── requirements.txt                       # Dependências principais: fastapi, uvicorn, python-dotenv, openai

```

---

## 📊 Aplicações em Cibersegurança

* Identificação automática de possíveis ameaças em novos sistemas e aplicações.
* Suporte à fase de arquitetura de software segura, auxiliando desenvolvedores a prever riscos antes da implementação.
* Análise de fluxos de autenticação e dados sensíveis sob a ótica das categorias STRIDE.
* Geração de relatórios padronizados em JSON estruturado, prontos para integração com dashboards de segurança.
* Auxílio em auditorias de conformidade (LGPD, GDPR, ISO 27001, etc.).
* Uso em testes de segurança de aplicações (Threat Modeling integrado ao DevSecOps).
* Possibilidade de extensão para incluir imagens ou diagramas arquiteturais como contexto adicional.

---

## 🤝 Patrocinadores ou Afins

- [DIO](https://www.dio.me/): plataforma de cursos e bootcamps online.
- [Baires Dev](https://www.bairesdev.com/): A BairesDev é uma empresa multinacional americana de outsourcing de TI e desenvolvimento de software
- [Microsoft Azure OpenAI](https://azure.microsoft.com/pt-br/products/ai-foundry/models/openai): Serviço de IA utilizado para geração automática de cenários STRIDE.
- [FastAPI](https://fastapi.tiangolo.com/): Framework moderno em Python para criação de APIs rápidas e escaláveis.
- [Uvicorn](https://www.uvicorn.org/): Servidor ASGI de alta performance usado para rodar a aplicação.
- [Google Collab](https://colab.google/): O Google Colab (ou Colaboratory) é um ambiente de desenvolvimento integrado (IDE) gratuito e baseado em nuvem que permite escrever e executar código Python diretamente no navegador, sem necessidade de instalação ou configuração.

---


# Contribuição

Contribuições são bem-vindas!\
Se você encontrar algum problema ou tiver sugestões de melhorias, por favor abra uma **issue** ou envie um **pull request** para o repositório.\
Ao contribuir para este projeto, siga as convenções de commits e envie suas alterações em um **branch** ou **file** separado.\
Saiba mais sobre o código de conduta acessando o link: [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)

---

# Licença

Este repositório possui licença [MIT](https://github.com/MARSELO10/deteccaoVulnerabilidade)
