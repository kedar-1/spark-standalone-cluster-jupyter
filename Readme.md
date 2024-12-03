# About the repo

# Running the code (Spark standalone cluster)
You can run the spark standalone cluster by running:
```shell
make run
```
or with 3 workers using:
```shell
make run-scaled
```
You can submit Python jobs with the command:
```shell
make submit app=dir/relative/to/spark_apps/dir
```
e.g. if you have `ex6.py` in your spark_apps folder: 
```shell
make submit app=ex6.py
```

There are a number of commands to build the standalone cluster,
you should check the Makefile to see them all. But the
simplest one is:
```shell
make build
```

## Web UIs
The master node can be accessed on:
`localhost:8080`. 
The spark history server is accessible through:
`localhost:18080`.

# Fixing the links on the Spark master UI
Since we are running the spark cluster on docker, the
worker related links do not work on the UI.
To fix this I created a generate-docker-compose script
that generates the docker compose file (called 
docker-compose.generated.yml) with the desired number of 
workers where each worker has assigned and exposed port
number.

To bring up this cluster, you can just run:
```shell
make run-generated
```

By default, the command will launch a Spark cluster with
a master, history server and 3 worker nodes. 

# Stories published on Medium
Setting up a standalone Spark cluster can be found [here](https://medium.com/@MarinAgli1/setting-up-a-spark-standalone-cluster-on-docker-in-layman-terms-8cbdc9fdd14b).
