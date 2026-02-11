# Sumário do Desafio da Sprint 02
- [Códigos](#códigos)
- [Evidências](#evidências)


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

# Observação das Perguntas / Análises

Antes eu tinha avisado que eram 4 perguntas, agora decidi que serão apenas 3 perguntas. Segue abaixo as perguntas definitivas:

Perguntas para Filmes

**1. Quais filmes mais antigos presentes no movies.csv ainda possuem popularidade alta no TMDB?**
Relação: usar anoLancamento e tituloOriginal do CSV para buscar o filme no /search/movie ou /movie/{movie_id} e verificar o campo popularity do TMDB.

**2. Existe relação entre o número de votos (numeroVotos) dos filmes no CSV e a receita de bilheteira (revenue) no TMDB?**
Relação: no CSV temos numeroVotos, no TMDB /movie/{movie_id} retorna revenue. Podemos comparar para ver se filmes muito votados também foram grandes bilheteiras.

Pergunta para Séries

**1. Séries com maior duração total (tempoMinutos * número de episódios no TMDB) são também as mais bem avaliadas (notaMedia)?**
Relação: no CSV temos tempoMinutos e notaMedia. No TMDB /tv/{series_id} temos number_of_episodes. Multiplicando, podemos estimar a duração e relacionar com a média das notas.

# Evidências
Evidência dos jobs executados:
<img src="../Evidencias/ev1.png"/>
<br><br>

script que transforma os csvs em parquet:
<img src="../Evidencias/ev2.png"/>
<br><br>

script que transforma os jsons em parquet:
<img src="../Evidencias/ev3.png"/>
<br><br>

movies.csv em parquet:
<img src="../Evidencias/ev4.png"/>
<br><br>

series.csv em parquet:
<img src="../Evidencias/ev5.png"/>
<br><br>

séries jsons em parquet:
<img src="../Evidencias/ev6.png"/>
<br><br>

filmes jsons em parquet:
<img src="../Evidencias/ev7.png"/>
<br><br>


