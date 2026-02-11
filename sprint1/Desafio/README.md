# Sumário do Desafio Sprint 1
- [Perguntas / Análises](#perguntas--análises)
- [Códigos](#códigos)
- [Evidências](#evidências)

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

# Perguntas / Análises

Perguntas para Filmes

**1. Quais filmes mais antigos presentes no movies.csv ainda possuem popularidade alta no TMDB?**
Relação: usar anoLancamento e tituloOriginal do CSV para buscar o filme no /search/movie ou /movie/{movie_id} e verificar o campo popularity do TMDB.

**2. Existe relação entre o número de votos (numeroVotos) dos filmes no CSV e a receita de bilheteira (revenue) no TMDB?**
Relação: no CSV temos numeroVotos, no TMDB /movie/{movie_id} retorna revenue. Podemos comparar para ver se filmes muito votados também foram grandes bilheteiras.

Perguntas para Séries

**1. Qual a porcentagem das séries do CSV que já estão finalizadas no TMDB (status = Ended) em relação às que ainda estão em produção (status = Returning Series)?**
Relação: no CSV temos anoTermino (se nulo = talvez em andamento), no TMDB /tv/{series_id} traz o status atualizado.

**2. Séries com maior duração total (tempoMinutos * número de episódios no TMDB) são também as mais bem avaliadas (notaMedia)?**
Relação: no CSV temos tempoMinutos e notaMedia. No TMDB /tv/{series_id} temos number_of_episodes. Multiplicando, podemos estimar a duração e relacionar com a média das notas.


# Evidências
Evidência do Docker build:

<img src="../Evidencias/ev1.png"/>
<br><br>

Evidência que os arquivos foram enviados para o bucket S3:

<img src="../Evidencias/ev2.png"/>
<br><br>
<img src="../Evidencias/ev3.png"/>
<br><br>

<img src="../Evidencias/ev4.png"/>

<br><br>

<img src="../Evidencias/ev6.png"/>
Evidência do arquivo rodando no lambda:
<br><br>
<img src="../Evidencias/ev7.png"/>

Evidências de criação das camadas:
<br><br>
<img src="../Evidencias/ev5.png"/>
<br><br>
<img src="../Evidencias/ev8.png"/>