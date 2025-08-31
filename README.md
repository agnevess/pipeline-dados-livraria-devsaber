# 📚 Projeto BigQuery - Livraria DevSaber

Este projeto foi desenvolvido como exercício do módulo de **SQL e BigQuery**.  
A proposta é criar um mini *data warehouse* para uma livraria fictícia, armazenar dados e realizar consultas analíticas.

---

## 📂 Estrutura dos Arquivos

- **01_create_tables_bigquery.sql** → Script para criar as tabelas (`Clientes`, `Produtos`, `Vendas`).
- **02_insert_data_bigquery.sql** → Inserção de dados fictícios.
- **03_analysis_and_view_bigquery.sql** → Criação de uma view analítica `v_relatorio_vendas_detalhado`e realização de consultas para análise dos dados.

---

## 🔍 Objetivos do Projeto

1. Criar as tabelas e definir o schema no **Google BigQuery**.
2. Inserir dados fictícios representando vendas reais.
3. Criar uma **VIEW** para facilitar consultas analíticas.
4. Desenvolver consultas que respondam perguntas de negócio.

---

## 🛠️ Tecnologias Utilizadas
- Google BigQuery
- SQL Padrão
- Google Cloud Console

---

## 📈 Exemplos de Insights
- Nome de clientes que moram em determinado estado
- Identificação de produtos do gênero Ficção Científica 
- Listagem de vendas
- Valor total de cada venda
- Produto mais vendido em quantidade

---
## ❓ Perguntas e Respostas do Projeto

### 🔹 1. Por que uma planilha não é ideal para uma empresa que quer analisar suas vendas a fundo?

Planilhas funcionam bem para dados pequenos e análises simples, mas **não escalam** quando há grandes volumes de vendas ou a necessidade de cruzar informações de várias fontes.  
- Limitações de tamanho, performance e controle de acesso.  
- Difícil de manter consistência e integridade dos dados.  
- Poucos recursos avançados de consulta e automação.  
Um banco de dados como o BigQuery permite **análises rápidas, seguras e escaláveis**.

---

### 🔹 2. Que tipo de perguntas o dono da livraria gostaria de responder com esses dados?

- Quais são os **clientes que mais gastam**?  
- Quais **produtos mais vendem** e em quais períodos?  
- Como está o **estoque** atual e quais produtos precisam de reposição?  
- Quais são os **picos de venda por dia/mês**?  
- Qual é a **receita total** por categoria de produto ou por período?

---

### 🔹 3. Com base nos dados brutos, quais outras duas tabelas poderíamos criar?

Além de `Clientes`, `Produtos` e `Vendas`, poderíamos criar:

1. **Tabela Funcionarios**  
   - `ID_Funcionario` (INT64)  
   - `Nome_Funcionario` (STRING)  
   - `Cargo` (STRING)  
   - `Email` (STRING)

2. **Tabela Fornecedores**  
   - `ID_Fornecedor` (INT64)  
   - `Nome_Fornecedor` (STRING)  
   - `Contato` (STRING)  
   - `Categoria_Produtos` (STRING)

Essas tabelas ajudariam a acompanhar **responsáveis pelas vendas** e **origem dos produtos**.

---

### 🔹 4. Se o BigQuery não tem chaves estrangeiras, como garantir integridade?

O BigQuery não valida automaticamente as relações, então a responsabilidade é do **analista/engenheiro de dados**:  
- Conferir consistência dos dados ao inserir registros.  
- Usar `JOIN` corretamente para relacionar as tabelas.  
- Criar processos de ETL ou scripts para validar IDs inexistentes.

---

### 🔹 5. Por que inserir clientes e produtos antes das vendas?

Inserir primeiro os **cadastros base** (clientes e produtos) garante:  
- Que todos os registros de vendas referenciem **entidades existentes**.  
- Facilidade em manter histórico de preços, categorias e dados dos clientes.  
- Melhora a organização e evita duplicações.

---

### 🔹 6. Em um cenário com milhões de vendas por dia, `INSERT INTO` seria ideal?

Não. Para grandes volumes, o ideal é:  
- **Carga em lote (batch load)** com arquivos CSV/Parquet.  
- Integração com pipelines ETL/ELT (Dataflow, Apache Beam, etc.).  
- Isso é muito mais rápido e econômico que inserir linha por linha com `INSERT INTO`.

---

### 🔹 7. Principal vantagem de uma `VIEW` em vez de salvar código em arquivo de texto?

- A `VIEW` **salva a lógica no banco** e sempre executa a consulta com dados atualizados.  
- Evita reescrever ou procurar scripts manualmente.  
- Permite versionamento, segurança e fácil compartilhamento.

---

### 🔹 8. O `Valor_Total` na VIEW será atualizado automaticamente?

Sim! O BigQuery recalcula o `Valor_Total` **toda vez que a view é consultada**.  
Se o preço em `Produtos` mudar, o resultado refletirá automaticamente a alteração, sem precisar reprocessar ou salvar dados manualmente.

---


