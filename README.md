# 📊 Pipeline Analítico de SST - Engenharia de Dados com Databricks e Spark

Este repositório contém um projeto analítico de ponta a ponta focado em Saúde e Segurança do Trabalho (SST), desenvolvido integralmente na plataforma **Databricks** utilizando a **Arquitetura Medalhão**.

O objetivo principal é processar logs operacionais brutos de ocorrências de segurança para extrair indicadores executivos de riscos corporativos que apoiem tomadores de decisão na prevenção de acidentes.

---

## 🔗 Links do Projeto
- **Dashboard Interativo Databricks:** https://dbc-258ec21e-749c.cloud.databricks.com/dashboardsv3/01f1c4b5c6021b88a94f785d385da940/published?o=7474648198152027

---

## 🏗️ Arquitetura de Dados (Governança Medalhão)

O pipeline foi estruturado utilizando **PySpark** e **Delta Lake** para garantir consistência, performance e eliminação de redundâncias em três estágios:

1. **Camada Bronze (Ingestão):** Consumo dos arquivos brutos em formato `.csv` armazenados nos Volumes do DBFS (`acidentes_sst.csv`, `cat_emitidas.csv`, `horas_trabalhadas.csv` e `quase_acidentes.csv`).
2. **Camada Silver (Limpeza & Padronização):** Aplicação de funções do Spark para eliminação de registros duplicados (`dropDuplicates`), conversão e herança de tipos de dados (datas e inteiros) e sanitização de strings.
3. **Camada Gold (Agregação de Negócio):** Construção de tabelas analíticas Delta consolidadas utilizando **Spark SQL** (`gold_causas`, `gold_accidents_gravidade` e `gold_taxa_frequencia`).

---

## 💡 Principais Insights Gerenciais Obtidos

- **O Paradoxo do Volume Absoluto vs. Risco Real:** Uma análise superficial dos dados absolutos apontaria a unidade de **Petrolina** como a mais crítica por registrar o maior volume de acidentes (6 ocorrências). No entanto, ao normalizar os dados aplicando a métrica de **Taxa de Frequência (TF)** por milhão de horas trabalhadas, a unidade de **Juazeiro** revelou-se o cenário de maior risco ocupacional da empresa, liderando o índice com **37.14**.
- **Mapeamento de Causa Raiz:** O painel aponta que fatores operacionais como *Ferramentas inadequadas* e *Falta de isolamento de energias perigosas* figuram no topo das causas de incidentes, indicando gargalos imediatos para investimento em manutenção e reciclagem de treinamentos.

---

## 🚀 Tecnologias e Conceitos Aplicados
- **Databricks Unified Analytics Platform**
- **Apache Spark / PySpark**
- **Delta Lake** (ACID Transactions)
- **Spark SQL**
- **Databricks AI/BI Dashboards**

