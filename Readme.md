# Running the code (Spark standalone cluster)
You can run the spark standalone cluster by running:
```shell
make run
```
or with 4 workers using (can be adsuted in Makefile):
```shell
make run-scaled
```

## Web UIs
The master node can be accessed on:
`localhost:8080`. 

The spark history server is accessible through:
`localhost:18080`.

To open workers UI, you should use port that was assigned in docker-compose.yml.  


## Data Files
If you would like to import data files into pyspark, please make sure you have them located both on the cluster and your local drive **by the same path**.

Default path is: ```/opt/spark/data/```.



## Jupyter Notebook
First, you have to install all the requirements to run Spark on your machine (not in VM), please for instructions from here (it's important to intsall JAVA locally first): https://spark.apache.org/docs/latest/api/python/getting_started/install.html.

Make sure you have all required libraries installed with the same version as it is on the cluster. 

Then you can connect to the cluster using Jupyter Notebook (or just any python script).

You can see an example of creating a spark session from this notebook: notebooks/session.ipynb.

All you need is to specify master node when creating the session, like this:
``` python
SparkSession.builder \
    .appName("cluster-app") \
    .master("spark://localhost:7077") \
```
You can specify additional configs, like memory per executor, or cores for each worker. 

You can find out more about config here https://sparkconfigoptimizer.com/ . 
