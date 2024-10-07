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

# Scatterplot e regplot: relações entre variáveis numéricas
**Programação para Advogados – 2024.2**
José Luiz Nunes e Lucas Thevenard

---
<!-- 
paginate: true 
header: Scatterplot e regplot: relações entre variáveis numéricas
footer: jose.luiz@fgv.br | lucas.gomes@fgv.br | 07/10/2024
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

- Scatterplot
- Regplot
  - O que é um modelo?
- Anotações em gráficos

---

### Passos Preliminares

<div style="margin: auto;">

![w:700](passos_preliminares.png)

</div>

---

<div style="margin: auto;">

![w:700](scatter_1.png)

</div>

---

## Convenção dos eixos

- Usualmente colocamos a variável que queremos entender/prever/explicar no **eixo y**.
  * Chamamos ela de "**variável de resposta**" ou "**variável dependente**".

* A variável utilizada para explicar o fenômeno é usualmente colocada no **eixo x**.
  * Chamamos ela de "**variável explicativa**" ou "**variável independente**".

---

<div class="columns">
<div style="margin: auto;">

## Scatterplot

- O gráfico ao lado é um scatterplot que relaciona a expectativa de vida dos países (eixo y) à expectativa de escolaridade (eixo x).
  * Qual é a relação entre essas variáveis evidenciada pelo gráfico mostra?

</div>
<div style="margin: auto;">
<br><br>

![w:700](scatter_1.png)

</div>
</div>

---

<div style="margin: auto;">

![w:700](corr.png)

</div>

---

## Cuidado: correlação ≠ causalidade

- O gráfico parece suportar a ideia de que quando aumentamos a expectativa de escolaridade de um país a expectativa de vida aumenta daquela população aumenta.
- No entanto essa conclusão é precipitada!
  * Quais outras explicações podemos ter?
    * **Hipótese rival 1**: A direção da causalidade é a inversa: é o aumento da expectativa de vida que causa aumento da escolaridade.
    * **Hipótese rival 2**: Há uma terceira variável que está causando tanto o aumento da expectativa de vida como de escolaridade.
    * **Hipótese rival 3**: Não há nenhuma relação real entre esas variáveis. A correlação observada é fruto do acaso (correlação espúria).

---

<div class="columns">
<div style="margin: auto;">

![w:700](spurious2.png)

</div>
<div style="margin: auto;">
<br>

#### [www.tylervigen.com](https://www.tylervigen.com/spurious-correlations)
<br><br>

![w:700](spurious1.png)

</div>
</div>

---

<div style="margin: auto;">

![w:600](reg_1.png)

</div>

---

<div style="margin: auto;">

![w:1200](reg_2w.png)

</div>

---

<div style="margin: auto;">

### A reta como um modelo

![w:800](replot.001.png)

</div>

---

<div style="margin: auto;">

### A reta como um modelo

![w:800](replot.002.png)

</div>

---

<div style="margin: auto;">

### A reta como um modelo

![w:800](replot.003.png)

</div>

---

<div style="margin: auto;">

### A reta como um modelo

![w:800](replot.004.png)

</div>

---

<div style="margin: auto;">

### A reta como um modelo

![w:800](replot.005.png)

</div>

---

<div style="margin: auto;">

### A reta como um modelo

![w:800](replot.006.png)

</div>

---

### A reta como um modelo

A reta de tendência que encontramos e sua a equação podem ser entendidas também como um **'modelo linear'**, por meio do qual podemos estimar os valores da nossa variável de resposta (expectativa de vida) a partir de variáveis explicativas (nesse caso só temos uma: a expectativa de escolaridade).

Quando você ouvir a expressão "modelo" referindo-se a modelagem matemática, estatística, econômica, etc., não se assuste. **O modelo nada mais é do que uma ou mais equações matemáticas utilizadas para descrever relações entre variáveis e, a partir disso, fazer previsões ou estimativas**.

---


<div style="margin: auto;">

![w:1200](reg_3w.png)

</div>

---

## Primeiro exemplo de anotação

- Vamos destacar a posição do Brasil no nosso scatterplot de Expectativa de vida x Expectativa de escolaridade. Para isso, começamos criando uma nova variável que utilizaremos para colorir o ponto do Brasil.

<div style="margin: auto;">

![w:800](anot_1.png)

</div>

---

## Primeiro exemplo de anotação

<div style="margin: auto;">

![w:1200](anot_2.png)

</div>

---

## Primeiro exemplo de anotação

Precisamos agora das coordenadas do Brasil no gráfico, para adicionar uma anotação próxima ao ponto. O código abaixo obtém essas coordenadas, acrescidas de um pequeno espaço para evitar sobreposições.

<div style="margin: auto;">

![w:800](anot_3.png)

</div>

---

## Primeiro exemplo de anotação

<div style="margin: auto;">

![w:1200](anot_4.png)

</div>

---

<div style="margin: auto;">

![w:1200](anot_5.png)

</div>

---

### Mãos à obra!