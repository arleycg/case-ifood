# case-ifood

### solução do case proposto por Arley Clayton Gomes

## Premissas:

Para o desenvolvimento do case, foram consideradas as seguintes tecnologias e premissas:
- Todo o desenvolvimento foi realizado utilizando o Databricks Free Edition
- As linguagens utilizadas foram PySpark e SparkSQL
- Foi adotado o Unit Catalog como estratégia de governança, catalogo dos dados, acessos, e linhagem dos dados (data lineage)
- Adotado arquitetura medalhão (landing zone, bronze, silver e gold layer como camada de consumo dos dados)
- A carga dos dados entre as camadas foi realizada utilizando Spark Streaming
- Utilizado bucket do S3 como storage

## Passo a passo do desenvolvimento:

###  1 - Criado storage no S3 com o nome "arley-case-ifood" (arley-case-ifood):
![bucket s3](imgs/s3.png)

###  2 -  Configurado o External Location do "Unit Catalog" para apontar para o S3:
![external location](imgs/external_location.png) 

###  3 -  Estrutura final do catalogo:
  - 3.1 criado catalogo de nome "ifood"
  - 3.2 criado schemas para cada layer (bronze, silver e gold)
  - 3.3 criado as respectivas tabelas em cada layer:

        3.3.1 - Bronze: ifood.bronze.tbl_bronze_nyc_taxi_data
        3.3.2 - Silver: ifood.silver.tbl_silver_nyc_taxi_data
        3.3.3 - Gold:   ifood.gold.tbl_gold_nyc_taxi_data
  - 3.4 criado volume de nome "landing" para governança via unit catalog dos dados baixados da API em JSON

![external location](imgs/catalogo.png) 

###  4 - Notebooks (src - codigos fontes da solução):
  -  4.1  Configuração do ambiente: [1 - nb_configuracao_ambiente_case_ifood.html](https://github.com/arleycg/case-ifood/blob/main/src/1%20-%20nb_configuracao_ambiente_case_ifood.html)
  -  4.2  Download dos dados para a Landing Zone: [2 - nb_download_landing_json.html](https://github.com/arleycg/case-ifood/blob/main/src/2%20-%20nb_download_landing_json.html)
  -  4.3  carga dos dados na bronze layer: [3 - nb_bronze_layer.html](https://github.com/arleycg/case-ifood/blob/main/src/3%20-%20nb_bronze_layer.html)
  -  4.4  carga dos dados na silver layer: [4 - nb_silver_layer.html](https://github.com/arleycg/case-ifood/blob/main/src/4%20-%20nb_silver_layer.html)
  -  4.5  carga dos dados na gold layer: [5 - nb_gold_layer.html](https://github.com/arleycg/case-ifood/blob/main/src/5%20-%20nb_gold_layer.html)

###  5 - Respostas do Desafio (analysis -  Scripts/Notebooks com as repostas do desafio):
  -  5.1  Notebook com as respostas do desafio: [6 - nb_respostas_desafio.html](https://github.com/arleycg/case-ifood/blob/main/analysis/6%20-%20nb_respostas_desafio.html)
