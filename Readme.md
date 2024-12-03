# PySpark standalone cluster


## Running the code 
You can run the spark standalone cluster by running:
```shell
make run
```
or with 4 workers using (can be adjusted in Makefile):
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
If you would like to import data files into PySpark, please make sure you have them located both on the cluster and your local drive **by the same path**.

Default path is: ```/opt/spark/data/```.



## Jupyter Notebook
First, you have to install all the requirements to run Spark on your machine (not in VM), please for instructions from here (it's important to install JAVA locally first): https://spark.apache.org/docs/latest/api/python/getting_started/install.html.

Make sure you have all required libraries installed with the same version as it is on the cluster. 

Then you can connect to the cluster using Jupyter Notebook (or just any Python script).

You can see an example of creating a spark session from this notebook: notebooks/session.ipynb.

All you need is to specify master node when creating the session, like this:
``` python
SparkSession.builder \
    .appName("cluster-app") \
    .master("spark://localhost:7077") \
```
You can specify additional configs, like memory per executor, or cores for each worker. 

You can find out more about config here https://sparkconfigoptimizer.com/ . 

## Details on Docker image

There is the tutorial describing in details on how the docker image can be configured for standalone cluster: https://medium.com/@MarinAgli1/setting-up-a-spark-standalone-cluster-on-docker-in-layman-terms-8cbdc9fdd14b.

Code in this repo was adjusted to make it work out of the box with PySpark using regular Python scripts or JuPyter notebooks. 

### Important Note
**You should be careful with Spark/PyPspark versions, because some of them may (older ones) not support cluster mode with Python.**
