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

# Bases de dados e tipos de variáveis | Countplot
**Programação para Advogados – 2024.2**
José Luiz Nunes e Lucas Thevenard

---

<!-- 
paginate: true 
header: Aula 2 - Bases de dados e tipos de variáveis | Countplot
footer: jose.luiz@fgv.br | lucas.gomes@fgv.br | 12/08/2024
-->

## Roteiro de Aula
- Bases de dados e tipos de variáveis
- A sintaxe do countplot
- Aula prática: vamos programar!
  - Preparação: configuração do VS Code
  - Nosso primeiro gráfico
- Exercício

---

## Bases de dados e tipos de variáveis

- O que é uma base de dados?
  * Dados estruturados e não estruturados
  * Dados tabulares (tabela)
  * Como organizar dados tabulares?
    * Conceito de **tidy data**


---

## Tidy Data

- **Conceito**: alinhamento entre a estrutura dos dados e sua semântica (significado).
- **Regra centrais**:
  * Linhas são observações
  * Colunas são variáveis
  * Apenas uma unidade de observação (ou de análise) por tabela

---

## Tidy Data

![](tidy_data.webp)

---

## Tidy Data

- Vamos construir um exemplo com uma tabela de alunos da sala.
  - **Unidade de observação**: Alunos
  - **Variáveis**: Nome, Matrícula, Altura, Ano de Nascimento, Signo, Cor Favorita
* Como construir uma tabela de jurisprudência no escritório?

---

### O Ciclo da Ciência de Dados

<br>
<div style="margin: 0 auto">

![w:800](ciclo.png)

</div>

---


![bg](section_bg.png)

<div style="text-align: center">

# Vamos para o código

</div>

---

### Bibliotecas para dados e visualizações

<br>
<div style="margin: 0 auto">

![w:600](imports.png)

</div>

---

### Carregar os dados da aula

<br>
<div style="margin: 0 auto">

![w:800](pd_read_csv.png)

</div>

---

### Dados de pagamentos dos cartões presidenciais

<br>
<div style="margin: 0 auto">

![](tabela_cartoes.png)

</div>

---

## Dicionário dos dados

- **data_pgto**: a data em que o pagamento foi realizado, no formato YYYY-MM-DD.
- **ano**: O ano em que a transação foi realizada, como número inteiro.
- **mes**: O mês em que a transação foi realizada, como número inteiro (1 = Janeiro, 2 = Fevereiro, etc).
- **forma_pagamento**: A forma de pagamento utilizada, que pode ser `"Crédito"` ou `"Débito"`.
- **valor**: O valor do pagamento realizado, em reais brasileiros (R$), como número decimal.

---

## Dicionário dos dados

- **tipo_despesa**: A classificação orçamentária da despesa detalhada.
- **nome_fornecedor**: A razão social ou nome do favorecido.
- **cpf_servidor**: Os 6 últimos dígitos, antes do código verificador, do Cadastro de Pessoa Física (CPF) do agente suprido (que realizou o pagamento).
- **mandato**: Identifica o mandato no qual aconteceu o pagamento.
- **posicao_mandato**: Variável numérica que representa a ordem do mandato no qual aconteceu o pagamento.

---

### Vamos aprender a fazer o nosso primeiro gráfico

---


<div class="columns">
<div>

## Primeiro Gráfico

- Contagem do uso das duas formas de pagamento: Crédito vs. Débito.
* Usamos a função `sns.countplot()`
  * `data=cartoes`: definimos qual DataFrame (dados) usar.
  * `x="forma_pagamento"`: qual coluna/variável dos dados queremos plotar, em qual eixo.

</div>
<div>
<br>

![w:600](count_forma_pagamento.png)

</div>
</div>

---

### Como poderíamos inverter os eixos do gráfico?

---

<div class="columns">
<div>

## Eixo invertido

- Invertemos os eixos definindo a função com a variável de contagem no eixo y.
  - Para isso usamos o argumento `y="forma_pagamento"` na função `sns.countplot()`.
  * Em que casos faz sentido fazer isso?

</div>
<div>
<br>

![w:600](count_forma_pagamento_invert.png)

</div>
</div>

---

<div class="columns">
<div>

## Problema dos nomes sobrepostos no eixo x

- Um problema comum é termos a sobreposição dos nomes. Isso ocorre quando temos
  - **Muitas categorias**.
  - **Nomes longos** das categorias.
- Veja ao lado o que ocorre quando tentamos plotar os mandatos no eixo x.

</div>
<div>
<br>

![w:600](count_mandatos_sobreposicao.png)

</div>
</div>

---

<div class="columns">
<div>

## Invertendo os eixos eliminamos a sobreposição

- Uma forma simples de eliminar o problema das sobreposições é inverter os eixos.
* Agora responda:
  - **Em qual mandato houve o maior gasto no cartão presidencial?**


</div>
<div>
<br>

![w:600](count_mandatos.png)

</div>
</div>

---

<div class="columns">
<div>

## Cruzando duas variáveis

- Podemos usar o argumento `hue` para cruzar duas variáveis.
- Veja ao lado o número de transações de cada presidente por forma de pagamento.


</div>
<div>

![w:600](count_mandatos_forma.png)

</div>
</div>

---

### Ainda podemos melhorar esse gráfico...

<br>
<div class="columns">
<div>


![w:500](code_count_avancado.png)

</div>
<div>


![w:600](plot_count_avancado.png)

</div>
</div>

---

### Agora mãos à obra!

---

## Config do Visual Studio Code

<div class="columns">
<div style="margin:auto">

![w:400](config_vscode.png)

</div>
<div>
<br><br>

- **Guia de Configuração do VS CODE**
  - Disponível no EClass
  - Link de acesso: [bit.ly/config_vscode](bit.ly/config_vscode)

</div>
</div>