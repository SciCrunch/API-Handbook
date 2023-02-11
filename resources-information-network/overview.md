# Overview

## Introduction

The Resources Information Network (RIN) APIs are provided via an ElasticSearch endpoint.  &#x20;

### Access to the RIN APIs

Access to the RIN API is provided via an Elasticsearch pass-through.

{% swagger method="post" path="" baseUrl="https://scicrunch.org/api/1/elastic/<index>/_search?api_key=####" summary="General Elasticsearch" %}
{% swagger-description %}
The pass-through is accessible at https://scicrunch.org/api/1/elastic.  Similar to standard Elasticsearch APIs you must then supply an index and an action.  In this case the index, the type and the search command (_search).

\




\


Documentation on the Elasticsearch Search API is available at https://www.elastic.co/guide/en/elasticsearch/reference/6.8/search.html 
{% endswagger-description %}

{% swagger-parameter in="path" name="index" required="true" %}
Production RIN indices
{% endswagger-parameter %}

{% swagger-parameter in="path" name="api_key" required="true" %}
Your API key to access the services
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```json
{
    "took": 23,
    "timed_out": false,
    "_shards": {
        "total": 2,
        "successful": 2,
        "skipped": 0,
        "failed": 0
    },
    "hits": {...}
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="the api key is incorrect" %}
```json
{
    "error": {
        "root_cause": [
            {
                "type": "illegal_argument_exception",
                "reason": "request [/RIN_Addgene_pr/rin/_search] contains unrecognized parameter: [api_key]"
            }
        ],
        "type": "illegal_argument_exception",
        "reason": "request [/RIN_Addgene_pr/rin/_search] contains unrecognized parameter: [api_key]"
    },
    "status": 400
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="such as "no api key"" %}
```json
{
    "error": {
        "root_cause": [
            {
                "type": "security_exception",
                "reason": "action [indices:data/read/search] requires authentication",
                "header": {
                    "WWW-Authenticate": [
                        "Bearer realm=\"security\"",
                        "ApiKey",
                        "Basic realm=\"security\" charset=\"UTF-8\""
                    ]
                }
            }
        ],
        "type": "security_exception",
        "reason": "action [indices:data/read/search] requires authentication",
        "header": {
            "WWW-Authenticate": [
                "Bearer realm=\"security\"",
                "ApiKey",
                "Basic realm=\"security\" charset=\"UTF-8\""
            ]
        }
    },
    "status": 401
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="the index or the server uri is incorrect" %}
```json
{
    "error": {
        "root_cause": [
            {
                "type": "index_not_found_exception",
                "reason": "no such index",
                "resource.type": "index_or_alias",
                "resource.id": "RIN_Addgene",
                "index_uuid": "_na_",
                "index": "RIN_Addgene"
            }
        ],
        "type": "index_not_found_exception",
        "reason": "no such index",
        "resource.type": "index_or_alias",
        "resource.id": "RIN_Addgene",
        "index_uuid": "_na_",
        "index": "RIN_Addgene"
    },
    "status": 404
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="the query is incorrect" %}
```json
{
    "error": {
        "root_cause": [
            {
                "type": "json_parse_exception",
                "reason": "Unexpected character ('=' (code 61)): was expecting a colon to separate field name and value\n at [Source: org.elasticsearch.transport.netty4.ByteBufStreamInput@4eccf1fd; line: 5, column: 25]"
            }
        ],
        "type": "json_parse_exception",
        "reason": "Unexpected character ('=' (code 61)): was expecting a colon to separate field name and value\n at [Source: org.elasticsearch.transport.netty4.ByteBufStreamInput@4eccf1fd; line: 5, column: 25]"
    },
    "status": 500
}
```
{% endswagger-response %}
{% endswagger %}



### RIN indices

Management of indices is accomplished via [Elasticsearch aliases](https://www.elastic.co/guide/en/elasticsearch/reference/6.8/indices-aliases.html). The index aliases are provided:

| Index Alias                        | Description                                  |
| ---------------------------------- | -------------------------------------------- |
| RIN\_Tool\_pr                      | Production tools index                       |
| RIN\_Antibody\_pr                  | Production antibodies index                  |
| RIN\_CellLine\_pr                  | Production cell lines index                  |
| RIN\_Organism\_pr                  | Production organisms index                   |
| RIN\_Addgene\_pr,RIN\_DGRC\_\*\_pr | Production plasmids (AddGene & DGRC) indices |
| RIN\_BioSample\_pr                 | Production biosamples index                  |
| RIN\_Protocols\_pr                 | Production protocols index                   |
| \*\_pr                             | Production all indices                       |

Using aliases will allow for testing on updates and enhancements to the  index structure.  If needed additional aliases can be constructed for specialized testing.
