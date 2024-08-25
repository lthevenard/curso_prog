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

# Histplot: Conhecendo o formato de uma distribuição de valores 
**Programação para Advogados – 2024.2**
José Luiz Nunes e Lucas Thevenard

---
<!-- 
paginate: true 
header: Histplot: Conhecendo o formato de uma distribuição de valores 
footer: jose.luiz@fgv.br | lucas.gomes@fgv.br | 19/08/2024
-->

## Roteiro da Aula
- O que é um histograma?
* Base de dados: IDH
* Criando o histograma no Python
  - Função `histplot()`
  - Formato de distribuições
* Mudando textos do gráfico

---

<div class="columns">

<div>

## O que é um histograma?

- A tabela ao lado mostra a altura de 15 alunos. Como podemos representar graficamente os intervalos de valor mais representativos?
* Vamos contar o número de alunos que aparecem em cada faixa de valor.

</div>

<div style="margin:auto 0 auto auto">

![width:300](altura_dos_alunos.png)

</div>


</div>

---

<div class="columns">

<div style="margin: auto">

## O que é um histograma?

![](alunos_7bins.png)

</div>

<div style="margin:auto 0 auto auto">

![width:300](altura_dos_alunos_7bins.png)

</div>

</div>

---

<div class="columns">

<div style="margin: auto">

## O que é um histograma?

![](alunos_4bins.png)

</div>

<div style="margin:auto 0 auto auto">

![width:300](altura_dos_alunos_4bins.png)

</div>

</div>

---

<div class="columns">

<div style="margin: auto">

## O que é um histograma?

<br>

- E se dividíssemos os alunos em 30 intervalos diferentes de altura?
- O que você acha que aconteceria com o gráfico nesse caso?

<br>

</div>

<div style="margin:auto 0 auto auto">

![width:300](altura_dos_alunos.png)

</div>

</div>

---

<br>

<div style="margin:auto">

![w:700](alunos_30bins.png)

</div>

---

### Alternativas ao histograma: density plot e ECDF

<br>

<div class="columns">

<div style="margin:auto">

![w:550](alunos_density.png)

</div>

<div style="margin:auto">

![w:550](alunos_ecdf.png)

</div>

</div>

---

## Vamos aos dados de hoje: IDH

- Hoje vamos trabalhar com uma base de dados nova, uma base que tem informações do Índice de Desenvolvimento Humano (IDH).
* Antes vamos recordar um pouco da importância de trabalharmos com dados em formato **tidy**.
  * **Tidy**: Observações nas linhas, variáveis nas colunas, unidade de análise fixa!
  * Vamos ver como os dados do IDH foram disponibilizados:
    - Excel: 
    - CSV: 



