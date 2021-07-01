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

```text
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
}
```

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
```

## Search for dataset by title

This search looks for a dataset by title.

#### POST

```text
https://scicrunch.org/api/1/elastic/SPARC_PortalDatasets_dev/_search?api_key=####
```

#### JSON Body

```text
{
    "size": 20,
    "from": 0,
    "query": {
        "query_string": {
            "fields": [
                "item.names.name"
            ],
            "query": "(Generic) AND (rat) AND (stomach) AND (scaffold)"
        }
    }
}
```

#### Result

```text
{
    "took": 22,
    "timed_out": false,
    "_shards": {
        "total": 2,
        "successful": 2,
        "skipped": 0,
        "failed": 0
    },
    "hits": {
        "total": 1,
        "max_score": 7.7667675,
        "hits": [
            {
                "_index": "scr_017041-sparc_portal-ks-2021jun22",
                "_type": "ks",
                "_id": "DOI:10.26275/dn1d-owj9",
                "_score": 7.7667675,
                "_source": {
                    "item": {
                        "version": {
                            "keyword": "1.1.2"
                        },
                        "types": [
                            {
                                "curie": "ilx:0102834",
                                "name": "Dataset",
                                "type": "category"
                            }
                        ],
                        "contentTypes": [
                            {
                                "curie": "ilx:0381348",
                                "name": "product"
                            }
                        ],
                        "names": [
                            {
                                "nameType": "Complete Data Set",
                                "name": "Generic rat stomach scaffold"
                            }
                        ],
                        "statistics": {
                            "files": {
                                "count": "24"
                            },
                            "directory": {
                                "count": "4"
                            },
                            "bytes": {
                                "count": "5582424"
                            }
                        }, ...
```
