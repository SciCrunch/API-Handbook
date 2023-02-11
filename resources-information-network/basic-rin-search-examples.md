# Basic RIN Search Examples

### POST

```
https://scicrunch.org/api/1/elastic/<index>/_search?api_key=####
```



## Search all resources

This search looks for all resources of the current RIN index.

For example, searching all registry resources (Tools).

### JSON Body

```json
{
    "size": 20,
    "from": 0,
    "aggregations": {
        "Resource Type": {
            "terms": {
                "field": "item.types.name.aggregate",
                "size": 200
            }
        },
        "Keywords": {
            "terms": {
                "field": "item.keywords.keyword",
                "size": 200
            }
        },
        "Organism": {
            "terms": {
                "field": "organisms.related.species.name.aggregate",
                "size": 200
            }
        },
        "Related Condition": {
            "terms": {
                "field": "diseases.related.name.aggregate",
                "size": 200
            }
        },
        "Funding Agency": {
            "terms": {
                "field": "supportingAwards.agency.name.aggregate",
                "size": 200
            }
        },
        "Website Status": {
            "terms": {
                "field": "item.status",
                "size": 200
            }
        },
        "Mentions": {
            "terms": {
                "field": "mentions.availability.keyword",
                "size": 200
            }
        }
    }
}
```

