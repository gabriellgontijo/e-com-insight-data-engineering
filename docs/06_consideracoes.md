# 4.6 Considerações Finais

##  Riscos e Limitações

Apesar da arquitetura proposta ser robusta e alinhada com práticas modernas de engenharia de dados, alguns desafios devem ser considerados:

- Complexidade na integração entre múltiplas tecnologias  
- Limitações de recursos computacionais (CPU, memória e armazenamento) em ambiente local  
- Possíveis dificuldades na configuração de ferramentas como Kafka e Spark  
- Latência maior em ambiente simulado em comparação com produção  

---

##  Viabilidade do Projeto

A arquitetura foi planejada considerando a viabilidade de implementação na Parte 2, utilizando:

- Ferramentas open-source  
- Execução local com Docker  
- Dados simulados ou em menor escala  

Essa abordagem garante que o projeto seja executável dentro das limitações de infraestrutura disponíveis.

---

##  Próximos Passos (Parte 2)

Na próxima etapa do projeto, será realizada a implementação prática da arquitetura planejada, incluindo:

- Configuração do ambiente com Docker  
- Implementação da ingestão de dados (batch e streaming)  
- Criação das camadas do Data Lake (Bronze, Silver e Gold)  
- Desenvolvimento de pipelines com Apache Spark  
- Orquestração dos fluxos com Airflow  
- Criação de dashboards para visualização dos dados  
- Implementação de um protótipo de sistema de recomendação  

---

##  Referências

- Conteúdo das aulas da disciplina de Engenharia de Dados  
- Documentação oficial das ferramentas utilizadas:
  - Apache Kafka  
  - Apache Spark  
  - Apache Airflow  
  - Delta Lake  
- Conceitos de arquitetura de dados (Lakehouse e Lambda Architecture)  

---
