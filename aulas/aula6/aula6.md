---
marp: true
backgroundImage: 'default_bg.png'
math: mathjax
---
<style>
section {
  background-image: url(default_bg.png);
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
  font-family: Verdana;
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
span.under {
  text-decoration: underline;
}
td.game, tr.game {
  background-color: white;
  text-align: center;
}
tr.game.action.player1, td.game.action.player1 {
  background-color: #f8f8f8;
  color: #058ED0;
  font-weight: bold;
}
tr.game.action.player2, td.game.action.player2 {
  background-color: #f8f8f8;
  color: #003E7E;
  font-weight: bold;
}
span.payoff.player1 {
  color: #058ED0;
  font-weight: bold;
}
span.payoff.player2 {
  color: #003E7E;
  font-weight: bold;
}
span.fade {
  color: lightgray!important;
}
td.eliminated {
  color: lightgray!important;
  text-decoration: line-through!important;
}
td.eliminated > span {
  color: lightgray!important;
  text-decoration: line-through!important;
}
td.player1 {
  height: 80px;
  width: 80px;
}
</style>


![bg](section_bg.png)

# Explorando distribuições – KDE, ECDF e Boxplot
**Programação para Advogados – 2024.2**
José Luiz Nunes e Lucas Thevenard

---
<!-- 
paginate: true 
header: Explorando distribuições – KDE, ECDF e Boxplot
footer: jose.luiz@fgv.br | lucas.gomes@fgv.br | 09/09/1986
-->


## O que aprendemos até aqui?

- **Argumentos no seaborn**
  * `x` e `y`
  * `data`
  * `hue`
  * `color`
  * `palette`
  * `hue_order`
  * `errorbar`
  * `estimator`

---

## O que aprendemos até aqui?

- **O que passamos para os argumentos?**
  * `x` e `y`:
    * variáveis numéricas ou categóricas - `str`
  * `data`:
    * nosso conjunto de dados - `pd.DataFrame`
  * `hue`:
    * variável categórica - `str`
  * `color`:
    * cor única - `str`

---

## O que aprendemos até aqui?

- **O que passamos para os argumentos?**
  * `palette`:
    * nome de paleta ou conjunto de cores - `str`, `list`, ou `dict`
  * `hue_order`:
    * ordem das categorias - `list` de `str`
  * `errorbar`:
    * controla barra de erro - `None` (**não vimos como alterar**)
  * `estimator`:
    * função para resumir dados - `str`; `"mean"`, `"sum"`, `"median"`

---

## Roteiro de Aula

- Gráficos KDE e ECDF
- Quartis e intervalo interquartil
- Boxplot

---



---

<div class="columns">
<div style="margin: auto;">

## KDE (Kernel Density Estimate)

- Como podemos criar um gráfico para compreender a distribuição dos valores do IDH dos países em 2022 (coluna `"idh"` da nossa base) usando a função `kdeplot`?
  * Você consegue ver algum problema nesse gráfico?

</div>
<div style="margin: auto;">
<br><br>

![w:700](kde_idh.png)

</div>
</div>