### Result

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
    "hits": {
        "total": 22140,
        "max_score": 1.0,
        "hits": [
            {
                "_index": "scr_005400-registry_resources_pr-rin-2022apr21",
                "_type": "rin",
                "_id": "rrid:scr_019389",
                "_score": 1.0,
                "_source": {
                    "item": {
                    ...
}
```

## Search for resources by keywords

This search looks for all resources that match keywords.

For example, searching Cell Line resources with keyword (CVCL\_0030) and Vendor (ATCC).

### JSON Body

```json
{
    "size": 20,
    "from": 0,
    "query": {
        "bool": {
            "must": [
                {
                    "query_string": {
                        "fields": [
                            "vendors.name"
                        ],
                        "query": "\"ATCC\"",
                        "default_operator": "and",
                        "lenient": "true"
                    }
                },
                {
                    "query_string": {
                        "fields": [
                            "*"
                        ],
                        "query": "\"CVCL_0030\"",
                        "type": "cross_fields",
                        "default_operator": "and",
                        "lenient": "true"
                    }
                }
            ],
            "should": [
                {
                    "match": {
                        "item.name": {
                            "query": "\"CVCL_0030\"",
                            "boost": 20
                        }
                    }
                },
                {
                    "term": {
                        "item.name.aggregate": {
                            "term": "CVCL_0030",
                            "boost": 2000
                        }
                    }
                }
            ]
        }
    },
    "aggregations": {
        "Vendor": {
            "terms": {
                "field": "vendors.name.aggregate",
                "size": 200
            }
        },
        "Category": {
            "terms": {
                "field": "item.keywords.keyword",
                "size": 200
            }
        },
        "Disease": {
            "terms": {
                "field": "diseases.host.name.aggregate",
                "size": 200
            }
        },
        "Organism": {
            "terms": {
                "field": "organisms.origin.species.name.aggregate",
                "size": 200
            }
        },
        "References": {
            "terms": {
                "field": "references.curie.aggregate",
                "size": 200
            }
        },
        "Sex": {
            "terms": {
                "field": "attributes.sex.value",
                "size": 200
            }
        },
        "Mentions": {
            "terms": {
                "field": "mentions.availability.keyword",
                "size": 200
            }
        },
        "Issues": {
            "terms": {
                "field": "issues.status",
                "size": 200
            }
        }
    }
}
```

### Result

```json
{
    "took": 11,
    "timed_out": false,
    "_shards": {
        "total": 2,
        "successful": 2,
        "skipped": 0,
        "failed": 0
    },
    "hits": {
        "total": 35,
        "max_score": 40.370987,
        "hits": [
            {
                "_index": "scr_013869-cellosaurus_celllines_pr-rin-2022apr27",
                "_type": "rin",
                "_id": "rrid:cvcl_0030-atcc-ccl-2",
                "_score": 40.370987,
                "_source": {
                    "item": {
                        "types": [
                            {
                                "curie": "ilx:0101850",
                                "name": "cell line"
                            },
                            {
                                "type": "supercategory"
                            }
                        ],
                        ...
}
```



## Search for resource by identifier

This search looks for a resource that matches the supplied identifier (RRID#).

For example, searching registry resource, RRID:SCR\_000415

### JSON Body

```
{
    "size": 1000,
    "from": 0,
    "query": {
        "query_string": {
            "fields": [
                "rrid.curie"
            ],
            "query": "RRID\\:SCR_000415"
        }
    }
}
```

### Result

```json
{
    "took": 3,
    "timed_out": false,
    "_shards": {
        "total": 2,
        "successful": 2,
        "skipped": 0,
        "failed": 0
    },
    "hits": {
        "total": 1,
        "max_score": 12.198048,
        "hits": [
            {
                "_index": "scr_005400-registry_resources_pr-rin-2022apr21",
                "_type": "rin",
                "_id": "rrid:scr_000415",
                "_score": 12.198048,
                "_source": {
                    "item": {
                        "supercategory": [
                            {
                                "name": "Resource",
                                "type": "supercategory"
                            }
                        ],
                        "contentTypes": [
                            {
                                "curie": "ilx:0381348",
                                "name": "product"
                            }
                        ],
                        "language": "en",
                        "description": "A software package for control of automated microscopes that runs as a plugin in ImageJ, works with virtually all scientific grade microscope equipment, and has a simple interface towards routine image acquisition strategies such as time-lapse, z- stacks, multi-channel, and multi-position acquisition. In addition, it uses a device abstraction layer available from various programming environments (such a C, Java, Python, Matlab and LabView), facilitating development of novel approaches to image acquisition. Manager has a simple and clean user interface, through which it lets users execute common microscope image acquisition strategies such as time-lapses, multi-channel imaging, z-stacks, and combinations thereof. Manager works with microscopes from all four major manufacturers (Leica, Nikon, Olympus and Zeiss), most scientific-grade cameras and many peripherals (stages, filter wheels, shutters, etc.) used in microscope imaging.",
                        "identifier": "SCR_000415",
                        "docid": "rrid:scr_000415",
                        "uuid": "eda7a99e-7e65-5055-b407-fd05d417e085",
                        "synonyms": [
                            {
                                "name": "Micro-Manager Open Source Microscopy Software"
                            }
                        ],
                        "types": [
                            {
                                "name": "software application",
                                "type": "category"
                            },
                            {
                                "name": "data processing software",
                                "type": "category"
                            },
                            {
                                "name": "data acquisition software",
                                "type": "category"
                            },
                            {
                                "name": "software resource",
                                "type": "category"
                            }
                        ],
                        "keywords": [
                            {
                                "keyword": "microscopy"
                            },
                            {
                                "keyword": "plugin"
                            },
                            {
                                "keyword": "data acquisition"
                            },
                            {
                                "keyword": "software package"
                            },
                            {
                                "keyword": "automated microscope"
                            }
                        ],
                        "curie": "SCR_000415",
                        "availability": [
                            {
                                "description": "",
                                "keyword": ""
                            }
                        ],
                        "alternateIdentifiers": [
                            {
                                "identifier": ""
                            }
                        ],
                        "abbreviations": [
                            {
                                "name": "Micro-Manager"
                            }
                        ],
                        "name": "Micro-Manager"
                    },
                    "authority": {
                        "name": "SciCrunch Registry"
                    },
                    "distributions": {
                        "current": [
                            {
                                "type": "landing page",
                                "uri": "http://micro-manager.org"
                            }
                        ],
                        "deprecated": [
                            {
                                "uri": ""
                            }
                        ],
                        "alternate": [
                            {
                                "uri": "http://www.nitrc.org/projects/micromanager"
                            }
                        ]
                    },
                    "rrid": {
                        "is_unique": "true",
                        "curie": "RRID:SCR_000415",
                        "properCitation": "Micro-Manager (RRID:SCR_000415)"
                    },
                    "disco": {
                        "v_uuid": "eda7a99e-7e65-5055-b407-fd05d417e085"
                    },
                    "graph": {
                        "parent": [
                            {
                                "resource": {
                                    "identifier": "SCR_010605",
                                    "name": "University of California at San Francisco; California; USA"
                                },
                                "relationship": {
                                    "identifier": "7",
                                    "name": "has_parent_organization"
                                }
                            }
                        ],
                        "related": [
                            {
                                "resource": {
                                    "identifier": "SCR_018680",
                                    "name": "ImageJ"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            }
                        ],
                        "relationships": [
                            {
                                "resource": {
                                    "identifier": "SCR_003430",
                                    "name": "NeuroImaging Tools and Resources Collaboratory (NITRC)"
                                },
                                "relationship": {
                                    "identifier": "4",
                                    "name": "is_listed_by"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_018680",
                                    "name": "ImageJ"
                                },
                                "relationship": {
                                    "identifier": "6",
                                    "name": "is_related_to"
                                }
                            },
                            {
                                "resource": {
                                    "identifier": "SCR_010605",
                                    "name": "University of California at San Francisco; California; USA"
                                },
                                "relationship": {
                                    "identifier": "7",
                                    "name": "has_parent_organization"
                                }
                            }
                        ]
                    },
                    "diseases": {
                        "related": [
                            {
                                "role": "Related Disease",
                                "name": ""
                            }
                        ]
                    },
                    "supportingAwards": [
                        {
                            "agency": {
                                "name": ""
                            }
                        }
                    ],
                    "references": [
                        {
                            "curie": ""
                        }
                    ],
                    "organisms": {
                        "related": [
                            {
                                "role": "Related Species",
                                "species": {
                                    "name": ""
                                }
                            }
                        ]
                    },
                    "dataItem": {
                        "dataTypes": [
                            "item",
                            "authority",
                            "distributions",
                            "rrid",
                            "disco",
                            "graph",
                            "diseases",
                            "supportingAwards",
                            "references",
                            "organisms"
                        ]
                    },
                    "provenance": {
                        "ingestMethod": "dkNET",
                        "ingestTarget": "",
                        "filePattern": "",
                        "ingestTime": "20230209T050017+0000",
                        "creationDate": [
                            "20220129T080201+0000"
                        ],
                        "docId": "61f4f47948932023e322e24e",
                        "primaryKey": "SCR_000415"
                    },
                    "mentions": [
                        {
                            "totalResourceMentions": {
                                "count": 229
                            },
                            "availability": {
                                "keyword": "available"
                            },
                            "totalRRIDMentions": {
                                "count": 31
                            },
                            "totalMentions": {
                                "count": 247
                            },
                            "timestamp": "2023-02-09 05:00:17.441"
                        }
                    ]
                }
            }
        ]
    }
}
```

&#x20;
