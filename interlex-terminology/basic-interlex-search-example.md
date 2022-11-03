# Basic Interlex Search Example

## Search for term by identifier

This search looks for a term that matches the supplied identifier

### POST

```
https://scicrunch.org/api/1/elastic/Interlex_pr/_search?api_key=####
```

### JSON Body

```
{
    "size": 20,
    "from": 0,
    "query": {
    	"bool": {
    	    "must": [ {
		"match_phrase": {
		    "existing_ids.curie": {
		    "query": "NCBITaxon:9606"
		    }
	        }
	    } ]
        }
    }
}
```

### Result

```
{
    "took": 2,
    "timed_out": false,
    "_shards": {
        "total": 5,
        "successful": 5,
        "skipped": 0,
        "failed": 0
    },
    "hits": {
        "total": 1,
        "max_score": 19.45221,
        "hits": [
            {
                "_index": "interlex_2019nov01",
                "_type": "term",
                "_id": "ilx_0105114",
                "_score": 19.45221,
                "_source": {
                    "ilx": "ilx_0105114",
                    "label": "Human",
                    "definition": "A mammal of the primate order and genus homo.",
                    "comment": "",
                    "type": "term",
                    "status": "0",
                    "synonyms": [
                        {
                            "literal": "homo sapien",
                            "type": ""
                        },
                        {
                            "literal": "homo sapiens",
                            "type": ""
                        },
                        {
                            "literal": "man",
                            "type": ""
                        }
                    ],
                    "existing_ids": [
                        {
                            "curie": "BIRNLEX:516",
                            "iri": "http://uri.neuinfo.org/nif/nifstd/birnlex_516",
                            "preferred": "0"
                        },
                        {
                            "curie": "ILX:0105114",
                            "iri": "http://uri.interlex.org/base/ilx_0105114",
                            "preferred": "0"
                        },
                        {
                            "curie": "NCBITaxon:9606",
                            "iri": "http://purl.obolibrary.org/obo/NCBITaxon_9606",
                            "preferred": "1"
                        },
                        {
                            "curie": "GBIF:102481489",
                            "iri": "http://www.gbif.org/species/102481489",
                            "preferred": "0"
                        }
                    ],
                    "superclasses": [
                        {
                            "ilx": "ilx_0105088",
                            "label": "Homo"
                        }
                    ],
                    "ancestors": [
                        {
                            "ilx": "ilx_0105088",
                            "label": "Homo"
                        },
                        {
                            "ilx": "ilx_0105089",
                            "label": "Homo Pan Gorilla group"
                        },
                        {
                            "ilx": "ilx_0105086",
                            "label": "Hominidae"
                        },
                        {
                            "ilx": "ilx_0105087",
                            "label": "Hominoidea"
                        },
                        {
                            "ilx": "ilx_0101695",
                            "label": "Catarrhini"
                        },
                        {
                            "ilx": "ilx_0110627",
                            "label": "Simiiformes"
                        },
                        {
                            "ilx": "ilx_0104889",
                            "label": "Haplorrhini"
                        },
                        {
                            "ilx": "ilx_0109341",
                            "label": "Primate"
                        },
                        {
                            "ilx": "ilx_0103972",
                            "label": "Euarchontoglires"
                        },
                        {
                            "ilx": "ilx_0103988",
                            "label": "Eutheria"
                        },
                        {
                            "ilx": "ilx_0111679",
                            "label": "Theria"
                        },
                        {
                            "ilx": "ilx_0106498",
                            "label": "Mammal"
                        },
                        {
                            "ilx": "ilx_0100551",
                            "label": "Amniota"
                        },
                        {
                            "ilx": "ilx_0111643",
                            "label": "Tetrapoda"
                        },
                        {
                            "ilx": "ilx_0110340",
                            "label": "Sarcopterygii"
                        },
                        {
                            "ilx": "ilx_0103987",
                            "label": "Euteleostomi"
                        },
                        {
                            "ilx": "ilx_0111564",
                            "label": "Teleostomi"
                        },
                        {
                            "ilx": "ilx_0104698",
                            "label": "Gnathostomata"
                        },
                        {
                            "ilx": "ilx_0112412",
                            "label": "Vertebrata"
                        },
                        {
                            "ilx": "ilx_0102612",
                            "label": "Craniata"
                        },
                        {
                            "ilx": "ilx_0102135",
                            "label": "Chordata"
                        },
                        {
                            "ilx": "ilx_0103158",
                            "label": "Deuterostomia"
                        },
                        {
                            "ilx": "ilx_0102337",
                            "label": "Coelomata"
                        },
                        {
                            "ilx": "ilx_0101278",
                            "label": "Bilateria"
                        },
                        {
                            "ilx": "ilx_0103978",
                            "label": "Eumetazoa"
                        },
                        {
                            "ilx": "ilx_0106844",
                            "label": "Metazoa"
                        },
                        {
                            "ilx": "ilx_0103976",
                            "label": "Eukaryota"
                        },
                        {
                            "ilx": "ilx_0108133",
                            "label": "Organism"
                        },
                        {
                            "ilx": "ilx_0106552",
                            "label": "Material entity"
                        },
                        {
                            "ilx": "ilx_0105405",
                            "label": "Independent continuant"
                        },
                        {
                            "ilx": "ilx_0102514",
                            "label": "Continuant"
                        }
                    ],
                    "relationships": [],
                    "annotations": [
                        {
                            "term_ilx": "ilx_0105114",
                            "term_label": "Human",
                            "annotation_term_ilx": "ilx_0381360",
                            "annotation_term_label": "hasDbXref",
                            "value": "http://neurolex.org/wiki/birnlex_516"
                        }
                    ],
                    "ontologies": [
                        {
                            "url": "https://raw.githubusercontent.com/tgbugs/nlxeol/master/neurolex_full.csv"
                        }
                    ]
                }
            }
        ]
    }
}
```

