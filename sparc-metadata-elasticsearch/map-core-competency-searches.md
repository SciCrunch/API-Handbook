---
description: >-
  A description of competency searches for MAP-Core including searches that are
  currently supported and searches to be supported in the future
---

# MAP-Core Competency Searches

## Search for all images

This search looks for all datasets that contain an image via the data file mimetype

### POST

```
https://api.scicrunch.io/elastic/v1//SPARC_PortalDatasets_pr/_search?api_key=####
```

### JSON Body

```
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

### Result

```
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

## Boolean Filter Search

This search finds data given by generating a boolean query across facets. Currently this is also combined with an optional text based search, although this may be removed in future.

These queries are generated in sparc-api [here](https://github.com/nih-sparc/sparc-api/blob/eb53aaa7b9904c0fabfe522db7cd8b8c97ff7608/app/process_kb_results.py#L92)

(In use as of 2021/06/11)

### POST

```
https://api.scicrunch.io/elastic/v1/SPARC_PortalDatasets_pr/_search?api_key=####
```

### JSON Body example

```yaml
{
  "size": 10,
  "from": 0,
  "query": {
    "query_string": {
      "query": "(Ardell) AND attributes.subject.sex.value:((male) OR (female))  AND anatomy.organ.name.aggregate:((heart))"
    }
  }
}
```

### Result

```yaml
{
    "took": 2070,
    "timed_out": false,
    "_shards": {
        "total": 2,
        "successful": 2,
        "skipped": 0,
        "failed": 0
    },
    "hits": {
        "total": 5,
        "max_score": 5.709837,
        "hits": [
            {
                "_index": "scr_017041-sparc_datasets-ks_2021apr28",
                "_type": "ks",
                "_id": "DOI:10.26275/w4my-puqm",
                "_score": 5.709837,
//...
```

## Available Facets Query

This query requests available facets for a given parameter in the 'hits' object.

Implementation of this can be seen in sparc-api [here](https://github.com/nih-sparc/sparc-api/blob/eb53aaa7b9904c0fabfe522db7cd8b8c97ff7608/app/process_kb_results.py#L59)

(In use as of 2021/06/11)

### POST

```
https://api.scicrunch.io/elastic/v1/SPARC_PortalDatasets_pr/_search?api_key=####
```

### JSON Body example

```yaml
{
  "from": 0,
  "size": 0,
  "aggregations": {
    "genotype": {
      "terms": {
        "field": "anatomy.organ.name.aggregate",
        "size": 200,
        "order": [
          {
            "_count": "desc"
          },
          {
            "_key": "asc"
          }
        ]
      }
    }
  }
}
```

### Result

```yaml
{
    "took": 2,
    "timed_out": false,
    "_shards": {
        "total": 2,
        "successful": 2,
        "skipped": 0,
        "failed": 0
    },
    "hits": {
        "total": 88,
        "max_score": 0.0,
        "hits": []
    },
    "aggregations": {
        "genotype": {
            "doc_count_error_upper_bound": 0,
            "sum_other_doc_count": 0,
            "buckets": [
                {
                    "key": "heart",
                    "doc_count": 21
                },
//...
```

## Search for all DOI

This search looks for all DOIs.

### POST

```yaml
https://api.scicrunch.io/elastic/v1/SPARC_PortalDatasets_dev/_search?api_key=####
```

### JSON Body Example

```yaml
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
```

### Result

```yaml
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

### POST

```yaml
https://api.scicrunch.io/elastic/v1/SPARC_PortalDatasets_dev/_search?api_key=####
```

### JSON Body Example

```yaml
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

### Result

```yaml
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
