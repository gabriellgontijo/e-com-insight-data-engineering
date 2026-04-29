# 4.2 Definição e Classificação dos Dados

# Visão Geral dos Dados

O projeto **E-Com Insight** utiliza dados provenientes de diferentes sistemas de um e-commerce, integrando tanto dados operacionais (batch) quanto dados de streaming (tempo real).

Essa combinação permite suportar:
- análises históricas e estratégicas  
- monitoramento em tempo real  
- sistemas de recomendação  



# Classificação dos Dados

Os dados foram classificados em dois grupos principais:

# Dados Operacionais (Batch)
Dados estruturados, armazenados em sistemas transacionais e processados periodicamente.

# Dados de Streaming
Dados gerados continuamente, processados com baixa latência para respostas em tempo real.



#  Dados Operacionais (Batch)

# 1. Dados de Vendas
- **Origem:** Banco de dados transacional (e-commerce)  
- **Formato:** CSV / Parquet  
- **Conteúdo:** pedidos, produtos, valores, datas  
- **Periodicidade:** diária  
- **Latência:** alta (horas)  
- **Volume estimado:** médio (milhares de registros por dia)  



# 2. Dados de Clientes
- **Origem:** Sistema de CRM  
- **Formato:** JSON / CSV  
- **Conteúdo:** informações cadastrais e histórico de compras  
- **Periodicidade:** diária  
- **Latência:** alta  
- **Volume:** médio  



# 3. Dados de Produtos
- **Origem:** Sistema de catálogo  
- **Formato:** JSON / CSV  
- **Conteúdo:** descrição, preço, categoria  
- **Periodicidade:** sob demanda / diária  
- **Latência:** média  
- **Volume:** baixo a médio  



# 4. Dados de Estoque
- **Origem:** Sistema logístico  
- **Formato:** CSV  
- **Conteúdo:** quantidade disponível e localização  
- **Periodicidade:** diária  
- **Latência:** média  
- **Volume:** médio  



#  Dados de Streaming (Tempo Real)

# 1. Eventos de Navegação (Clickstream)
- **Origem:** Aplicação web/mobile  
- **Formato:** JSON  
- **Conteúdo:** cliques, páginas visitadas, tempo de sessão  
- **Frequência:** contínua  
- **Latência:** baixa (segundos)  
- **Volume estimado:** alto (milhares de eventos por minuto)  



# 2. Eventos de Carrinho
- **Origem:** Sistema de compras  
- **Formato:** JSON  
- **Conteúdo:** adição/remoção de produtos, abandono de carrinho  
- **Frequência:** contínua  
- **Latência:** baixa  
- **Volume:** alto  



# 3. Logs de Sistema
- **Origem:** servidores e APIs  
- **Formato:** JSON / texto  
- **Conteúdo:** erros, requisições, desempenho  
- **Frequência:** contínua  
- **Latência:** baixa  
- **Volume:** alto  



# 4. Eventos para Recomendação
- **Origem:** interações do usuário  
- **Formato:** JSON  
- **Conteúdo:** produtos visualizados, comprados e tempo de interação  
- **Frequência:** contínua  
- **Latência:** muito baixa  
- **Volume:** alto  



#  Tabela Resumo dos Dados

| Tipo        | Fonte              | Formato        | Frequência  | Latência | Volume |
|------------|-------------------|---------------|------------|---------|--------|
| Vendas     | Banco transacional| CSV/Parquet   | Diário     | Alta    | Médio  |
| Clientes   | CRM               | JSON/CSV      | Diário     | Alta    | Médio  |
| Produtos   | Catálogo          | JSON/CSV      | Diário     | Média   | Baixo  |
| Estoque    | Logística         | CSV           | Diário     | Média   | Médio  |
| Navegação  | Web/App           | JSON          | Contínuo   | Baixa   | Alto   |
| Carrinho   | Sistema de compra | JSON          | Contínuo   | Baixa   | Alto   |
| Logs       | Servidores        | JSON/Texto    | Contínuo   | Baixa   | Alto   |
| Recomendação| Interações       | JSON          | Contínuo   | Muito baixa | Alto |



## 🔍 Considerações

- A separação entre batch e streaming permite atender diferentes necessidades analíticas  
- Dados batch são utilizados para análises históricas e relatórios  
- Dados de streaming permitem respostas rápidas e suporte a sistemas de recomendação  
- A diversidade de formatos (CSV, JSON, Parquet) exige uma arquitetura flexível  

---
