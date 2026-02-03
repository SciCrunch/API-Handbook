# Overview

## Introduction

The SPARC metadata APIs are provided via an ElasticSearch endpoint.  The metadata is extracted from K-Core's metadata export and processed via the FDI Lab's Foundry - a message-oriented, horizontally scalable ETL system for scientific data integration and enhancement (Ozyurt and Grethe 2018).&#x20;

### Access to the metadata APIs

Access to the metadata API is provided via an Elasticsearch pass-through.

## General Elasticsearch

<mark style="color:blue;">`GET`</mark> https://api.scicrunch.io/elastic/v1//SPARC\_PortalDatasets\_pr/\_search

The pass-through is accessible at https://api.scicrunch.io/elastic/v1/.  Similar to standard Elasticsearch APIs you must then supply an index and an action.  In this case the SPARC Portal Dataset metadata (SPARC\_PortalDatasets\_pr) and the search command (\_search).\
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

### SPARC metadata indices

Management of indices is accomplished via [Elasticsearch aliases](https://www.elastic.co/guide/en/elasticsearch/reference/6.8/indices-aliases.html). Three index aliases are provided:

| Index Alias                | Description                                               |
| -------------------------- | --------------------------------------------------------- |
| SPARC\_PortalDatasets\_pr  | Production metadata index for SPARC Portal datasets       |
| SPARC\_PortalDatasets\_dev | Development metadata index for SPARC Portal datasets      |
| SPARC\_PortalDatasets\_old | Prior production metadata index for SPARC Portal datasets |

Using aliases will allow for testing on updates and enhancements to the metadata index structure.  If needed additional aliases can be constructed for specialized testing.

### References

Ozyurt, I. B., & Grethe, J. S. (2018). Foundry: a message-oriented, horizontally scalable ETL system for scientific data integration and enhancement. Database : the journal of biological databases and curation, 2018, bay130. [https://doi.org/10.1093/database/bay130](https://doi.org/10.1093/database/bay130)
