# Overview

## Introduction

The InterLex APIs are provided via an ElasticSearch endpoint.  &#x20;

### Access to the InterLex APIs

Access to the InterLex API is provided via an Elasticsearch pass-through.

{% swagger baseUrl="https://scicrunch.org/api" path="/1/elastic/Interlex_pr/_search" method="get" summary="General Elasticsearch" %}
{% swagger-description %}
The pass-through is accessible at https://scicrunch.org/api/1/elastic.  Similar to standard Elasticsearch APIs you must then supply an index and an action.  In this case the Interlex index (Interlex_pr) and the search command (_search).

\




\


Documentation on the Elasticsearch Search API is available at https://www.elastic.co/guide/en/elasticsearch/reference/6.8/search.html 
{% endswagger-description %}

{% swagger-parameter in="path" name="api_key" type="string" %}
Your API key to access the services
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "took": 35,
    "timed_out": false,
    "_shards": {
        "total": 2,
        "successful": 2,
        "skipped": 0,
        "failed": 0
    },
    "hits": {...
```
{% endswagger-response %}
{% endswagger %}

### Interlex indices

Management of indices is accomplished via [Elasticsearch aliases](https://www.elastic.co/guide/en/elasticsearch/reference/6.8/indices-aliases.html). The index aliases are provided:

| Index Alias  | Description               |
| ------------ | ------------------------- |
| Interlex\_pr | Production Interlex index |

Using aliases will allow for testing on updates and enhancements to the  index structure.  If needed additional aliases can be constructed for specialized testing.
