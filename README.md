# ETL_SALARIOS_TI - Arquitetura Medallion com PySpark

## 📌 Descrição
Este projeto realiza um processo de **ETL (Extract, Transform, Load)** sobre uma base de dados global de salários de profissionais de TI.  
O objetivo é **normalizar e padronizar** os dados para que a área de negócios possa realizar análises e descobrir insights relevantes.

---

## 🔎 Profiling dos Dados

- **Validação da quantidade de registros** da fonte de dados.
- **Identificação dos registros nulos** na coluna `ano`.
- **Padronização** dos nomes das **colunas: inglês → português**
- **Identificação das siglas categóricas que serão convertidas** para nomes mais compreensíveis.
- **Apresentação de exemplos antes e depois** das principais transformações realizadas.

## 🏗️ Arquitetura Medallion
Neste projeto, as camadas **Bronze** e **Silver** são mantidas em memória durante o processamento do notebook, sendo utilizadas como etapas intermediárias do pipeline. 
**Em ambientes profissionais, essas camadas normalmente devem ser persistidas em uma camada de armazenamento, garantindo durabilidade, rastreabilidade, reprocessamento e independência entre as etapas do pipeline**. 

![Arquitetura Medallion](imgs/1_medalhao.png)

---

## 🎯 Objetivos do ETL
- **Removendo 10 linhas** nulas da coluna **ano**
- **Tradução dos nomes das colunas** para **português**, tornando o dataset mais legível.
- Padronização de **4 colunas categóricas**:
  - `senioridade`
  - `contrato`
  - `trab_remoto`
  - `tamanho_empresa`

---

## 🛠️ Transformações Realizadas
- **Coluna `contrato`**:  
  - FT → Tempo Integral  
  - PT → Parcial  
  - CT → Contrato  
  - FL → Freelancer  

- **Coluna `trab_remoto`**:  
  - 0 → Presencial  
  - 50 → Híbrido  
  - 100 → Remoto  

- **Coluna `tamanho_empresa`**:  
  - S → Pequena  
  - M → Média  
  - L → Grande  

- **Coluna `senioridade`**:  
 - EX → Executivo
 - EN → Júnior
 - SE → Sênior
 - MI → Pleno

## 📊 Exemplo de Transformação

**Removendo 10 Linhas nulas da coluna ano:**

![Padronizacao colunas](imgs/2_remove_linhas.png)

**Colunas Padronizadas English to Português:**

![Padronizacao colunas](imgs/3_padronizacao_colunas.png)

**Distribuição da coluna `tamanho_empresa` antes e depois da tradução:**

![Antes e depois](imgs/4_antes_depois.png)

## 📊 Amostra Geral do ETL Finalizado

**Resultado do processamento:**

![Amostra sample](imgs/5_etl_salary_sample.png)

## 📊 Camada Gold

A camada **Gold** representa a etapa final do ETL e disponibiliza os dados tratados e padronizados para consumo analítico.

Neste projeto, a Gold é persistida em formato **Parquet** e utilizada como fonte para as análises e perguntas de negócio.

## 📂 Dados de origem e saída

O dataset de origem contém **133.349 registros**. Durante o processamento, **10 registros nulos na coluna `ano` foram removidos**, resultando em **133.339 registros** na camada Gold.

A tabela analítica da Gold é persistida em formato **Parquet** e será utilizada como fonte para o projeto **(LINK em breve aqui)**, desenvolvido no **Databricks**, onde os dados serão utilizados para análises e visualizações.


## Atenção

**Esse projeto pode sofrer alterações a qualquer momento sem aviso prévio com intuito de aplicar melhorias**
## 👤 Autor

**Genivon Silva**

**Engenheiro de Dados**
- 💻 GitHub: [Genivon Silva](https://github.com/jhenivon)
- 🔗 LinkedIn: [Genivon Silva](https://www.linkedin.com/in/genivon-silva-69bb9b9b/)