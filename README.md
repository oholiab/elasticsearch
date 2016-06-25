## Elasticsearch Dockerfile


This repository contains **Dockerfile** of [Elasticsearch](http://www.elasticsearch.org/) for [Docker](https://www.docker.com/)


### Base Docker Image

* Alpine 3.4
* Forked from
  [dockerfile/elasticsearch](https://github.com/dockerfile/elasticsearch) -
changed a bunch of the README cos it's suddenly all not technically true.


### Installation

1. Install [Docker](https://www.docker.com/).
2. Build an image from Dockerfile: `docker build -t="dockerfile/elasticsearch"`

### Usage

    docker run -d -p 9200:9200 -p 9300:9300 

#### Attach persistent/shared directories

  1. Create a mountable data directory `<data-dir>` on the host.

  2. Create Elasticsearch config file at `<data-dir>/elasticsearch.yml`.

    ```yml
    path:
      logs: /data/log
      data: /data/data
    ```

  3. Start a container by mounting data directory and specifying the custom configuration file:

    ```sh
    docker run -d -p 9200:9200 -p 9300:9300 -v <data-dir>:/data dockerfile/elasticsearch /elasticsearch/bin/elasticsearch -Des.config=/data/elasticsearch.yml
    ```

After few seconds, open `http://<host>:9200` to see the result.
