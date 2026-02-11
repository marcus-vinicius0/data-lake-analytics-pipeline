# 🎬 Data Lake de Filmes e Séries – Desafio Técnico Compass UOL

> Projeto desenvolvido durante estágio na Compass UOL  
> Foco: Engenharia de Dados na AWS

## 📖 Sobre o Projeto

Este repositório contém o desenvolvimento completo do desafio técnico realizado durante meu estágio na **Compass UOL**.

O desafio foi dividido em **4 sprints**, onde construí um **Data Lake em AWS**, realizando:

- Ingestão de dados (CSV + API TMDB)
- Processamento e padronização
- Modelagem dimensional (Star Schema)
- Construção de Dashboard analítico no Amazon QuickSight

O projeto simula um cenário real de engenharia de dados, seguindo boas práticas de arquitetura em camadas:

Raw -> Trusted -> Refined

---

# 🏗️ Arquitetura do Projeto

📌 Camadas do Data Lake:

- **Raw Layer**
  - Dados brutos (CSV e JSON)
  - Armazenamento no Amazon S3
- **Trusted Layer**
  - Dados limpos e padronizados
  - Conversão para Parquet
- **Refined Layer**
  - Modelagem dimensional
  - Tabelas Fato e Dimensão
  - Pronto para consumo analítico

Serviços AWS utilizados:

- Amazon S3
- AWS Lambda
- AWS Glue (Spark)
- AWS Glue Crawler
- Amazon QuickSight
- Docker

---

# 🚀 Evolução por Sprint

Em cada sprint eu resolvi uma etapa do desafio. Além disso realizei cursos técnicos relacionados para aprofundar meus conhecimentos práticos. Poderá ser encontrado um resumo do que aprendi em cada sprint, certificados dos cursos que eu fiz, evidências do desafio.

## 🟢 Sprint 1 – Ingestão de Dados (Raw Layer)

### Objetivo
Criar a camada Raw no S3 realizando ingestão de:

- Arquivos CSV (movies.csv e series.csv)
- Dados da API do TMDB

### Implementação

✔ Upload de CSV para S3 via Python + boto3  
✔ Containerização com Docker  
✔ Ingestão via AWS Lambda para API TMDB  
✔ Particionamento por data no S3  

Estrutura de armazenamento:

Raw/<br>
├── Local/CSV/Movies/<br>
├── Local/CSV/Series/<br>
└── TMDB/JSON/{movies|series}/ano/mes/dia/


---

## 🟡 Sprint 2 – Processamento (Trusted Layer)

### Objetivo
Transformar dados brutos em dados tratados no formato Parquet.

### Implementação

✔ AWS Glue (Spark)  
✔ Limpeza de dados  
✔ Deduplicação  
✔ Cast de tipos  
✔ Tratamento de strings  
✔ Conversão JSON → Parquet  
✔ Conversão CSV → Parquet  

Saída armazenada na camada:<br>
Trusted/<br>
├── Movies/<br>
└── Series/


---

## 🔵 Sprint 3 – Modelagem Dimensional (Refined Layer)

### Objetivo
Criar modelo dimensional para análise de dados.

Foram desenvolvidas tabelas:

### 🎬 Para Filmes
- DimFilme
- DimGenero
- DimTempo
- FatoFilme

### 📺 Para Séries
- DimSerie
- DimGenero
- DimTempo
- FatoSerie

Filtro aplicado:
- Apenas conteúdos de **Ficção Científica e Fantasia**

Modelos dimensionais:

![Modelo Filmes](sprint4/Desafio/assets/modeloDimensionalFilmes.png)

![Modelo Séries](sprint4/Desafio/assets/modeloDimensionalSeries.png)

Dados armazenados em:

Refined/<br>
├── Movies/<br>
│ ├── DimFilme/<br>
│ └── FatoFilme/<br>
└── Series/<br>
├── DimSerie/<br>
└── FatoSerie/


✔ Glue Crawler para catalogação  
✔ Escrita em Parquet  
✔ Geração de chaves substitutas  

---

## 🟣 Sprint 4 – Dashboard (QuickSight)

Construção de dashboard analítico para responder perguntas estratégicas.

### 📊 Perguntas Analisadas

### 🎬 Filmes

1. Filmes antigos ainda possuem alta popularidade?
2. Existe relação entre número de votos e receita?

### 📺 Séries

1. Séries mais longas são melhor avaliadas?

---

# 📈 Principais Insights

### 🎬 Filmes

- Filmes mais novos tendem a ter maior popularidade média.
- Existe correlação positiva entre número de votos e receita.
- Filmes antigos com alta popularidade são exceções específicas.

### 📺 Séries

- Não foi identificada correlação clara entre duração total e nota média.

---

# 📊 Dashboard

Dashboard completo desenvolvido no Amazon QuickSight.

![Dashboard](sprint4/Evidencias/ev3.png)

Principais visualizações:

- Scatter plot (Ano vs Popularidade)
- Scatter plot (Votos vs Receita – escala log)
- Mediana de Receita por faixa de votos
- Duração total vs Nota média

---

# 🎨 Identidade Visual

O dashboard foi desenvolvido utilizando:

- Tema Dark Mode
- Paleta de cores baseada na identidade visual da Compass UOL

---

# 🛠️ Tecnologias Utilizadas

- Python 3.10
- Spark (AWS Glue)
- boto3
- AWS Lambda
- Amazon S3
- AWS Glue
- AWS Glue Crawler
- Amazon QuickSight
- Docker

---

# 📚 Aprendizados

Durante as sprints também realizei cursos técnicos relacionados a:

- Engenharia de Dados na AWS
- Modelagem Dimensional
- Spark
- Boas práticas em Data Lake

Certificados podem ser encontrados na pasta `/certificados` de cada sprint.

Ao final do estágio, consegui obter a certificação AWS cloud practitioner, consolidando meus conhecimentos em AWS. O certificado pode ser encontrado na pasta `/certificados` da Sprint 4.

---

# 📌 Conclusão

Este projeto consolidou conhecimentos práticos em:

✔ Construção de Data Lake  
✔ Ingestão batch e API  
✔ Processamento distribuído com Spark  
✔ Modelagem dimensional  
✔ Construção de dashboards analíticos  
✔ Arquitetura em camadas (Raw, Trusted, Refined)  

Observação: não pude compartilhar os códigos de resolução do desafio por questões de confidencialidade, mas coloquei evidências de execução para demonstrar o processo.