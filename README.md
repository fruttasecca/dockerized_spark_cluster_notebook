# dockerized_spark_cluster_notebook

Interfacing a spark cluster through a python notebook, dockerized.  

Spark master web ui at [http://127.0.0.1:8080/](http://127.0.0.1:8080/)  
Each worker web ui is on a port assigned by docker so that the number of workers can be
scaled up, their port can be found with ``docker container ls``.

Get to the notebook via http://\<hostname\>:8888/?token=\<token\>  
Check the notebook logs (``docker logs notebook``) for the token or the direct link.
Once inside the notebook, connect with:

```python
from pyspark.sql import SparkSession

spark = SparkSession.builder \
    .master("spark://spark-master:7077") \
    .appName("Spark Swarm") \
    .getOrCreate()
```

Also working in swarm mode as of ``Docker version 19.03.4, build 9013bf583a``.


