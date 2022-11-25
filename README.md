# Análise de tweets em perfis no Twitter

<div align="justify">

<img align="right" width="100" height="100" src="img/twitter_icon.png">

<div style="display: inline-block;">
<img src="https://img.shields.io/badge/c++-%2300599C.svg?style=for-the-badge&logo=c%2B%2B&logoColor=white"/> 
<img src="https://img.shields.io/badge/Visual_Studio_Code-0078D4?style=for-the-badge&logo=visual%20studio%20code&logoColor=white"/> 
</a> 
</div>

## 1. Grafos

A ideia básica de grafos surgiu com o matemático Leonhard Euler no século XVIII (1735). Ele usou grafos para resolver o famoso problema das 7 pontes de Konigsberg.


<div align="center">
 <p> </p>
 <img src="img/cidade.webp">
  <p> </p>
 <figcaption>Configuração das pontes na cidade de Königsberg. </figcaption>
 <p> </p>
</div>

> *A cidade de Königsberg, na Prússia, foi definida em ambos os lados do rio Pregel , e incluía duas grandes ilhas — Kneiphof e Lomse — que estavam conectadas entre si, ou às duas porções continentais da cidade, por 7 pontes. O problema era planejar um passeio pela cidade que cruzasse cada uma dessas pontes uma vez e apenas uma vez.*

A solução de Euler foi primeiro remover tudo que fosse irrelevante ao problema, ou seja, remover as cidades próximas, ruas conectadas e deixou apenas o que precisava em vértices que se ligavam baseado nas rotas possíveis. Isso permitiu a ele formular o problema de forma abstrata, iniciando o que temos hoje em teoria dos grafos.

Por que é necessário saber teoria dos grafos? Para responder esta pergunta, utilizaremos um exemplo de aplicação muito comum atualmente. Suponha que um ponto representa uma pessoa, e que linhas entre esses pontos representam relações juntando pares de pessoas que você segue. Então no final para cada pessoa que você seguir vai ter uma ligação. Se for analisado o perfil de uma das pessoas que você segue, ela tem um conjunto de pessoas que também segue outros. Algo que poderia ser usado com esse grafo, é recomendar seguidores. Essa lógica é usada para a maioria das redes sociais!
