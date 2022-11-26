# Análise de tweets em perfis no Twitter

<div align="justify">

<img align="right" width="100" height="100" src="img/twitter_icon.png">

<div style="display: inline-block;">
<img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/> 
<img src="https://img.shields.io/badge/Visual_Studio_Code-0078D4?style=for-the-badge&logo=visual%20studio%20code&logoColor=white"/>
<img src="https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white"/>
</a> 
</div>

## 1. Grafos

A ideia básica de grafos surgiu com o matemático Leonhard Euler no século XVIII (1735). Ele usou grafos para resolver o famoso problema das 7 pontes de Konigsberg.


<div align="center">
 <p> </p>
 <img src="img/cidade.webp">
  <p> </p>
 <figcaption>Figura 1: Configuração das pontes na cidade de Königsberg</figcaption>
 <p> </p>
</div>

> *A cidade de Königsberg, na Prússia, foi definida em ambos os lados do rio Pregel, e incluía duas grandes ilhas — Kneiphof e Lomse — que estavam conectadas entre si, ou às duas porções continentais da cidade, por 7 pontes. O problema era planejar um passeio pela cidade que cruzasse cada uma dessas pontes uma vez e apenas uma vez.*

A solução de Euler foi primeiro remover tudo que fosse irrelevante ao problema, ou seja, remover as cidades próximas, ruas conectadas e deixou apenas o que precisava em vértices que se ligavam baseado nas rotas possíveis. Isso permitiu a ele formular o problema de forma abstrata, iniciando o que temos hoje em teoria dos grafos.

<div align="center">
 <p> </p>
 <img src="img/grafos ponte.webp">
  <p> </p>
 <figcaption>Figura 2: Visualização de grafos utilizando o problema das 7 pontes de Konigsberg. </figcaption>
 <p> </p>
</div>

Por que é necessário saber teoria dos grafos? Para responder esta pergunta, utilizaremos um exemplo de aplicação muito comum atualmente. Suponha que queiramos descobrir o assunto do momento de um determinado grupo de pessoas. Esse grupo de pessoas será baseado nos seguidores de um perfil específico e também nos seguidores destes seguidores. Dessa forma, podemos entender os tópicos que estão em alta naquele momento dentro de uma bolha de seguidores.

<div align="center">
 <p> </p>
 <img src="img/ilustracao.png">
  <p> </p>
 <figcaption>Figura 3: Ilustração da rede de seguidores</figcaption>
 <p> </p>
</div>

### 1.1 Networkx

NetworkX é uma biblioteca Python para estudar grafos e redes. Esta é uma demonstração de código para mostrar como usamos o NetworkX para conduzir a comparação de subgráficos e manipulamos os parâmetros para desenhar os grafos.

Grafos em networkX podem ser criados de algumas maneiras diferentes:

- Podemos carregar um grafo de um arquivo contendo uma lista de adjacências.
- Podemos carregar um grafo de um arquivo contendo uma lista de arestas (edge list).
- Podemos criar um grafo a partir de uma matriz de adjacência.
- Podemos criar um gráfico a partir de um dataframe do pandas.
- Podemos criar um grafo vazio e adicionar os vértices e arestas um a um ou a partir de uma lista.
- Finalmente, alguns gráficos especiais (gráficos completos, gráficos bipartidos completos, …) podem ser criados usando funções especiais.

## 2. Twitter

> Twitter é uma plataforma para as pessoas conversarem sobre assuntos do momento, um lugar que cria uma audiência muito engajada, que fica ao nosso alcance — seja por meios orgânicos ou anúncios pagos.

Jenny Broekemeier, Gerente de Mídias Sociais Pagas da MANSCAPED, Inc.

Trata-se de uma rede social, bastante difundida, onde seu usuário poder realizar publicações, chamados de tweets que podem conter, textos, imagens, vídeos, hiperlinks ou todos deles integrados. Essas publicações podem ser visualizadas por diversos usuários e que eventualmente poderão republicar aquela "mensagem" em uma operação conhecida como retweet.

