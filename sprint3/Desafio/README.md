# Sumário do Desafio da Sprint
- [Códigos](#códigos)
- [Modelo Dimensional](#modelo-dimensional)
- [Evidências](#evidências)


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

![Modelo Filmes](../Desafio/modeloDimensionalFilmes.png)

![Modelo Séries](../Desafio/modeloDimensionalSeries.png)

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

# Perguntas / Análises

Perguntas para Filmes

**1. Quais filmes mais antigos presentes no movies.csv ainda possuem popularidade alta no TMDB?**
Relação: usar anoLancamento e tituloOriginal do CSV para buscar o filme no /search/movie ou /movie/{movie_id} e verificar o campo popularity do TMDB.

**2. Existe relação entre o número de votos (numeroVotos) dos filmes no CSV e a receita de bilheteira (revenue) no TMDB?**
Relação: no CSV temos numeroVotos, no TMDB /movie/{movie_id} retorna revenue. Podemos comparar para ver se filmes muito votados também foram grandes bilheteiras.

Pergunta para Séries

**1. Séries com maior duração total (tempoMinutos * número de episódios no TMDB) são também as mais bem avaliadas (notaMedia)?**
Relação: no CSV temos tempoMinutos e notaMedia. No TMDB /tv/{series_id} temos number_of_episodes. Multiplicando, podemos estimar a duração e relacionar com a média das notas.


# Modelo Dimensional

Resolvi fazer dois modelos dimensionais separados, um para filmes e outro para séries, pois apesar de termos algumas colunas em comum, as tabela fatos são diferentes.


Modelo Dimensional Filmes:
<img src="modeloDimensionalFilmes.png"/>

Modelo Dimensional Séries:
<img src="modeloDimensionalSeries.png"/>

# Evidências

Evidência do job no AWS Glue:



<img src="../Evidencias/ev1.png"/>
<br><br>
Evidência da execução do job:

<br>

<img src="../Evidencias/ev2.png"/>
<br><br>
Evidência dos dados no S3 em formato Parquet:

<br>
<img src="../Evidencias/ev3.png"/>
<img src="../Evidencias/ev4.png"/>
<img src="../Evidencias/ev5.png"/>
<br><br>
Evidência da execução do Crawler:

<br>
<img src="../Evidencias/ev6.png"/>
<br><br>
Evidência das tabelas geradas:

<br>
<img src="../Evidencias/ev7.png"/>
<br><br>
Evidência da tabela dimSerie:

<br>
<img src="../Evidencias/ev8.png"/>
<br><br>
Evidência da tabela dimTempoSerie:

<br>
<img src="../Evidencias/ev9.png"/>
<br><br>
Evidência da tabela dimGeneroSerie:

<br>
<img src="../Evidencias/ev10.png"/>
<br><br>
Evidência da tabela fatoSerie:

<br>
<img src="../Evidencias/ev11.png"/>
<br><br>
Evidência da tabela dimFilme:

<br>
<img src="../Evidencias/ev12.png"/>
<br><br>
Evidência da tabela dimTempoFilme:

<br>
<img src="../Evidencias/ev13.png"/>
<br><br>
Evidência da tabela fatoFilme:

<br>
<img src="../Evidencias/ev14.png"/>
<br><br>
Evidência da tabela dimGeneroFilme:

<br>
<img src="../Evidencias/ev15.png"/>

<br><br>