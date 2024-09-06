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
- Query

---

### Passos Preliminares

<div style="margin: auto;">

![w:700](passos_preliminares.png)

</div>

---

<div class="columns">
<div style="margin: auto;">

## KDE (Kernel Density Estimate)

- Como podemos criar um gráfico para compreender a distribuição dos valores do IDH dos países em 2022 (coluna `"idh"` da nossa base) usando a função `kdeplot`?

<br><br>
</div>
<div style="margin: auto;">
<br><br>



</div>
</div>

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

---

<div class="columns">
<div style="margin: auto;">
<br><br>

![w:500](hist_idh.png)


</div>
<div style="margin: auto;">
<br><br>

![w:520](kde_idh.png)

</div>
</div>

---

<div class="columns">
<div style="margin: auto;">

## ECDF (Empirical Cum. Dist. Function)

- Como podemos criar um gráfico para compreender a distribuição dos valores do IDH dos países em 2022 (coluna `"idh"` da nossa base) usando a função `ecdfplot`?

<br><br>
</div>
<div style="margin: auto;">
<br><br>



</div>
</div>

---

<div class="columns">
<div style="margin: auto;">

## ECDF (Empirical Cum. Dist. Function)

- Como podemos criar um gráfico para compreender a distribuição dos valores do IDH dos países em 2022 (coluna `"idh"` da nossa base) usando a função `ecdfplot`?
  * Como interpretamos esse gráfico e quais são as suas limitações?

</div>
<div style="margin: auto;">
<br><br>

![w:700](ecdf_idh.png)

</div>
</div>

---

<div style="margin: auto;">

![w:900](ecdf.001.png)

</div>

---

<div style="margin: auto;">

![w:900](ecdf.002.png)

</div>


---

<div style="margin: auto;">

![w:900](ecdf.003.png)

</div>

---

<div style="margin: auto;">

![w:900](ecdf.004.png)

</div>

---

<div style="margin: auto;">

![w:900](ecdf.005.png)

</div>

---

<div style="margin: auto;">

![w:900](ecdf.001.png)

</div>

---

## A divisão de uma distribuição em quartis

- Vamos trabalhar com as idades de 12 pessoas.
- `Idade`: 22, 24, 25, 28, 30, 35, 40, 42, 45, 50, 54, 60.
* **Quartis como "partes" da distribuição de valores**:
  * Agora vamos dividir essa distribuição em quatro partes:

<br>
<div class="columns" style="grid-template-columns: auto auto auto auto; gap: 5rem;">

<div>

* **1º Quartil**
  -  22
  -  24
  -  25

</div>
<div>

* **2º Quartil**
  -  28
  -  30
  -  35

</div>
<div>

* **3º Quartil**
  -  40
  -  42
  -  45

</div>
<div>

* **4º Quartil**
  -  50
  -  54
  -  60

</div>
</div>

---

## A divisão de uma distribuição em quartis

- `Idade`: 22, 24, 25, 28, 30, 35, 40, 42, 45, 50, 54, 60.
* **Quartis como fronteiras entre as partes**:
  * Por vezes usamos o termo "quartil" para designar as **3 fronteiras** entre as partes da nossa distribuição:
    * **Q1**: divide o 1º quartil do 2º quartil. Ou seja, 25% dos casos estão abaixo desse valor.
    * **Q2**: divide o 2º quartil do 3º quartil. Abaixo desse valor teríamos metade dos casos, ou seja, **Q2 é a mediana**.
    * **Q3**: divide o 2º quartil do 3º quartil. Ou seja, 75% dos casos estão abaixo desse valor (e 25% estão acima).

---

## Intervalo Interquartil

- O intervalo interquartil ($IQR$) é dado pela distância entre $Q1$ e $Q3$. Ou seja:

<br>

$$IQR = Q3 - Q1$$

<br>

- O $IQR$ é importante porque ele nos dá uma medida do grau de dispersão da nossa distribuição, tomando como base os casos "centrais", ou seja, os valores que estão em torno da nossa mediana.

---

<div style="margin: auto;">

![w:900](ecdf.005.png)

</div>

---

