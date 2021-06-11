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

## Boolean Filter Search

This search finds data given by generating a boolean query across facets. Currently this is also combined with an optional text based search, although this may be removed in future.

These queries are generated in sparc-api [here](https://github.com/nih-sparc/sparc-api/blob/eb53aaa7b9904c0fabfe522db7cd8b8c97ff7608/app/process_kb_results.py#L92)

(In use as of 2021/06/11)

#### POST

```text
https://scicrunch.org/api/1/elastic/SPARC_PortalDatasets_pr/_search?api_key=####
```

#### JSON Body example

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

#### Result

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

#### POST

```text
https://scicrunch.org/api/1/elastic/SPARC_PortalDatasets_pr/_search?api_key=####
```

#### JSON Body example

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

#### Result

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
