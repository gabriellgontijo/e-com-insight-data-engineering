# 4.3 Domínios e Serviços

# Visão Geral

A arquitetura do projeto **E-Com Insight** é organizada em domínios de negócio, seguindo princípios de engenharia de dados como baixo acoplamento, alta coesão e separação de responsabilidades.

Essa abordagem permite maior escalabilidade, facilidade de manutenção e evolução independente dos componentes.

---

# Domínios de Negócio

# 1. Domínio de Vendas
Responsável pelas transações realizadas na plataforma.

**Serviços:**
- Serviço de Pedidos → registro de compras realizadas  
- Serviço de Pagamentos → processamento financeiro  
- Serviço de Histórico de Vendas → consolidação para análise  

---

# 2. Domínio de Clientes
Responsável pelos dados e comportamento dos usuários.

**Serviços:**
- Serviço de Cadastro de Clientes → dados cadastrais  
- Serviço de Perfil de Cliente → preferências e comportamento  
- Serviço de Segmentação → agrupamento para campanhas  

---

# 3. Domínio de Produtos e Estoque
Responsável pelo catálogo e disponibilidade de produtos.

**Serviços:**
- Serviço de Catálogo → informações dos produtos  
- Serviço de Estoque → controle de disponibilidade  
- Serviço de Atualização de Produtos → alterações de preço e descrição  

---

# 4. Domínio de Marketing
Responsável pela análise de comportamento e campanhas.

**Serviços:**
- Serviço de Eventos de Navegação → coleta de cliques e sessões  
- Serviço de Campanhas → gestão de promoções  
- Serviço de Análise de Conversão → métricas de funil  

---

# 5. Domínio de Recomendação
Responsável pela geração de recomendações personalizadas.

**Serviços:**
- Serviço de Coleta de Eventos → captura interações do usuário  
- Serviço de Processamento de Recomendação → geração de sugestões  
- Serviço de Entrega de Recomendações → envio para front-end  

---

# 6. Domínio de Logística
Responsável pela entrega e movimentação de produtos.

**Serviços:**
- Serviço de Rastreamento de Pedidos  
- Serviço de Gestão de Entregas  
- Serviço de Distribuição  

---

# Serviços Compartilhados (Transversais)

Esses serviços são utilizados por múltiplos domínios e fazem parte da plataforma de dados:

- Serviço de Ingestão de Dados → coleta de dados batch e streaming  
- Serviço de Armazenamento → Data Lake / Lakehouse  
- Serviço de Processamento → transformação de dados  
- Serviço de Orquestração → gerenciamento de pipelines  
- Serviço de Governança → qualidade, segurança e organização dos dados  
- Serviço de Monitoramento → observabilidade e controle de execução  

---

# Diagrama de Domínios e Serviços

```mermaid
flowchart TD

Vendas --> Pedidos
Vendas --> Pagamentos
Vendas --> Historico

Clientes --> Cadastro
Clientes --> Perfil
Clientes --> Segmentacao

Produtos --> Catalogo
Produtos --> Estoque
Produtos --> Atualizacao

Marketing --> Eventos
Marketing --> Campanhas
Marketing --> Conversao

Recomendacao --> ColetaEventos
Recomendacao --> ProcessamentoRec
Recomendacao --> EntregaRec

Logistica --> Rastreamento
Logistica --> Entregas
Logistica --> Distribuicao

Ingestao --> Vendas
Ingestao --> Clientes
Ingestao --> Produtos
Ingestao --> Marketing

Processamento --> Recomendacao
Armazenamento --> Processamento
Orquestracao --> Processamento
Monitoramento --> Processamento
Governanca --> Armazenamento
