---
description: >-
  A description of competency searches for MAP-Core including searches that are
  currently supported and searches to be supported in the future
---

# MAP-Core Competency Searches

## Search for all images

This search looks for all datasets that contain an image via the data file mimetype

#### POST

```text
https://scicrunch.org/api/1/elastic/SPARC_PortalDatasets_pr/_search?api_key=####
```

#### JSON Body

```text
{
    "size": 10,
    "from": 0,
    "query": {
            "bool": {
                "must": [
                    { "match" : { "objects.mimetype.name" : "image" } }
                ]
            }
        }
}
```

#### Result

```text
{
    "took": 278,
    "timed_out": false,
    "_shards": {
        "total": 2,
        "successful": 2,
        "skipped": 0,
        "failed": 0
    },
    "hits": {
        "total": 67,
        "max_score": 1.26017,
        "hits": [ ...
```

## Search for all DOI

This search looks for all DOIs.

#### POST

```text
https://scicrunch.org/api/1/elastic/SPARC_PortalDatasets_dev/_search?api_key=####
```

#### JSON Body

````text
{
    "from": 0,
    "size": 0,
    "aggregations": {
        "doi" : {
            "composite": {
                "size": 1000,
                "sources": [
                    {
                        "curie": {"terms": {"field": "item.curie.aggregate"}}
                    }
                ],
                "after": {"curie": ""}
            }
        }
    }
}```

#### Result

```text
{
    "took": 31,
    "timed_out": false,
    "_shards": {
        "total": 2,
        "successful": 2,
        "skipped": 0,
        "failed": 0
    },
    "hits": {
        "total": 98,
        "max_score": 0.0,
        "hits": []
    },
    "aggregations": {
        "doi": {
            "after_key": {
                "curie": "doi:10.26275/zxe9-o3ss"
            },
            "buckets": [
                {
                    "key": {
                        "curie": "doi:10.26275/0ag5-j3x7"
                    },
                    "doc_count": 1
                }, ...
````
