# Mineração de Regra de Associação

Este mini projeto é referente ao capítulo 04 chamado de "Big Data na prática 3", referente ao curso Big Data Analytics with R e Microsoft Azure Machine Learning na Data Science Academy.

Ao invés de utilizar a conexão no banco de dados SQL Lite conforme instrução da DSA, eu fiz a conexão e depois exportei os data frames para CSV utilizando a funcão "write.csv" e posteriormente carregar todos os dados através desses arquivos, assim não é mais necessário utilizar o banco de dados SQL Lite para executar este projeto.

Obs.: Alguns arquivos '.CSV' não puderam ser carregados, devido ao seu tamanho, então é necessário fazer o download no link abaixo.
____________________________________________________________________________________________________________________________________

Utilizando o dataset oferecido pelo Kaggle: https://www.kaggle.com/hugomathien/soccer, vamos analisar dados de clubes de futebol, usando a linguagem estatistica R.

Embora tenha mais de 20 anos, o Market Basket Analysis (MBA) (ou Mineração de Regras de Associação) ainda pode ser uma técnica muito útil para obter insights em grandes conjuntos de dados transacionais. 

O exemplo clássico são dados transacionais em um supermercado. Para cada cliente, sabemos quais são os produtos individuais (itens) que ele colocou na cesta e comprou. Outros casos de uso para o MBA podem ser dados de clique da web, arquivos de log e até questionários.

Com a análise de cesta de compras, podemos identificar itens que são frequentemente comprados juntos. 
Normalmente, os resultados de um MBA são apresentados sob a forma de regras. 
As regras podem ser tão simples quanto {A ==> B}, quando um cliente compra o item A então é (muito) provável que o cliente compre o item B. Regras mais complexas também são possíveis {A, B ==> D, F}, quando um cliente compra os itens A e B, é provável que ele compre os itens D e F.

Neste mini projeto, vamos buscar a associação entre os clubes de futebol da Europa e responder a pergunta:

Quais clubes mais realizam transações de compra e venda de jogadores, entre si?

O dataset contêm cerca de 25.000 partidas de onze ligas de futebol europeias a partir da temporada 2008/2009 até a temporada 2015/2016. 

Depois de realizar o trabalho de Data Wrangling, vamos gerar um conjunto de dados transacionais adequado para análise de cesta de compras.

Portanto, não temos clientes, mas jogadores de futebol, e não temos produtos, mas clubes de futebol. 

No total, o conjunto de dados transacionais de futebol contém cerca de 18.000 registros. 
Obviamente, esses registros não incluem apenas as transferências multimilionárias cobertas pela mídia, mas também todas as transferências de jogadores que ninguém nunca ouviu falar.

# Como vamos aplicar o MBA?

Em R você pode usar o pacote arules para mineração de regras de associação / MBA. 
Alternativamente, quando a ordem das transações é importante, você deve usar o pacote arulesSequences. 
Depois de executar o algoritmo, obteremos alguns resultados interessantes. 
  
Por exemplo: neste conjunto de dados, a transferência mais frequente é da Fiorentina para o Gênova (12 transferências no total). Vamos imprimir a tabela com todos os resultados ao final do processo.

# Visualização de gráfico de rede

Todas as regras que obtemos da mineração de regras de associação formam um gráfico de rede. 
Os clubes de futebol individuais são os nós do gráfico e cada regra "de ==> para" é uma aresta (edge) do gráfico de rede.

Em R, os gráficos de rede podem ser visualizados bem por meio do pacote visNetwork.
