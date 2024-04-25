# TrabalhoEngDados
TEMA DO TRABALHO: APACHE SPARK COM DELTA LAKE E APACHE ICEBERG

## Integrantes
* [Guilherme Machado Darabas](https://github.com/gmdarabas)
* [Paulo Roberto Simão](https://github.com/paulorsimao)
* [Rubens Scotti Junior](https://github.com/rubensscotti)
* [Stephan  Anthony  Marques](https://github.com/stephan-anthony)

#Procedimento

1. Instalação do PySpark com pip e poetry:
Primeiro, vamos instalar o PySpark usando pip e poetry.
Instale o Python e o pip se ainda não estiverem instalados. Você pode usar o Anaconda ou instalar diretamente do site do Python.
Instale o poetry se ainda não o tiver:
"pip install poetry"

3. Crie um novo ambiente com poetry:
poetry new pyspark-jupyter
cd pyspark-jupyter
poetry add pyspark

4. Instalação do JupyterLab
Instale o JupyterLab dentro do ambiente Poetry:
"poetry add jupyterlab"

4. Configuração do ambiente
Ative o ambiente Poetry:
"poetry shell"

Inicie o JupyterLab:
"jupyter lab"

5. Configuração do ambiente PySpark no JupyterLab
Dentro do JupyterLab, crie um novo notebook Python e configure o ambiente PySpark:

from pyspark.sql import SparkSession
# Configuração básica do SparkSession
spark = SparkSession.builder \
    .appName("Spark with JupyterLab") \
    .getOrCreate()
# Teste básico para verificar se o Spark está funcionando
df = spark.createDataFrame([(1, 'Alice'), (2, 'Bob')], ['id', 'name'])
df.show()

6. Instalação do Delta Lake e Apache Iceberg
Para instalar o Delta Lake e Apache Iceberg, você pode fazer isso diretamente no ambiente Poetry:
"poetry add delta-spark iceberg-spark"

7. Uso do Delta Lake e Apache Iceberg
Agora você pode usar o Delta Lake e Apache Iceberg em seus notebooks PySpark:

# Importe as bibliotecas Delta Lake e Apache Iceberg
from delta import *
from iceberg.spark import SparkSession
from iceberg.catalog import Catalog
# Configure o catálogo Iceberg
iceberg_catalog = Catalog.builder().build()
iceberg_catalog.loadTable("namespace.table_name").history().show()
# Use o Delta Lake
delta_table = DeltaTable.forPath(spark, "path_to_delta_table")
delta_table.toDF().show()
