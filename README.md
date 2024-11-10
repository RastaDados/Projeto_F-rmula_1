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













    