### 2.1 API

Para consumir dados do Twitter, não é necessário ter acesso aos servidores e bancos de dados internos do Twitter, também não é preciso entender como o Twitter é codificado. É necessário um intermediário entre o usuário e o back-end do Twitter, um intermediário em que o clinte pode solicitar (com alguns parâmetros) para obter alguns dados ou interagir com os serviços do Twitter. Em poucas palavras, uma API é isso: simplesmente uma junção entre dois aplicativos independentes que se comunicam entre si. Como abstração, a API do Twitter simplifica a integração com terceiros (desenvolvedores, aplicativos, outras APIs, etc.).


<div align="center">
 <p> </p>
 <img src="img/API twitter.png">
   <p> </p>
 <figcaption>Figura 4: Funcionamento da API.</figcaption>
 <p> </p>
 <p> </p>
</div>

Aqui está o que se pode fazer com a API do Twitter:

- Pesquisar tweets programaticamente com base em hashtags, palavras-chave, geolocalização, etc.
- Criar bots do Twitter que retuitam automaticamente uma lista de contas predefinidas
- Transmitir tweets em tempo real com base em uma série de filtros
- Seguir automaticamente uma lista de usuários
- etc.

Logo, a API permite que você execute programaticamente qualquer ação que executaria manualmente na interface.

## 3. Social network analysis ou Análise de rede social
 
A noção de rede social refere-se historicamente à abordagem estrutural de estudo dos grupos sociais. O conceito, que tem suas raízes na Sociologia há quase um século, principalmente através do trabalho do Jakob Moreno, ainda na década de 30, que sistematicamente coletou e analisou as interações sociais de alunos de escolhas, é uma das principais bases do que ele chamava de Sociometria. Na base, rede social significava a visão de um grupo social através de suas relações, considerando o grafo (estrutura de rede) como construto para tal.


<div align="center">
 <p> </p>
 <img src="img/evolucao de grupos.jpeg">
  <p> </p>
 <figcaption>Figura 4: Um dos grafos originais do Moreno, do livro "Who shall survive" (1934). </figcaption>
 <p> </p>
</div>

 Outros autores, depois de Moreno, também se apropriaram do conceito para seus estudos e setaram outras bases para o que depois veio a se tornar a Análise de Redes Sociais. Mas foi apenas na década de 90 que aconteceu uma mudança radical: Com o surgimento da mídia digital e a transformação das interações sociais em dados, novas formas de estudar esses grupos sociais, principalmente de forma mais massiva (a análise de redes sociais era feita com trabalho de coleta de dados mais "formiguinha" até então). Essa nova abordagem, muito mais interdisciplinar, vai ser inaugurada por autores como Barabási e Christakis, entre outros, e notadamente, vai também originar outras novas "subáreas" de estudo em áreas que tradicionalmente não estudavam dados sociais (como a Ciência Social Computacional, por exemplo).
 
Quando transformamos essa discussão para as redes sociais online ou as redes sociais na internet, o que temos é uma mudança importante entre uma estrutura mediada principalmente pelas relações institucionais e interpessoais e uma estrutura mediada pelas relações mediadas pela tecnologia digital. Eu costumo dizer que, nessa mudança, essas redes ganham “superpoderes”, tais como:

- A possibilidade de conexão mais “individual” e por interesse, não limitada pela localização geográfica;
- A posssibilidade de conexões massivas, em grande escala (uma vez que essas conexões podem ser mantidas pelas ferramentas sem a necessidade de interação social), assim permitindo que as pessoas tenham centenas ou milhares de “amigos” — o fenômeno dos “influenciadores”, por exemplo;
- A possibilidade de participação em conversações globais e de acesso a conteúdos que não necessariamente estariam disponíveis devido à complexificação das conexões sociais;
- A possibilidade de ser alguém diferente, ter mais de um “perfil”, brincar com a própria identidade (o que também possibilita que coisas que não poderiam ser atores em redes sociais offline, como um perfil robô, por exemplo, agora possam ser).

