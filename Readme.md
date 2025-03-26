# Docker container for ElasticSearch

## Container Structure

This Docker container provides a complete setup for Elasticsearch using Docker Compose.

### Folder Structure

The directory structure inside the `docker-es` project is organized as follows:

```
docker-es/ 
    ├── docker-compose.yaml # Defines Elasticsearch container setup and runtime behavior 
    └── elasticsearch 
    ├── config 
        │ 
        ├── Dockerfile # Defines the Elasticsearch container build process └── elasticsearch.yml # Elasticsearch configuration file 
        ├── data # Elasticsearch data storage └── logs # Elasticsearch logs
```

### Explanation of Files

#### `docker-compose.yaml`

- Manages Elasticsearch container build and runtime settings.
- Mounts local directories (`data`, `logs`) into the container for persistent data management.

#### `Dockerfile`

- Builds a Docker image based on the official Elasticsearch Docker image.
- Copies Elasticsearch configurations (`elasticsearch.yml`) into the container.

#### `config/elasticsearch.yml`

- Elasticsearch configuration settings (e.g., single-node discovery).

## Create and Start the Docker Container

To launch Elasticsearch interactively, execute:

```bash
docker-compose build
docker-compose up -d
```

### Elasticsearch Sample CURL Operations

## Create Document

```bash
curl -X PUT "<http://localhost:9200/books/_doc/1>" -H 'Content-Type: application/json' -d'
{
  "title": "Elasticsearch Guide",
  "author": "Elastic"
}'
```

## Get Document

```bash
curl -X GET "http://localhost:9200/books/_doc/1"
```

## Update Document

```bash
curl -X POST "http://localhost:9200/books/_doc/1/_update" -H 'Content-Type: application/json' -d'
{
  "doc": {
    "author": "Elastic Updated"
  }
}'
```

## Delete Document

```bash
curl -X DELETE "http://localhost:9200/books/_doc/1"
```

## Search all documents

```bash
curl -X GET "http://localhost:9200/books/_search" -H 'Content-Type: application/json' -d'
{
  "query": { "match_all": {} }
}'
```

## Licence

MIT License

Copyright (c) 2024

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
