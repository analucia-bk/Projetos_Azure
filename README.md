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

<h3> Fonte dos dados </h3>
<p>ECDC Website: </p>
<li>Casos Confirmados</li>
<li>Mortalidade</li>
<li>Hospitalização e Casos de UTI</li>
<li>Quantidade de testes</li>
<h4>Eurostat Website:</h4>
<li>População por faixa etária</li>

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

![Captura de Tela 2022-02-14 às 16 16 55](https://user-images.githubusercontent.com/53180510/153931630-f3a08fae-cc59-4c48-8b86-823a2fd3f42f.png)

<li> Criação de dois datasets, um no blob onde foi carregado o arquivo "population_by_age" e um no ADLS para onde o arquivo foi copiado </li>
<li> Criação do pipeline</li>
<li>Na primeira atividade foi feita uma validação para checagem se o arquivo realmente existia no Blob antes de ser copiado para o ADSL Gen2.</li>

![Captura de Tela 2022-02-14 às 15 38 09](https://user-images.githubusercontent.com/53180510/153932381-01cdefe8-0aa6-4d92-a82b-9d45cf1c1ea5.png)

<li>Na segunda, além da validação anterior, foi inserida uma condição para a cópia do arquivo, ela só seria feito se o número de colunas do dataset estivesse correto. Para isso foi feita uma atividade no If para condição True. Caso essa atividade essa condição estivesse satisfeita, o arquivo seria copiado e após, excluído do blob.
  
  
![Captura de Tela 2022-02-14 às 15 53 54](https://user-images.githubusercontent.com/53180510/153932971-5d9dc63a-aaeb-4305-ab7b-c34b2a670138.png)

![Captura de Tela 2022-02-14 às 16 05 54](https://user-images.githubusercontent.com/53180510/153933282-05116164-34cf-49a0-83fd-157f3e08eeed.png)

