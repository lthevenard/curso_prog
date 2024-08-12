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

# Gráficos de barras - Variáveis categóricas X numéricas

**Programação para Advogados – 2024.2**
José Luiz Nunes e Lucas Thevenard

---

<!-- 
paginate: true 
header: Aula 2 - Bases de dados e tipos de variáveis | Countplot
footer: jose.luiz@fgv.br | lucas.gomes@fgv.br | 12/08/2024
-->

## Revisão

- O que vimos até aqui?
- Que tipo de gráfico o countplot gera?
- Quais tipos de variáveis estavam sendo usadas?

---

<div class="columns">
<div>

## Revisão

- Gráficos são "representações geométricas dos dados"
* Qual atributo dos dados esta sendo representado?


</div>
<div>

<br>

![w:600](../aula2/count_forma_pagamento.png)

</div>
</div>

---


<div class="columns">
<div>

## Revisão

- Gráficos são "representações geométricas dos dados"
- Qual atributo dos dados esta sendo representado?
  - Eixo X - Categorias (barras diferentes)
  - Eixo Y - Contagem (altura das barras)


</div>
<div>
<br>

![w:600](../aula2/count_forma_pagamento.png)

</div>
</div>

---

<div class="columns">
<div>

## Revisão

- Gráficos são "representações geométricas dos dados"
- Qual atributo dos dados esta sendo representado?
  - Eixo X - Categorias (barras diferentes)
  - Eixo Y - Contagem (altura das barras) - **aqui o seaborn criou uma variável numérica para nós!**


</div>
<div>
<br>

![w:600](../aula2/count_forma_pagamento.png)

</div>
</div>

---

<div class="columns">
<div>

## Revisão

- Gráficos são "representações geométricas dos dados"
- Qual atributo dos dados esta sendo representado?
  - Eixo X - Categorias (barras diferentes)
  - Eixo Y - Contagem (altura das barras) - **aqui o seaborn criou uma variável numérica para nós!**


</div>
<div>
<br>

![w:600](../aula2/count_forma_pagamento.png)

</div>
</div>

---

<div class="columns">
<div>

## Revisão

- Gráficos são "representações geométricas dos dados"
- Qual atributo dos dados esta sendo representado?
  - Eixo X - Categorias (barras diferentes)
  - Eixo Y - Contagem (altura das barras) - **aqui o seaborn criou uma variável numérica para nós!**


</div>
<div>
<br>

![w:600](../aula2/count_forma_pagamento.png)

</div>
</div>

---

![bg](section_bg.png)

<div style="text-align: center">

# Mas e se quisermos representar algo além de uma contagem?

</div>

---

## Gráficos de barras

- Barras representam em um eixo uma variável categórica e no outro uma variável numérica
- O countplot cria um gráfico de barras. Mas limitado a uma "função de agregação": contagem
- Para outras funções de agregação, usamos o `barplot`: e.g. soma e média

---

## Gráficos de barras

- Nossas observações devem ter: 
  - Uma variável categórica
  - Uma variável numérica
- Podemos também ter outras variáveis categóricas para segmentar o gráfico (i.e. cor pelo `hue`)

---

## Gráficos de barras

- No gráfico de barras a altura da barra é a codificação de nossa variável numérica
- Devemos manter a relação de seu formato com o valor representado
  - Exemplo: gráficos de barra sempre devem começar em 0!

---

## Um exemplo de gráfico $missleading$

<br>

- ADICIONAR IMAGEM!!

---

## Voltando aos dados

- Quais variáveis numéricas temos disponíveis?

<br>
<div style="margin: 0 auto">

![](../aula2/tabela_cartoes.png)

</div>

---

## Voltando aos dados

- ``"Ano"``, `"mes"`, e `"posicao_mandato"` são variáveis numéricas?

<br>
<div style="margin: 0 auto">

![](../aula2/tabela_cartoes.png)

</div>

---

## Teste

- 