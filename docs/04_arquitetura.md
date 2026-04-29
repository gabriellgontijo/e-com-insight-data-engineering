# 4.4 Arquitetura — Fluxo de Dados

##  Visão Geral da Arquitetura

A arquitetura proposta para o projeto **E-Com Insight** segue o modelo **Lakehouse com abordagem Lambda**, permitindo o processamento integrado de dados batch e streaming.

Essa arquitetura foi escolhida por oferecer flexibilidade, escalabilidade e suporte a múltiplos tipos de análise, atendendo tanto necessidades históricas quanto em tempo real.

---

## Fluxo de Dados (Ponta a Ponta)

O fluxo de dados da arquitetura é dividido nas seguintes etapas:

### 1. Origem dos Dados
Os dados são gerados por diferentes sistemas do e-commerce:

- Sistemas transacionais (vendas, clientes, produtos)  
- Aplicações web/mobile (eventos de navegação)  
- Sistemas logísticos  
- Logs de sistemas e APIs  

---

### 2. Ingestão de Dados

A ingestão ocorre de duas formas:

####  Batch
- Extração periódica de bancos de dados relacionais  
- Dados estruturados  
- Maior latência  

####  Streaming
- Captura contínua de eventos em tempo real  
- Baixa latência  
- Alto volume de dados  

---

### 3. Armazenamento — Data Lake (Lakehouse)

Os dados são armazenados em um Data Lake estruturado no modelo Lakehouse, organizado em camadas:

- **Bronze:** dados brutos, sem tratamento  
- **Silver:** dados limpos e transformados  
- **Gold:** dados agregados e prontos para consumo  

Essa organização permite rastreabilidade e reprocessamento dos dados.

---

## 4. Processamento e Transformação

# Processamento Batch
- Transformação de dados históricos  
- Agregações e cálculos analíticos  
- Preparação de dados para relatórios  

# Processamento Streaming
- Processamento em tempo real  
- Detecção de eventos (ex: abandono de carrinho)  
- Geração de dados para recomendação  

---

# 5. Serviço de Dados (Consumo)

Os dados da camada Gold são disponibilizados para:

- Ferramentas de BI (dashboards e relatórios)  
- Sistemas de recomendação  
- APIs de dados  
- Análises estratégicas  

---

# Separação de Fluxos

# Pipeline Batch
- Dados estruturados (vendas, clientes, produtos)  
- Processamento periódico  
- Foco em análise histórica  

# Pipeline Streaming
- Eventos de navegação e interação  
- Processamento contínuo  
- Foco em baixa latência e tempo real  

---

## 📊 Diagrama da Arquitetura

```mermaid
flowchart LR

subgraph Fontes
A[Vendas/DB]
B[Clientes/CRM]
C[Produtos]
D[Eventos Web]
E[Logs]
end

subgraph Ingestao
F[Batch]
G[Streaming]
end

subgraph Lakehouse
H[Bronze]
I[Silver]
J[Gold]
end

subgraph Processamento
K[Batch Processing]
L[Streaming Processing]
end

subgraph Consumo
M[BI]
N[Recomendação]
O[APIs]
end

A --> F
B --> F
C --> F
D --> G
E --> G

F --> H
G --> H

H --> I
I --> J

H --> K
G --> L

K --> J
L --> J

J --> M
J --> N
J --> O
