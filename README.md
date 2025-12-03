# 📡 Pipeline de Mensagens do Telegram com AWS

Este projeto implementa um pipeline de dados que captura mensagens de um grupo do Telegram, armazena-as em um data lake na AWS e as disponibiliza para análise via SQL no Athena.

---

## 🔧 Tecnologias Utilizadas
- **AWS**: API Gateway, Lambda, S3, EventBridge, Athena  
- **Python**  
- **SQL**  
- **Webhooks**

---

## 🧱 Arquitetura do Pipeline
O pipeline é dividido em duas camadas:

### **1. Sistema Transacional (Telegram)**
- Um bot é adicionado ao grupo do Telegram.  
- Mensagens são enviadas ao **API Gateway** via webhook.

### **2. Sistema Analítico (AWS)**
- **Ingestão:** API Gateway → Lambda → S3 (JSON).  
- **ETL:** EventBridge ativa Lambda que transforma JSON em Parquet.  
- **Apresentação:** Dados organizados em tabela particionada no **Athena**.

---

## 🗂️ Principais Componentes

### ✔️ Ingestão
- Webhook recebe mensagens do Telegram.  
- Lambda valida o chat e salva no S3 em formato JSON.

### ✔️ ETL
- Lambda processa todos os arquivos do dia.  
- Dados são transformados e gravados em Parquet no bucket enriquecido.

### ✔️ Athena
- Criação de tabela para consultas SQL.  
- Permite análises como:
  - Mensagens por dia  
  - Mensagens repetidas  
  - Quantidade de mensagens por usuário

---

## 📊 Resultados
O pipeline permite análises rápidas e flexíveis sobre o grupo, gerando insights sobre volume, comportamento dos usuários e padrões de mensagens.
