# Overview

## Introduction

The SPARC metadata APIs are provided via an ElasticSearch endpoint.  The metadata is extracted from K-Core's metadata export and processed via the FDI Lab's Foundry - a message-oriented, horizontally scalable ETL system for scientific data integration and enhancement \(Ozyurt and Grethe 2018\). 

### Access to the metadata APIs

Access to the metadata API is provided via an Elasticsearch pass-through.

{% api-method method="get" host="https://scicrunch.org/api" path="/1/elastic/elastic/SPARC\_PortalDatasets\_pr/\_search" %}
{% api-method-summary %}
General Elasticsearch
{% endapi-method-summary %}

{% api-method-description %}
The pass-through is accessible at https://scicrunch.org/api/1/elastic.  Similar to standard Elasticsearch APIs you must then supply an index and an action.  In this case the SPARC Portal Dataset metadata \(SPARC\_PortalDatasets\_pr\) and the search command \(\_search\).  
  
Documentation on the Elasticsearch Search API is available at https://www.elastic.co/guide/en/elasticsearch/reference/6.8/search.html 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="api\_key" type="string" required=true %}
Your API key to access the services
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### SPARC metadata indices

Management of indices is accomplished via [Elasticsearch aliases](https://www.elastic.co/guide/en/elasticsearch/reference/6.8/indices-aliases.html). Three index aliases are provided:

| Index Alias | Description |
| :--- | :--- |
| SPARC\_PortalDatasets\_pr | Production metadata index for SPARC Portal datasets |
| SPARC\_PortalDatasets\_dev | Development metadata index for SPARC Portal datasets |
| SPARC\_PortalDatasets\_old | Prior production metadata index for SPARC Portal datasets |

Using aliases will allow for testing on updates and enhancements to the metadata index structure.  If needed additional aliases can be constructed for specialized testing.

### References

Ozyurt, I. B., & Grethe, J. S. \(2018\). Foundry: a message-oriented, horizontally scalable ETL system for scientific data integration and enhancement. Database : the journal of biological databases and curation, 2018, bay130. [https://doi.org/10.1093/database/bay130](https://doi.org/10.1093/database/bay130)

