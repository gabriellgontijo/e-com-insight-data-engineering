# 4.5 Tecnologias — Como será feito

##  Visão Geral

A arquitetura do projeto **E-Com Insight** utiliza um conjunto de tecnologias modernas, cobrindo todas as etapas do ciclo de vida de engenharia de dados: ingestão, armazenamento, processamento, orquestração e consumo.

As escolhas foram feitas considerando escalabilidade, flexibilidade e viabilidade de implementação em ambiente local (Parte 2 do projeto).

---

##  1. Ingestão de Dados

### Tecnologias:
- Apache Kafka (streaming)  
- Airbyte (batch)

### Justificativa:

O **Apache Kafka** será utilizado para ingestão de dados em tempo real, permitindo alta taxa de processamento e baixa latência, sendo ideal para eventos como navegação e interações do usuário.

O **Airbyte** será utilizado para ingestão batch, facilitando a extração de dados de bancos relacionais e sua integração com o Data Lake de forma automatizada.

### Integração:
- Airbyte envia dados batch para o Data Lake  
- Kafka envia eventos para processamento em tempo real  

---

##  2. Armazenamento

### Tecnologias:
- MinIO (simulação local de S3)  
- Delta Lake  

### Justificativa:

O **MinIO** será utilizado como Data Lake local, permitindo armazenamento escalável e compatível com soluções em nuvem.

O **Delta Lake** adiciona suporte a transações ACID, versionamento e organização em camadas (Bronze, Silver e Gold), caracterizando o modelo Lakehouse.

### Integração:
- Dados ingeridos são armazenados no MinIO  
- Delta Lake organiza e gerencia as camadas  

---

##  3. Processamento e Transformação

### Tecnologias:
- Apache Spark  
- Pandas (apoio)

### Justificativa:

O **Apache Spark** será utilizado para processamento distribuído, suportando tanto batch quanto streaming (Structured Streaming).

O **Pandas** será utilizado para testes locais e pequenas validações.

### Integração:
- Spark lê dados do Data Lake  
- Processa e grava nas camadas Silver e Gold  
- Consome dados de streaming via Kafka  

---

##  4. Orquestração

### Tecnologia:
- Apache Airflow

### Justificativa:

O **Airflow** será responsável pelo agendamento e controle dos pipelines batch, garantindo organização, monitoramento e reexecução em caso de falhas.

### Integração:
- Controla execuções do Spark  
- Coordena ingestão batch via Airbyte  

---

## 5. Consumo de Dados

### Tecnologias:
- Power BI (ou Metabase)

### Justificativa:

Ferramentas de BI serão utilizadas para visualizar dados da camada Gold, permitindo análises estratégicas e operacionais.

### Integração:
- Conectam-se diretamente aos dados processados  

---

##  6. Sistema de Recomendação

### Tecnologias:
- Apache Spark (Streaming)

### Justificativa:

O processamento em tempo real permite gerar recomendações com base no comportamento recente do usuário, como produtos visualizados e interações.

---

##  7. Infraestrutura e Ambiente

### Tecnologia:
- Docker

### Justificativa:

O Docker será utilizado para containerizar os serviços, garantindo padronização do ambiente, isolamento de dependências e facilidade de implementação na Parte 2 do projeto.

---

## . Governança, Segurança e DataOps

A arquitetura considera práticas essenciais do ciclo de vida de dados:

- **Segurança:** controle de acesso aos dados e isolamento de ambientes  
- **Governança:** organização e qualidade dos dados nas camadas Bronze, Silver e Gold  
- **Monitoramento:** acompanhamento de pipelines via Airflow  
- **DataOps:** automação e padronização dos processos com uso de Docker  

---

##  Integração Geral

O fluxo integrado ocorre da seguinte forma:

1. Airbyte realiza ingestão batch  
2. Kafka recebe eventos em tempo real  
3. Dados são armazenados no Data Lake (MinIO + Delta Lake)  
4. Spark processa dados batch e streaming  
5. Airflow orquestra os pipelines  
6. Dados são consumidos por BI e sistemas de recomendação  

---

## Considerações

- A stack escolhida é amplamente utilizada no mercado  
- Permite escalabilidade e flexibilidade  
- É viável de implementar em ambiente local utilizando Docker  

---