Logo, de acordo com a Wikipédia,

> “A análise de redes sociais (SNA) é o processo de investigação de estruturas sociais por meio do uso de redes e teoria dos grafos. Caracteriza as estruturas em rede em termos de nós (atores individuais, pessoas ou coisas dentro da rede) e os laços, arestas ou links (relacionamentos ou interações) que os conectam.

Ele entrou em praticamente todos os campos - novamente, de acordo com a Wikipedia:

> “A análise de redes sociais emergiu como uma técnica chave na sociologia moderna. Também ganhou seguidores significativos em antropologia, biologia, demografia, estudos de comunicação, economia, geografia, história, ciência da informação, estudos organizacionais, ciência política, saúde pública, psicologia social, estudos de desenvolvimento, sociolinguística e ciência da computação e agora é comumente disponível como uma ferramenta de consumo (consulte a lista de software SNA).”

## 4. O Algoritmo

### 4.1 Problema Proposto 

Neste trabalho o objetivo é aplicar as estruturas em grafos para solucionar um problema real qualquer. Cada dupla de alunos deve escolher em literatura uma das áreas de aplicação do tema e propor uma solução baseada nos conceitos apresentados. Essa solução pode ser realizada utilizando C, C++ e/ou Python. O objetivo e mostrar a atuação de algoritmos clássicos em grafos na resolução de problemas emergentes. Alguns temas para inspiração são: Análise de rede social, rotas de entregas, análise de trafego (i.e., carros, pacotes na internet, etc), mínima quantidade de saltos em redes, teoria dos jogos, elaboração de horário vs rodízio de salas, envoltória convexa (do inglês, convex hull), etc.

Desta forma, o seguinte trabalho consiste em:

1) Usar o Tweepy para raspar o Twitter para todos os meus seguidores e (a maioria) de seus seguidores;
2) Criar um DataFrame pandas de todas essas conexões;
3) Usar o NetworkX para extrair uma rede desses dados e executar algumas análises básicas de rede;
4) Visualizar a rede no Gephi.
5) A partir do usuário com maior numero de conexões, extrair os 20 tweets mais recentes de cada um de seus seguidores;
6) Tratar estes tweets utilizando regex, codecs e nltk, para respectivamente, excluir dados estranhos(pontuação, espaço duplo, linha vazia, emojis, links, etc), salvar com codificação utf-8(manter acentos) e remover stopwords;
7) Utilizando os tweets tratados, criamos nós com palavras únicas, e ligamos essas palavras através de arestas com as outras palavras do tweet;
8) A cada repetição de palavra e aresta adicionamos um valor ao item referente a estes, e no final plotamos o grafo usando o matplotlib.

### 4.2 Instalação

Para rodar este código, é necessário instalar as bibliotecas a seguir.

```
pip3 install networkx
pip3 install codecs
pip3 install nltk
pip3 install tweepy
pip3 install community
pip3 install python-louvain
pip3 install ipython

nltk.download('stopwords')
nltk.download('punkt')
```

### 4.3 Estrutura do algoritmo

Irei explicar as etapas que segui para extrair dados do Twitter. Em primeiro lugar, você deve obter as credenciais da API do Twitter no site do desenvolvedor do Twitter, que são a chave da API, a chave secreta da API, o token de acesso e o segredo do token de acesso.

#### 4.3.1 Criação de um aplicativo do Twitter e configurção das credenciais

Para poder reproduzir as etapas a seguir é necessário ter uma conta no Twitter. Para usar a API do Twitter, primeiro precisa-se registrar como desenvolvedor do Twitter, no site dos desenvolvedores. Uma vez registrado, e necessário criar um aplicativo do Twitter que irá configurar um monte de credenciais: essas credenciais serão usadas posteriormente pela biblioteca Tweepy para autenticação.

<div align="center">
 <p> </p>
 <img src="img/twitter - API.png">
  <p> </p>
 <figcaption>Figura 5: Portal do desenvolvedor do Twitter. </figcaption>
 <p> </p>
</div>

#### 4.3.2 Conexão à API do Twitter

