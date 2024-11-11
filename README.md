<h1>Projeto Fórmula 1</h1>

<hr>
<br>

Este projeto foi desenvolvido com o intuito de realizar análises e retirar insights dos dados aqui presentes. É uma base de dados bem antiga contendo informações do ano de 1950 até o ano de 2022.

<hr>
<br>

<h1>Entendo a Base de Dados</h1>

<h2>Cricuits</h2>

  Essa tabela exibe dados dos circuitos (pistas)
  
  Dentro da tabela Circuits temos as seguintes colunas:
  
  <b>circuitId</b> - Identificador dos cicuitos das corridas.
  
  <b>name</b> - Nome dos cicuitos.
  
  <b>location</b> - Localização dos circuitos (Cidade).
  
  <b>country</b> - Localização dos circuitos (País).
  
  <b>flag_url</b> - URL das imagens das bandeiras de cada país do circuito.
  
  <b>picture_url</b> URL das imagens que exibem um mapa do circuito.

<br>

<h2>Constructors</h2>

  Essa tabela exibe dados dos carros
  
  Dentro da tabela Constructors temos as seguintes colunas:

  <b>constructorId</b> - Identificador do carro
  
  <b>name</b> -  Nome (marca) do carro

  <b>nationality</b> - Nacionalidade do carro (marca)

  <b>car_url</b> - URL da imagem do carro

<br>

<h2>Drivers</h2>

  Essa tabela exibe dados dos pilotos
  
  Dentro da tabela Drivers temos as seguintes colunas:

  <b>driverId</b> - Identificador dos pilotos

  <b>fullName</b> - Nome completo dos pilotos

  <b>nationality</b> - Nacionalidade dos pilotos

  <b>picture_url</b> - URL da imagem dos pilotos

<br>

<h2>Races</h2>
  
  Essa tabela exibe dados das corridas

  Dentro da tabela Races temos as seguintes colunas:

  <b>circuitId</b> - Identificador dos circuits (Chave Estrangeira da tabela Circuits)

  <b>date</b> - Exibe as datas das corridas (Ano, Trimestre, Mês e Dia)

  <b>name</b> - Exibe o Nome do campeonato (Grand Prix)

  <b>raceId</b> - Exibe o identificador das corridas

  <b>round</b> - Exibe o número de rodadas da corrida

  <b>year</b> - Exibe o ano que ocorreu a corrida

<br>

  <h2>Results</h2>

  Essa tabela exibe dados dos resultados

  Dentro da tabela Results temos as seguintes colunas:

  <b>resultId</b> - Exibe o identificador dos resultados

  <b>raceId</b> - Exibe o identificador de corridas (Chave estrangeira da tabela Races)

  <b>driverId</b> - Exibe o identificador de pilotos (Chave estrangeira da tabela Drivers)

  <b>position</b> - Exibe a posição que os pilotos terminaram as corridas

  <b>points</b> - Exibe a quantidade de pontos cada piloto contém

  <b>laps</b> - Exibe a quantidade de voltas dos pilotos nos circuitos

  <b>fastestLapSpeed</b> - Exibe a velocidade máxima atingida por cada piloto

<hr>
<br>

Agora que entendemos a base de dados que irei trabalhar, vou aos processos realizados de tratamento de dados: coleta, transformação e carregamento <b>(ETL)</b>:

<h1>Processo de Tratamento de Dados (ETL)</h1>

Nesta etapa inicial, fiz o carregamento dos dados da minha fonte de dados, os meus dados estavam armazenados em um arquivo na extensão ".xls", por se tratar de um arquivo excell após o carregamento dos dados abri o PowerQuery do Power Bi para fazer o tratamento dos dados.

