---
marp: true
backgroundImage: 'default_bg.png'
math: mathjax
---
<style>

:root{
  font-family: "Source Sans Pro", sans-serif;
}

section {
  background-image: url(default_bg.png);
  font-family: "Source Sans Pro", sans-serif;
}
h1, h2, h3, strong {
  color: #003E7E;
}
h3, h4, h5 {
  text-align: center;
}
h4, h5 {
  font-weight: normal;
}
h1 {
  font-size: 200%;
}
h2, h3 {
  font-size: 150%;
}
h4 {
  font-size: 100%;
}
h5 {
  font-size: 75%;
}
header, a {
  color: #058ED0;
}
header {
  font-size: 85%;
}
footer {
  color: black;
  font-size: 60%;
}
blockquote {
  background: #f9f9f9;
  font-style: italic;
  font-family: Source Sans Pro;
  font-size: 80%;
  line-height: 170%;
  border-left: 10px solid #ccc;
  margin: 1.5em 20px;
  padding: 1.2em 30px;
  quotes: "\201C""\201D""\2018""\2019";
}
blockquote p {
  display: inline;
}
section::after {
  content: attr(data-marpit-pagination) ' / ' attr(data-marpit-pagination-total);
  color: #003E7E;
  font-size: 60%;
}
table {
  margin-left: auto;
  margin-right: auto;
}
th {
  background-color: #003E7E;
  color: white
}
.columns {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 1rem;
}
.columns3 {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 1rem;
}
.codeimage {
  display: grid;
  grid-template-columns: 35% 65%;
  gap: 1rem;
}

.codeimage2 {
  display: grid;
  grid-template-columns: 30% 70%;
  gap: 1rem;
}
span.under {
  text-decoration: underline;
}

span.fade {
  color: lightgray!important;
}

section > h2 {
  flex: 0.2 0 auto;
  padding: 0;
  margin: 0;
  order: -999999;
}

section:has(> h2)::before {
  flex: 1 0 auto;
  display: block;
  content: '';
  order: 999999;
}

</style>

![bg](section_bg.png)

# Gráficos de linha: linheplot e paleta de cores

**Programação para Advogados – 2024.2**
José Luiz Nunes e Lucas Thevenard

---

<!-- 
paginate: true 
header: Aula 7 - Selecionando pontos e mais distribuições
footer: jose.luiz@fgv.br | lucas.gomes@fgv.br | 16/09/2024
-->

## Roteiro da Aula

- Pointplot
  1. Selecionando pontos específicos
  2. Intervalo de valores
  3. Customização

- Lembrando: Definindo cores para categorias

- Stripplot e Swarmpot

---

## Vamos carregar os dados

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

idh = pd.read_csv("https://bit.ly/idh_tidy")

idh.head()
```

Estamos voltando para o dataset de IDH que contém a série histórica dos países.

**Atenção**: Chamamos nosso dataset de `idh`.

---

## Pointplot

- Em aulas anteriores, vimos como criar gráficos de linha com o `lineplot`.

- Vimos também que poderíamos destacar a mudança total com o `pointplot`, mas não fizemos esse gráfico.

- Agora temos todos os recursos para criar um gráfico nesse formato.

---

## Pointplot

Qual o passo a passo necessário para criar esse gráfico com a função `pointplot`?

<div class="codeimage">

<div>


</div>

<div>

![](point_inicio_fim.png)

</div>

</div>

---

## Pointplot

Qual o passo a passo necessário para criar esse gráfico?

<div class="codeimage">

<div>

1. Selecionar os **pontos específicos** que queremos destacar.

</div>

<div>

![](point_inicio_fim.png)

</div>

</div>

---

## Pointplot

Qual o passo a passo necessário para criar esse gráfico?

<div class="codeimage">

<div>

1. Selecionar os **pontos específicos** que queremos destacar.
  a) Selecionar Países
  b) Selecionar Anos

</div>

<div>

![](point_inicio_fim.png)

</div>

</div>

---

## Pointplot

Qual o passo a passo necessário para criar esse gráfico?

<div class="codeimage">

<div>

1. Selecionar os **observações** para manter.
  a) Selecionar Países
  b) Selecionar Anos
2. Definir **paleta** de cores

</div>

<div>

![](point_inicio_fim.png)

</div>

</div>

---

## Pointplot

Qual o passo a passo necessário para criar esse gráfico?

<div class="codeimage">

<div>

1. Selecionar os **observações** para manter.
  a) Selecionar Países
  b) Selecionar Anos
2. Definir **paleta** de cores
3. Criar o **gráfico**

</div>

<div>

![](point_inicio_fim.png)

</div>

</div>

---


## Pointplot

**Começando**: para fazer a seleção precisamos da variável `ano` e `pais`.

- Como proceder para fazer cada filtro?

---


## Pointplot

**Começando**: para fazer a seleção precisamos da variável `ano` e `pais`.

- Como proceder para fazer cada filtro?

```python
anos_interesse = [1990, 2022]

idh_anos = idh.query("ano in @anos_interesse")
```

---


## Pointplot

**Começando**: para fazer a seleção precisamos da variável `ano` e `pais`.

- Como proceder para fazer cada filtro?

```python
paises_interesse = ["Brasil", "Argentina", "China"]

df_comp_paises = idh_anos.query("pais in @paises_interesse")
```

---

## Pointplot

Todo nosso processo:

```python
idh
# Começamos com os dados carregados na variável `idh`

anos_interesse = [1990, 2022]
idh_anos = idh.query("ano in @anos_interesse")
# criamos uma nova variável com os anos de interesse

paises_interesse = ["Brasil", "Argentina", "China"]
df_comp_paises = idh_anos.query("pais in @paises_interesse")
# criamos uma terceira variável com os países de interesse
# Usamos idh_anos par manter o filtro anterior
```

**Pergunta**: Se alterarmos a ordem dos filtros, o resultado será o mesmo?
