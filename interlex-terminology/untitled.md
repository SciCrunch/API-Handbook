# Overview

## Introduction

The InterLex APIs are provided via an ElasticSearch endpoint.  &#x20;

### Access to the InterLex APIs

Access to the InterLex API is provided via an Elasticsearch pass-through.

## General Elasticsearch

<mark style="color:blue;">`GET`</mark> https://api.scicrunch.io/elastic/v1/Interlex\_pr/\_search

The pass-through is accessible at https://api.scicrunch.io/elastic/v1/.  Similar to standard Elasticsearch APIs you must then supply an index and an action.  In this case the Interlex index (Interlex\_pr) and the search command (\_search).\
\
Documentation on the Elasticsearch Search API is available at https://www.elastic.co/guide/en/elasticsearch/reference/6.8/search.html&#x20;

#### Path Parameters

| Name     | Type   | Description                         |
| -------- | ------ | ----------------------------------- |
| api\_key | string | Your API key to access the services |

{% tabs %}
{% tab title="200 " %}
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
{% endtab %}
{% endtabs %}

### Interlex indices

Management of indices is accomplished via [Elasticsearch aliases](https://www.elastic.co/guide/en/elasticsearch/reference/6.8/indices-aliases.html). The index aliases are provided:

| Index Alias  | Description               |
| ------------ | ------------------------- |
| Interlex\_pr | Production Interlex index |

Using aliases will allow for testing on updates and enhancements to the  index structure.  If needed additional aliases can be constructed for specialized testing.