Para começar, constrói-se uma rede usando minha conta pessoal no Twitter (@_Pablitoss_). Para fazer isso, inicia-se com uma lista de todos os seguidores (atualmente 47 seguidores). Em seguida, obtém-se todos os seguidores dessas 47 contas. Para economizar tempo, para contas com mais de 5.000 seguidores, irá se raspar apenas as primeiras 5.000 contas.

Primeiro, importa-se os pacotes Tweepy e Pandas.

https://github.com/barbrina/AEDs-II/blob/7d3954f73d13c52d913bbdebae227a7f303ae8b2/Analisando%20conex%C3%B5es%20do%20Twitter/src/twitter.py#L5-L6

Em seguida, insere-se a credenciais da API do Twitter retiradas na sessão **Criação de um aplicativo do Twitter e configurção das credenciais**.

```
consumer_key = info['API_ACCESS']
consumer_secret = info['API_ACCESS_SECRET']
access_key = info['ACCESS_TOKEN']
access_secret = info['ACCESS_TOKEN_SECRET']
```

Com o Tweepy, poderá ser usada essas credenciais para conectar à API do Twitter e começar a baixar os dados. O código a seguir usa apenas as credenciais inseridas acima para se conectar a ela. Como irei fazer o download de grandes conjuntos de dados, é importante especificar alguns parâmetros quando inicializarei a API. Definimos ‘wait_on_rate_limit’ como True. Existem limites de taxa ao baixar dados do Twitter - só se pode fazer um número limitado de solicitações de download para a API em um determinado período de tempo. Ao definir esse parâmetro como True, não interromperei a conexão com a API quando atingirmos esses limites. Em vez disso, esperarei até que o tempo limite termine e eu possa continuar baixando os dados.

### <b>4.4 Etapa 2 - Assunto mais importante</b>

Para descobrir o assunto mais importante da rede do usuário mais influente seguimos a seguinte tática:

1) Extraímos os tweets de todos os seguidores do Usuário mais influente;
2) Tratamos esses tweets, de maneira a deixar somente palavras importantes;
3) Construímos um grafo utilizando as palavras como nós, e as vezes qe se repetiram como tamanho dos nós. As arestas são feitas das conexões entre palavras em um tweet e o peso da aresta é derivado da quantidade de vezes que essa conexão aparece;
4) São retiradas as palavras de menos importância (aparecem menos que 100 vezes) e as conexões que elas fazem;
5) Plota-se o grafo.

#### <b>4.4.1 Extração de Tweets</b>

Extraímos o id usuário mais influente do arquivo "nodes.csv";

https://github.com/barbrina/Twitter-Data-Analysis/blob/ddf123a492798b6a2c42deed7efaaea0e50ed2af/Final/Etapa2.py#L2617

Cria-se uma lista de seguidores e ela é preenchida com os seguidores do usuário mais influente;

https://github.com/barbrina/Twitter-Data-Analysis/blob/ddf123a492798b6a2c42deed7efaaea0e50ed2af/Final/Etapa2.py#L2619-L2626

A partir dos ids encontrados (excluindo-se os que possuem twitter privado), obtemos os 20 tweets mais recentes dos mesmos (a quantidade foi estabelecida como consenso geral entre o grupo de média de tweets por dia de um usuário);

https://github.com/barbrina/Twitter-Data-Analysis/blob/ddf123a492798b6a2c42deed7efaaea0e50ed2af/Final/Etapa2.py#L2628-L2641

#### <b>4.4.2 Tratamento de texto</b>

