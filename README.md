<h1> Projeto Azure </h1>

<p> Exercícios e projetos realizados com o objetivo de exercitar ferramentas do Azure e de Engenharia de Dados </p>
<p> Lista de projetos: </p>
<ul> 01 - Covid 19 </ul>
<p> Projeto criado durante o curso Azure Data Factory for Data Engineers - Project on Covid19 lecionado por Ramesh Retnasamy na Udemy </p>
<h3>Tecnologias Utilizadas:</h3>

<h3> Data Lake </h3>

O Data Lake foi construído com os seguintes dados para ajudar na previsão da propagação do vírus/mortalidade:
<li>Casos Confirmados</li>
<li>Mortalidade</li>
<li>Hospitalização e Casos de UTI</li>
<li>Quantidade de testes</li>
<li>População por faixa etária</li>

<h3> Data Warehouse </h3>
O Data Warehouse foi construído com os seguintes dados para ajudar a relatar tendências:
<li>Casos Confirmados</li>
<li>Mortalidade</li>
<li>Hospitalização e Casos de UTI</li>
<li>Quantidade de testes</li>

<h3> Arquitetura </h3>

<h3>Recursos Utilizados:</h3>
<li>Data Factory</li>
<li>Blob Storage Account</li>
<li>Data Lake Storage Gen2</li>
<li>Azure SQL Database</li>
<li>Azure Databricks Cluster</li>
<li>HD Insight Cluster</li>

<h3>Primeira atividade no Azure Data Factory: CopyData</h3>
<p> Realizar a ingestão dos dados do arquivo "population by age" no Data Lake que posteriormente serão utilizados nos modelos de machine learning para predizer o aumento das taxas de mortalidade</p>
<p> Passo a passo </p>
<li> Criação de dois linked services para as conexões com o blob e o data lake: </li>

<img width="600" height="300" src= "https://user-images.githubusercontent.com/53180510/153931630-f3a08fae-cc59-4c48-8b86-823a2fd3f42f.png">


<li> Criação de dois datasets, um no blob onde foi carregado o arquivo "population_by_age" e um no ADLS para onde o arquivo foi copiado </li>
<li> Criação do pipeline</li>
<li>Na primeira atividade foi feita uma validação para checagem se o arquivo realmente existia no Blob antes de ser copiado para o ADSL Gen2.</li>

<img width="650" height="250" src= "https://user-images.githubusercontent.com/53180510/153932381-01cdefe8-0aa6-4d92-a82b-9d45cf1c1ea5.png">

<li>Na segunda, além da validação anterior, foi inserida uma condição para a cópia do arquivo, ela só seria feito se o número de colunas do dataset estivesse correto. Para isso foi feita uma atividade no If para condição True. Caso essa atividade essa condição estivesse satisfeita, o arquivo seria copiado e após, excluído do blob.</li>
  
<img width="600" height="250" src= "https://user-images.githubusercontent.com/53180510/153934018-581b65ce-1990-4a2e-865d-2f33bfce2e64.png">
<img width="600" height="250" src= "https://user-images.githubusercontent.com/53180510/153935208-29f64b8d-12f7-47d4-8591-d4cfc0db8316.png">


<h3>Segunda atividade no Azure Data Factory: CopyData</h3>
<p> Realizar a ingestão dos dados do arquivo "cases_death_csv" no Data Lake, a ingestão dos dados, diferentemente da primeira atividade, foi feita via HTTP. Por isso, foi criado um novo linked service para realizar a conexão, dois novos datasets, um para o arquivo via HTTP e outro na camada raw  e um novo pipeline para realizar o copy data desses dados.</p>
 
<img width="300" height="200" src= "https://user-images.githubusercontent.com/53180510/154516288-68efea7c-4cf1-4d76-a636-193bfd5762ce.png">

<img width="1200" height="450" src= "https://user-images.githubusercontent.com/53180510/154515623-14a42536-7c84-4dcc-8d3c-f26f78e06dc4.png">



  