![01](https://github.com/user-attachments/assets/ec8ea6c1-4956-44ba-a9c3-f957d7728e05)

<br>
<br>

A primeira transformação que fiz nos meus dados foi mudar o tipo da coluna <b>"position"</b> da tabela <b>"Results"</b> que estava com os dados no tipo <b>"Text"</b>, fiz a mudança e transformei os dados para o tipo <b>"Número Inteiro"</b>.

![02](https://github.com/user-attachments/assets/2cd8c6c3-4b05-42a1-ac36-2bc1cba00277)

<br>
<br>

Ainda na tabela <b>"Results"</b> faço a mudança do tipo de dados da coluna <b>"fatestLapSpeed"</b> que estava com os dados formatados no tipo <b>"Texto"</b> e transformei-os para o tipo <b>"Número Decimal"</b>.


![03](https://github.com/user-attachments/assets/c2c7a990-b315-49f1-9486-b2f0e687e8ab)

<br>
<br>

Ainda na tabela <b>"Results"</b> notei que havia uma coluna chamada <b>"positionText"</b> em que eu não a utilizaria no meu projeto, então para otimizar ainda mais eficiência computacional eu optei por deletar (drop) toda a coluna, já que não faria uso da mesma.

![04](https://github.com/user-attachments/assets/69f122e8-2234-4816-9b5a-b19295df5800)

<br>
<br>

Agora indo para a tabela <b>"Drivers"</b> notei que haviam duas colunas chamadas de <b>"forename"</b> e <b>"suname"</b> onde eu poderia fazer uma normalização dos dados, então decidi fazer a junção das duas colunas para os dados ficarem unificados em uma coluna apenas.

![05](https://github.com/user-attachments/assets/4e93357e-657a-4df5-a587-c67a9f75b5f0)

<br>
<br>

Após a junção das duas colunas foi criado uma coluna que nomeie como <b>"fullName"</b>, note que como a base de dados está em inglês tenho que seguir o padrão nomeando a coluna também em inglês.
Como o nome já sugere, está coluna contém o nome e o sobrenome dos pilotos da fórmula 1.

![06](https://github.com/user-attachments/assets/7e91c233-e90e-456e-b005-f100472132d5)

<br>
<br>

Como a base de dados veio da origem bem formatada e tratada, não foi preciso fazer muitas etapas de transformação na mesma, este é um cenário semi-ideal. eralmente as bases de dados vêm bem mais sujas para realizarmos um tratamento mais eficiente.

<hr>
<br>
<br>

<h1>Relacionamento das tabelas</h1>

Agora com os dados já tratados e carregados no ambiente do Power Bi, tenho que vê se o mesmo criou os relacionamentos automaticamente corretos, e dando uma olhada nos meus relacionamentos vi que ele de fato criou todos corretamente, então não preciso mudar nada nessa parte de relacionamento entre as tabelas.
Para ficar melhor contextualizado irei mostrar a cardinalidade desses relacionamentos entre as tabelas.

Results (N) > (1) Races (Muitos pra Um) (N, 1)

Results (N) > (1) Drivers (Muitos pra Um) (N, 1)

Results (N) > (1) Constructors (Muitos pra Um) (N, 1)

Races (N) > (1) Circuits (Muitos pra Um) (N, 1)

<br>

![00](https://github.com/user-attachments/assets/0365e283-42dc-4897-8a80-2fb92192a8f9)

<hr>
<br>
<br>

<h1>Criação de Medidas</h1>

Após o tratamento dos dados, farei a criação de algumas medidas utilizando a linguagem <b>DAX (Data Analysis Expressions)</b> do próprio Power BI. Isso me ajudará posteriormente na criação dos gráficos.

<br>

Nesta etapa eu faço a criação de uma tabela com o nome de <b>"Medidas"</b>, como o nome já sugere essa tabela terá como função única e exclusivamente organizar as medidas que irei criar ao longo do projeto.

![01](https://github.com/user-attachments/assets/5ecf36ae-0f33-46ed-ae46-3fc277208e66)

<br>
<br>

A primeira medida que irei criar se chama <b>"Corridas</b> com a finalidade de saber o numero de corridas.

No código eu faço um "DISTINCTCOUNT para me dá os valores únicos da coluna <b>"raceId"</b> da tabela <b>"Results"</b>.

![02](https://github.com/user-attachments/assets/533f6e19-901d-49f9-b823-d7e4eff06acd)

<br>
<br>

Outra medida que criei se chama <b>"Equipes"</b> com a finalidade de saber a quantidade de equipes.

Utilizando também o DISTINCTCOUNT da coluna <b>"constructorID"</b> da tabela <b>"Results"</b> para me dá os valores distintos (únicos) das equipes.

![03](https://github.com/user-attachments/assets/4bbec303-8137-41d7-8f23-5ffcc95b5786)

<br>
<br>

A próxima medida criada foi para saber a quantidade de pilotos e se chamará <b>"Pilotos</b>.

Seguindo a mesma lógica das demais utilizo o comando DISTINCTCOUNT para me dá a contagem distinta dos pilotos na coluna <b>"driverID"</b> da tabela <b>"Results"</b>.

![04](https://github.com/user-attachments/assets/62960bb9-5e02-4e28-905e-b59b0d63d25b)

<br>
<br>

E por fim, a última medida criada foi para saber a quantidade de temporadas e se chamará <b>"Temporadas"</b>.

Para ter uma contagem distinta das temporadas eu fiz um DISTINCTCOUNT da coluna "year" que está na tabela "Races".

![05](https://github.com/user-attachments/assets/00dcd7f2-6308-4b94-bea1-e10f91304e3c)

<hr>
<br>
<br>

<h1>Página Inicial</h1>

A primeira página que irei criar no projeto será a HomePage (Página Inical), irei criar todas as páginas na minha linguagem natal (Português - br)

Será uma página bem básica.
Começarei trocando o background da página (vale lembrar que todas as imagens e telas de fundo desse projeto foram criados no Figma) e logo após irei criar alguns botões com a função de ação para eles terem a finalidade de navegar pelas páginas do Dashboard.

Depois de todas as estilizações e de ter adicionado todos os botões, a Página Inicial ficou o seguinte aspecto:

![01](https://github.com/user-attachments/assets/03ecb235-dde0-4cd2-991b-7833330ce794)

<hr>
<br>
<br>

<h1>Corridas</h1>

Agora vou criar a página de corridas.

Para começar a criação dos dashboards primeiramente mudei o fundo da minha área de trabalho para criar os dashboards com o fundo já aplicado, isso facilita e muito na hora de organizar os gráficos nos seus respectivos lugares

Ressaltando: Esses fundos e todas as imagens utilizadas nesse projeto foram criadas no Programa "Figma".

![00](https://github.com/user-attachments/assets/2c7a688b-4bda-4071-9fa6-335e781a0cf5)

<br>
<br>

<h2>Adicionando os gráficos na página de Corridas</h2>

Nessa parte de criação dos gráficos, eu fui colocando cada gráfico no seu respectivo local de acordo com a tela de fundo que adicionei na etapa anterior.

Os gráficos criados com seus respectivos dados foram os seguintes:

<h3>Gráfico de Cartões:</h3>

Corridas recebeu os dados da medida criada chamada <b>"Corridas"</b>

Temporadas recebeu os dados da medida criada chamada <b>"Temporadas"</b>

Pilotos recebeu os dados da medida criada chamada <b>"Pilotos"</b>

Equipes recebeu os dados da medida criada chamada <b>"Equipes"</b>

<h3>Gráfico de Coluna Clusterizado</h3>

Recebeu no eixo <b>"X"</b> os dados da medida <b>"Corridas"</b>

Recebeu no eixo <b>"Y"</b> os dados da coluna <b>"year"</b> da tabela <b>"Races"</b>

Após a criação da Coluna Clusterizada acima eu notei que os dados ficaram muito ruim de visualizar pois tinha bastante informações, por isso vi necessário a criação de um gráfico de <b>"Segmentação de Dados"</b> que servirá como filtro justamente para filtrar os dados e mostrar apenas os valores relevantes para uma posterior análise dos mesmos.

<h3>Gráfico Segmentação de Dados</h3>

Recebeu a coluna <b>"year"</b> da tabela <b>"Races"</b>

<br>

Resultado:

![01](https://github.com/user-attachments/assets/60a64126-5143-4aa9-a223-2c8ce61a54ac)

<hr>
<br>
<br>

Agora irei fazer a estilização dos meus gráficos.
Para poupar tempo e não estilizar gráfico por gráfico eu dou preferência em estilizar todos de uma vez com a opção de temas no Power Bi.

Eu fiz a exportação de um tema já criado em um arquivo .JSON

Após a aplicação do tema, os gráficos ficaram assim:

<br>

![02](https://github.com/user-attachments/assets/6f9693e6-5f4f-4693-ab97-ad7d48a4e832)

<br>
<br>

<h1>Criação de Gráficos da Página Corridas</h1>

Agora vamos para a criação dos outros gráficos desse dashboard.

<h2>Gráfico de Barras Empilhadas</h2>

Recebeu no eixo <b>"Y"</b> os dados da coluna <b>"country"</b> da tabela <b>"Circuits"</b>

Recebeu no eixo <b>"X"</b> os dados da medida <b>"Corridas"</b>

<h2>Gráfico de Mapa</h2>

No campo Localização recebeu os dados da coluna <b>"country"</b> da tabela <b>"Circuits"</b>

No campo Tamanho da bolha recebeu os dados da medida <b>"Corridas"</b>

<h2>Gráfico de Tabela </h2>

No campo colunas recebeu dados da medida <b>"Corridas"</b>

Também recebeu dados da tabela <b>"Circuits"</b> com as coluans <b>"Country"</b>, <b>"Location"</b> e <b>"Name"</b>

No próprio gráfico renomeie para seguir o padrão do idioma em português - Br

<b>"Name"</b> virou = <b>"Circuito"</b>

<b>"Country"</b> virou = <b>"Estado"</b>

<b>"Location"</b> virou = <b>"País"</b>

<br>

Resultado: 

![03](https://github.com/user-attachments/assets/e0cb2f32-320a-4d3e-896f-644821c850b3)

<br>

Para o gráfico de tabela ficar ainda melhor para uma posterior análise dos dados decidi fazer uma formatação condicional de barra de dados no campo Corridas, pintando os valores positivos em um azul mais claro.

<br>

Resultado

![04](https://github.com/user-attachments/assets/224fcc17-6d7e-449d-b4fb-fe02f1dac617)

<hr>
<br>
<br>

<h1>Criação do Tooltip Para a Página de Corridas</h1>

Agora vamos fazer a criação do Tooltip para utilizar na página de carros.

Para criar o Tolltip de Corridas eu tive que criar uma nova página no ambiente PowerBi com o nome de "Tolltip Corridas", esta página será de uso único e exclusivo para o indicador de Tooltip (Será usada como uma dica de ferramenta) que será adicionado ao gráfico de Tabelas.

Primeiro passo na criação do Tooltip é importar o Background do mesmo.

![05](https://github.com/user-attachments/assets/a38c88d1-ec55-488c-8e59-9b3863996084)

<br>
<br>

<h2>Agora fiz a criação dos seguintes gráficos:</h2>

<h2>Gráfico de Cartão</h2>

Recebeu em Valores a coluna <b>"name"</b> da tabela <b>"Circuits"</b>

Agora este é um passo muito <b>importante</b> na criação do Tooltip, colocarei em um gráfico a imagem de cada pista de fórmula 1 presente na base de dados. Para isso tive que mudar o formato de uma coluna específica.

A coluna é a <b>"picture_url"</b> da tabela <b>"Circuits"</b>. Os dados dessa coluna são links (urls) das imagens da pista, então eu tive que mudar a categoria dos dados de "Não categorizado" para "URL da Imagem".

![06](https://github.com/user-attachments/assets/c15b7c99-f4cc-4f77-9adf-43f1dfc68be1)

<br>
<br>

Para utilizar esta imagem em algum gráfico (visual) dentro do Power Bi, não se tem um visual que se adapte bem com imagens, todos ficam mal formatados ou com Bug's, então a solução será importar da loja de visuais do prróprio PowerBi um visual que atenda á minha necessidade.

O viusal personalizado escolhido foi o "Simple Image" que é gratuito para adquiri-lo.

Além da imagem eu também introduzi um outro gráfico ao lado.

<h2>Gráfico de Barras Empilhadas:</h2>

No eixo <b>"Y"</b> adicionei a coluna <b>"name"</b> da tabela <b>"Constructors"</b>
No eixo <b>"X"</b> adicionei a medida <b>"Corridas"</b>

E para finalizar vou adicionar a imagem da bandeira do país de cada pista que for selecionada.

![07](https://github.com/user-attachments/assets/8d4275cd-71e6-4d89-82a4-198bcacbffc1)

<hr>
<br>
<br>

<h2>Voltando para a criação de gráficos na página de corridas</h2>

Agora preciso criar um filtro para mostrar apenas as equipes vencedores de cada pista, e trazer isso em um rank com apenas os top 5 vencedores.

Na aba filtro do PowerBi ele me dá apenas a opção ed filtrar por colocação, mas não me dá a opção de trazer o Rank com as Top 5 equipes ganhadoras de cada pista, para isso então precisei criar uma nova medida.

A medida que vou criar é para obter a quantidade de vitórias de cada equipe.

Utilizo a função CALCULATE para filtrar a medida de corridas, filtrando ela na coluna <b>"position"</b> da tabela <b>"Results"</b>, depois eu uso o sinal de = 1 para trazer apenas os primeiros colocados.

![08](https://github.com/user-attachments/assets/4daba07a-f9d0-4bc3-b638-8c0640757e19)

<br>
<br>

Agora sim vou utilizar a aba filtros do PowerBi, justamente para colocar minha medida no campo de filtros e filtrar pelas 5 equipes que mais ganharam.

Note que meu filtro está bugado todo em branco, já fechei e abri o PowerBi diversas vezes, mas apenas nesse arquivo em específico que ele buga, como não está me atrapalhando na criação, eu deixei bugado até porque não achei uma solução para o problema.

![09](https://github.com/user-attachments/assets/23129a75-2437-47e5-941d-805fb6184500)

<br>
<br>

Após criado o Tooltip, basta eu ir no meu Gráfico de Tabela da página 1 que criei e adicionar o Tooltip.

Agora ao passar o mouse em cima da informação de pista, ele trás a informação do Tooltip contendo o nome da pista, imagem da pista selecionada,as 5 equipes que mais ficaram em primeiro lugar em cada pista selecionada e a bandeira do país da respectiva pista.

![10](https://github.com/user-attachments/assets/80d2bc85-88aa-4443-9305-42bc3676a53e)

<hr>
<br>
<br>

<h1>Página de Corridas</h1>

Reaproveitei alguns gráficos da página de Corridas e adicionei nesta página.

<br>

<h2>Criação dos gráficos</h2>

Agora vamos para a criação dos gráficos exclusivos da página de <b>"Equipes"</b>.

Crio um Gráfico de Tabelas, para mostrar o nome da equipe e a quantidade de vitórias que cada uma teve. Faço isso reaproveitando a formatação da tabela da página de <b>"Corridas"</b>.

Em colunas eu uso os dados de:

Tabela <b>"Cosntructors"</b> Coluna <b>"name"</b>

Medida <b>"Corridas"</b>

Medida <b>"Vitórias"</b>

![02](https://github.com/user-attachments/assets/daa6c8f9-efe5-47b7-be46-d72fb81f6c36)

<br>
<br>

<h1>Criação do Tooltip da Página Equipes</h1>

Assim como na primeira página <b>"Corridas"</b>, também irei fazer um tooltip para as páginas <v>"Equipes".

Começando com a criação do tooltip:

Criei uma nova página com o nome Tooltip Equipes para usar essa página exclusivamente como um Tooltip (Dica de Ferramentas).

Primeiro faço a mudança do Background e personalizo o tamanho da página para 400 x 560.

![03](https://github.com/user-attachments/assets/c03ac094-40da-4766-82a5-0fd49435893c)

<br>
<br>

Vamos fazer a criação de um gráfico para mostrar a imagem do construtor (equipe) no tooltip, porém para isso vamos ter que mudar a categoria dos dados da coluna <b>"car_url"</b> da tabela <b>"Constructors"</b>, ela está categorizada inicialmente como "Não Categorizado" e fiz a mudança para "URL da Imagem", justamente para utilizar os dados dessa coluna como imagem.

![04](https://github.com/user-attachments/assets/778595c8-5df6-4517-92ba-0cba1f301f81)

<br>
<br>

Após essa transformação, agora eu preciso do gráfico que baixei dos gráficos externos do PowerBi que se chama "Simple Image", justamente para utilizar essa coluna <b>"car_url"</b> como uma imagem dos construtores (equipe).

Agora vamos para a criação dos demais gráficos do Tooltip:

<h2>Gráfico Simple Image</h2>

No campo Image URL adiciono a coluna <b>"car_url"</b> da tabela <b>"Constructors"</b>

<h2>Gráfico de Cartão</h2>

No campo Campos adiciono a coluna <b>"name"</b> da tabela <b>"Constructors"</b>

![05](https://github.com/user-attachments/assets/9fbc641d-6e04-4d9c-8d54-f5d9376ba900)

<br>
<br>

Agora para a criação dos dois gráficos que faltam vou precisar criar uma medida chamada de Total Pontos, como o nome já sugere esta medida é a soma dos Pontos totais.

![06](https://github.com/user-attachments/assets/191af797-c802-4eae-a9ba-bc5704899e0a)

<br>
<br>

Agora vou criar os dois gráficos que restam.

<h2>Gráfico de colunas clusterizado</h2>

No eixo <b>"X"</b> adiciono a coluna <b>"fullname"</b> da tabela <b>"Drivers"</b>

No eixo <b>"Y"</b> adiciono a medida recém criada <b>"Total Pontos"</b>

<h2>Gráfico de colunas clusterizado</h2>

No eixo <b>"X"</b> adiciono a coluna <b>"name"</b> da tabela <b>"Races"</b>

No eixo <b>"Y"</b> adiciono a medida recém criada <b>"Total Pontos"</b>

![08](https://github.com/user-attachments/assets/0f163224-c512-4013-b2c7-603493a69b04)

<br>
<br>

Agora para terminar meu Tooltip vou fazer um filtro para buscar o Top 3 Pilotos e o Top 3 Grand Pix nos dois gráficos criados.

Aproveio e já faço a estilização das cores dos gráficos.

![09](https://github.com/user-attachments/assets/a90d58a7-abe6-4f1a-84c0-5888ec6f2c66)

<br>
<br>

<h2>Resultado do Tooltip:</h2>

![09](https://github.com/user-attachments/assets/c440a238-480e-4515-af9e-2694c21067f8)

<br>
<br>

<h1>Voltando Para a Criação dos Gráficos da Página Equipes</h1>

Voltando para nossa página de Equipes eu preciso criar algumas medidas para colocar na minha tabela.

A primeira medida criada será a <b>"Corridas 1st"</b>, como o nome sugere vou pegar as corridas que as equipes saíram em primeiro lugar.

Filtro a coluna com a função CALCULATE, com a função COUNTROWS faço as contagens da linha da tabela <b>"Results"</b>, e trago todas as posições da coluna <b>"position"</b> que seja igual a 1 (=1), primeiro lugar.

![10](https://github.com/user-attachments/assets/130b7e99-c2bb-4ed0-b4cb-c1bc35f58b95)

<br>
<br>

A segunda medida a ser criada vai ser a <b>"Podium"</b> e terá como função exibir o podium de primeiro, segundo e terceiro lugar.

Porém antes de criar esta medida eu fiz a criação de mais duas medidas complementares, que será a <b>"Corridas 2st"</b> e <b>"Corridas 3st"</b>, justamente para colocá-las na medida de <b>"Podium"</b>, ambas as medidas são iguais a medida criada de <b>"Corridas 1st"</b> so múdando o numero da colocação na medida.

Após a criação dessas medidas, vou criar a medida <b>"Podium"</b>

A medida é bem simples, é concatenação das medidas criadas de Primeiro, Segundo e Terceiro lugar.

![11](https://github.com/user-attachments/assets/bc008a90-9300-451e-a509-d5f88a2856be)

<br>
<br>

Agora para finalizar os dados da tabela vamos criar mais uma medida, essa medida se chamará <b>"Rank Total Pontos"</b>, e ela fará justamente um rank de todas as equipes de acordo com os pontos somados.

Traremos a função RANKX, e dentro colocaremos uma função ALL para retirar os filtros e trazer todos os dados da tabela <b>"Constructors"</b>, e assim faremos o rank das equipes utilizando a medida Total Pontos.

![12](https://github.com/user-attachments/assets/1a5d018c-fcaf-45e2-8180-99830ec7400d)

<br>
<br>

Agora basta adicionar os campos ao gráfico de Tabela já renomeando elas para o Português - BR

No campo colunas adicionei os seguintes dados:

Coluna <b>"name"</b> da tabela <b>"Constructors"</b> - Renomeie para <b>"Equipe"</b>

Coluna <b>"nationality"</b> da tabela <b>"Constructors"</b> - renomeie para <b>"Nacionalidade"</b>

Medida <b>"Corridas"</b>

Medida <b>"Rank Total Pontos (Equipe)"</b> - renomeie para <b>"Rank (pts)"</b>

Medida <b>"Total Pontos"</b> - renomeie para <b>"Pontos"</b>

Medida <b>"Corridas 1st"</b> - renomeie para <b>"Vitórias"</b>

Medida <b>"Podiums"</b> - renomeie para <b>"Pódiums"</b>

<br>

Após adicionar todos os dados, eu preciso fazer a estilização da Tabela criada.

Fiz a criação da formatação condicional dos dados e mudei algumas coisas na parte de estilização da tabela.

Por fim a tabela ficou desta forma:

![14](https://github.com/user-attachments/assets/b881eecc-1110-4409-96b0-68b540c6430f)

<br>
<br>

Agora vou fazer todas as criações de gráficos da página, e posteriormente a estilização de todos.

Este gráfico é para saber o Número de podiums, vitórias e pontos por temporada.

Agora vamos criar um gráfico de Colunas agrupadas e linha com os seguintes dados

No eixo <b>"X"</b> vou adicionar a coluna <b>"year"</b> da tabela <b>"Races"</b>

No eixo <b>"Y"</b> vou adicionar a medida <b>"Podium"</b>

No eixo <b>"Y"</b> vou adicionar a medida <b>"Corridas 1st"</b> e Renomear para <b>"Vitórias"</b>

No eixo <b>"Y"</b> da linha vou adicioanr a medida <b>"Total Pontos"</b> e Renomear para <b>"Pontos"</b>

Para complementar este gráfico vou criar um Segmentador de dados para fazer o filtro das equipes somente neste gráfico, sem afetar os demais gráficos.

![15](https://github.com/user-attachments/assets/dd8f608d-d995-45f4-a682-bd2289c533aa)

<br>
<br>

Agora farei a criação de um gráfico de barras empilhadas.

Este gráfico irá me mostrar os pódiums por equipe

Já farei após a inserção dos dados a estilização do gráfico.

No eixo <b>"Y"</b> irei adicionar a coluna <b>"name"</b> da tabela <b>"Constructors"</b>

No eixo <b>"X"</b> adcionarei a Medida <b>"Corridas 1st"</b> - Renomeando para 1º Lugar

No eixo <b>"X"</b> adcionarei a Medida <b>"Corridas 2st"</b> - Renomeando para 2º Lugar

No eixo <b>"X"</b> adcionarei a Medida <b>"Corridas 3st"</b> - Renomeando para 3º Lugar

Por fim o gráfico com o seguinte aspecto:

![16](https://github.com/user-attachments/assets/7316f042-40ab-4fcb-9d6d-fbae5538dcdb)

<br>
<br>

Agora vou criar um Gráfico de Tabelas para exibir a Equipe vencedora por Grand Pix.

Após a inserção dos valores vou fazer a estilização do gráfico.

No campo Colunas vou adicionar os seguintes valores:

Vou adicionar a coluna <b>"year"</b> da tabela <b>"Races"</b> - Renomeie para "Ano"

Vou adicionar a coluna <b>"name"</b> da tabela <b>"Races"</b> - Renomeie para "Grand Pix"

Após a criação e estilização, o gráfico ficou dessa forma:

![17](https://github.com/user-attachments/assets/39814c09-ef46-4f60-a805-f486565ce301)

<hr>
<br>
<br>






























































































































    