Para não ser necessária a repetição da pesquisa, já que temos limite de pesquisas, salva-se os tweets em um arquivo, com uma sequência de caracteres(;;;) no final de cada tweet, que será utilizada para quebrar os tweets depois do tratamento. E como tratamento inicial, retira-se todos os emojis do tweet com a função [deEmojify](https://gist.github.com/slowkow/7a7f61f495e3dbb7e3d767f97bd7304b?permalink_comment_id=4071933#gistcomment-4071933).     
A seguir fazemos o tratamento adicional de todos os tweets, removendo caracteres e links, e stopwords, utilizando as bibliotecas Regex e Nltk:

https://github.com/barbrina/Twitter-Data-Analysis/blob/ddf123a492798b6a2c42deed7efaaea0e50ed2af/Final/Etapa2.py#L2649-L2664

#### <b>4.4.3 Construção do grafo</b>

Utilizando a sequência de caracteres definida, quebramos os tweets em um array (*data_set=texto.split("; ; ;")*). Em seguida começamos a criar nosso grafo:

https://github.com/barbrina/Twitter-Data-Analysis/blob/ddf123a492798b6a2c42deed7efaaea0e50ed2af/Final/Etapa2.py#L2564-L2599

A classe possui as seguintes funções:

 - <font size="3"><b> \_\_init\_\_:</b></font> Responsável por criar os dicionários(serão usados como Hash) para armazenar os nós(Palavras e repetições) e as arestas(ligações de palavras e repetições);
 - <font size="3"><b>addNode(palavra):</b></font> Adiciona 10 a posição de chave **palavra** do dicionário de nós, toda vez que esta **palavra** aparece;
 - <font size="3"><b>addEdge(a,b):</b></font> Utilizando um *frozenset(a,b)* como chave(qualquer ordem das duas palavras será considerada igual), adiciona 1 a posição com esta chave toda vez que as palavras aparecem juntas;
 - <font size="3"><b>visualize:</b></font> Responsável por desenhar o grafo.

Para cada tweet presente na lista (*data_set*) percorremos o mesmo palavra por palavra, adicionando cada palavra como nó (**addNode()**) e cada par de palavra prensente no tweet como aresta (**addEdge()**);

https://github.com/barbrina/Twitter-Data-Analysis/blob/ddf123a492798b6a2c42deed7efaaea0e50ed2af/Final/Etapa2.py#L2668-L2674

A seguir utilizamos a função visualize da classe de grafo, essa função funciona da seguinte maneira:

 1) Remove nós que possuem valores abaixo de 1000 (aparecem menos de 100 vezes), e removem as arestas que possuem esses nós

 https://github.com/barbrina/Twitter-Data-Analysis/blob/ddf123a492798b6a2c42deed7efaaea0e50ed2af/Final/Etapa2.py#L2578-L2582

 2) Cria as arestas no estilo da biblioteca networkx e adiciona em ordem, os grafos da classe e as arestas criadas a partir das arestas da classe

 https://github.com/barbrina/Twitter-Data-Analysis/blob/ddf123a492798b6a2c42deed7efaaea0e50ed2af/Final/Etapa2.py#L2583-L2589

 3) Ajusta o layout da grafo (posicionamento, tamanho de nós, label de aresta)

 https://github.com/barbrina/Twitter-Data-Analysis/blob/ddf123a492798b6a2c42deed7efaaea0e50ed2af/Final/Etapa2.py#L2590-L2594

 4) Plota o grafo

 https://github.com/barbrina/Twitter-Data-Analysis/blob/ddf123a492798b6a2c42deed7efaaea0e50ed2af/Final/Etapa2.py#L2595-L2599


## 5. Conclusão

No final, com a análise de redes sociais, podemos aprender muito sobre o que acontece nas mídias sociais, como os usuários interagem e que tipo de interações estão acontecendo. Esta é uma ferramenta muito poderosa para analisar dados de mídia social e esses dados podem ser usados para moldar a forma como os usuários interagem e como eles interagem em determinados tópicos e determinados usuários. Isso pode ser benéfico especialmente ao promover algo ou construir uma marca.

O objetivo do trabalho foi cumprido, apesar de ter realizado uma análise de uma pequena amostragem de dados visto as limitações da própria API, da arquitetura do computador e o tempo para fazer o trabalho e coletar os dados. Para trabalhos futuros, seria interessante uma maior coleta de dados e mais atribuições para análise de conexões, como tweets, curtidas e menções.

## 6. Compilação e Execução 

