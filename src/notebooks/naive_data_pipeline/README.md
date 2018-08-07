# Naive Data Pipeline

### Pre-requisites

- Python 3.5+
- pipenv
- Docker

### Before you jump into the notebook

- Run bblfsh using: `docker run -d --name bblfshd --privileged -p 9432:9432 -v bblfsh-storage:/var/lib/bblfshd bblfsh/bblfshd`
- Run sourced-engine using: `docker run --name engine-jupyter --rm -it -p 8080:8080 -v <Absolute_Path_to_repositories>/siva/latest:/repositories --link bblfshd:bblfshd srcd/engine-jupyter`

### Play around with the notebook

- The notebook can be accessed at `0.0.0.0:8080`

### If you've never used Spark before ...

- [PySpark SQL Docs](https://spark.apache.org/docs/2.3.0/api/python/pyspark.sql.html) can be pretty helpful

#### Some questions that I had to find answers for while making this run ...

* How do I classify blobs by language?
    * [Use blobs.classify_languages()](https://github.com/src-d/engine/blob/master/_examples/pyspark/pyspark-shell-classifying-languages.md)
* My machine crashed! How do I prevent that from happening?
    * I don't have a definite answer to this yet, but I put a max limit on the memory and number of cores.
        * You can do that by adding config options while building the SparkSession object
