---
description: >-
  The data model for results from Elasticsearch is provided below. We provide
  documentation as "comments" within a trimmed JSON document for a SPARC
  dataset.
---

# SPARC Datasets Elasticsearch JSON Data Model

Tarotin, I., Mastitskaya, S., Ravagli, E., holder, david, & Aristovich, K. (2022). Temporal dispersion in porcine subdiaphragmatic nerves ex vivo (Version 1) \[Data set]. SPARC Consortium. https://doi.org/10.26275/4MFY-Y7BJ

<pre class="language-json"><code class="lang-json"><strong>### Dataset ID for the returned dataset.  This is part of the core
</strong><strong>### Elasticsearch metadata.  This is an example of one dataset which
</strong><strong>### would be found within the 'hits' for the search
</strong><strong>    "hits": {
</strong>        "total": 250,
        "max_score": 1.0,
        "hits": [
<strong>
</strong><strong>### Elasticsearch document ID which is the SPARC Portal dataset ID
</strong><strong>"_id": "229"
</strong>
### _source contains the return results from Elasticsearch for the dataset
"_source": {

### item contains dataset metadata
    "item": {

### Version information for the JSON results
        "version": {
            "keyword": "1.1.5",
            "description": "Updates for multi-field datacite path information"
        },
        
### The type of datase (e.g. computational model, dataset, ...) 
        "types": [
            {
                "name": "dataset",
                "type": "category"
            }
        ],
 
### Is the object represented informational or something that can be accessed (product)      
        "contentTypes": [
            {
                "curie": "ilx:0381348",
                "name": "product"
            }
        ],

### General statistics about the dataset
        "statistics": {
            "directory": {
                "count": "361"
            },
            "files": {
                "count": "2864"
            },
            "subjects": {
                "count": "7"
            },
            "bytes": {
                "count": "89148729951"
            }
        },
        
### Dataset keywords supplied by the authors
        "keywords": [
            {
                "keyword": "vagus"
            },
        ],
    
### Publication information (published, revision, embargo) 
        "published": {
            "status": "revision",
            "boolean": "true"
        },
        
### Dataset name (title) and description (abstract)
        "dataset": {
            "description": "It includes electrophysiological measurements in response to vagus nerve stimulation taken in swine.",
            "name": "Vagus Nerve Stimulation Mapping in Swine"
        },
    
### Curator notes and additional information about the dataset
        "readme": {
            "description": "**Study Purpose:** To investigate neck muscle responses to vagus nerve stimulation applied at different locations on the vagus nerve.\n\n**Data Collection:** Electrophysiology and electromyography was collected using a Tucker Davis Technology system in swine in response to vagus nerve stimulation.\n\n**Primary Conclusion:** The superior laryngeal branch is activated via current leakage from the stimulation electrode cuff insulation while stimulating caudal to the branching point, and superior laryngeal activation can be avoided by moving the stimulation electrode caudally away from the branch. Activation of the recurrent laryngeal branch fibers, which run under the electrode cuff at all locations in the cervical vagus, cannot be avoided via moving the stimulation electrode. The threshold for activation of the recurrent laryngeal branch fibers could be modulated by hundreds of microamperes, but EMG responses associated with recurrent laryngeal branch fiber activation were always observed before any other response (heart rate or breathing changes) associated with other fiber activation. \n\n---\n\n**Experimental Design:** Intrafascicular electrodes were placed within the vagus nerve to record electroneurographic (ENG) responses, and needle electrodes were placed in the vagal-innervated neck muscles to record electromyographic (EMG) responses. Bipolar stimulation was delivered at 30 Hz using symmetric biphasic pulses with 200 μs per phase and amplitudes from 50 to 3000 μA evaluated in random order. Stimulation was typically delivered for 30 s at each amplitude with at least 1 min rest between trials to allow cardiac responses to return to baseline; in some cases, stimulation was delivered for 3 s at each amplitude with at least 10 s rest due to time constraints.\n\n**Completeness:** Dataset is complete.\n\n**Subjects &#x26; Samples:** Male (n=3) and female (n=4) domestic pigs between 3-4 months of age were used in this study.\n\n**Primary vs derivative data:** Each specific nested data folder nested under primary data (sub-) includes raw electrophysiology recordings organized by individual session subfolders. Parameters of the individual sessions can be found in the performances.xlsx file. There is no derivative data folder.\n\n**Code Availability:** Source Matlab code used to analyze all the electrophysiology and electromyography data are provided in the code folder. Use the notes files in the \"docs\" folder to understand entries into the code. There are multiple tabs (bottom right in excel) for each notes file."
        },
        
### Dataset name (potentially short display title)
        "name": "Vagus nerve stimulation mapping in swine",
        
### Pennsieve dataset identifier (UUID)
        "identifier": "N:dataset:2b9d01f8-41a5-47f9-9168-e809edcae6cb",
        
### Persistent identifier for the dataset (DOI)
        "curie": "DOI:10.26275/qw1u-zxea",
        
### Experimental modalities utilized by the dataset
        "modalities": [
            {
                "keyword": "physiology"
            },
        ],
        
### Document ID to be used for indexing document (corresponds to Portal dataset ID)
        "docid": "229",
        "description": "VNS evoked vagus nerve compound action potential and neck muscle electromyography data via stimulation at a 1 mm disk electrode at many locations on vagus nerve"
    },
    
### Funding information for dataset
    "supportingAwards": [
        {
            "identifier": "OT2OD025340",
            "agency": {
                "name": "National Institutes of Health"
            }
        },
    ],
    
### Information on data files and directories that are a part of the dataset
    "objects": [

### Checksum for the datafile 
        {
            "checksums": [
                {
                    "cypher": "sha256",
                    "hex": "39822c420ea4aab39265a6b2d45c4acfa622e0318110178b9c5470f95539be00"
                }
            ],
            
### Pennsieve identifier for the object (file or directory)
            "identifier": "package:8f8f72f5-06fb-4f35-8667-17f7b46ac5ae",
            
### If a file - the size of the file
            "bytes": {
                "count": "41715"
            },
            
### Relationship of the object to other objects
### Relationships are from the Datacite metdata model
### 
            "datacite": {
                "isSourceOf": {
                    "path": [
                        ""
                    ],
                    "relative": {
                        "path": [
                            ""
                        ]
                    }
                },
            },
            
### Object name
            "name": "subjects.xlsx",
            
### Object description
            "description": "",
            
### Additional mimetype defined in dataset manifest file
            "additional_mimetype": {
                "name": ""
            },
            
### Mimetype for a datafile
            "mimetype": {
                "name": "application/vnd.openxmlformats-officedocument.spreadsheetml.sheet"
            },
        
### Dataset indentifier and path for object
            "dataset": {
                "path": "subjects.xlsx",
                "identifier": "dataset:2b9d01f8-41a5-47f9-9168-e809edcae6cb"
            },
            
### Timestamp for the object
            "updated": {
                "timestamp": "2022-01-17T18:24:22,957212Z"
            },
            
### URL accessible locations for the object
            "distributions": {
                "current": [
                    {
                        "uri": "https://app.pennsieve.io/N:organization:618e8dd9-f8d2-4dc4-9abb-c6aaab2e78a0/datasets/N:dataset:2b9d01f8-41a5-47f9-9168-e809edcae6cb/files/v/N:package:8f8f72f5-06fb-4f35-8667-17f7b46ac5ae"
                    }
                ],
                "api": [
                    {
                        "uri": "https://api.pennsieve.io/packages/N:package:8f8f72f5-06fb-4f35-8667-17f7b46ac5ae/files/1320527"
                    }
                ]
            }
        }
    ],
    
### Pennsieve metadata for the dataset
    "pennsieve": {
        "files": {
            "count": "2880"
        },
        "owner": {
            "orcid": {
                "identifier": "0000-0003-0447-568X"
            },
            "identifier": "733",
            "first": {
                "name": "Evan"
            },
            "last": {
                "name": "Nicolai"
            }
        },
        "organization": {
            "identifier": "367",
            "name": "SPARC Consortium"
        },
        "arn": "arn:aws:s3:::pennsieve-prod-discover-publish-use1/229/1/",
        "createdAt": {
            "timestamp": "2022-04-15T20:25:12.512006Z",
            "epoch": "1650054312"
        },
        "uri": "s3://pennsieve-prod-discover-publish-use1/229/1/",
        "status": "PUBLISH_SUCCEEDED",
        "name": "Vagus nerve stimulation mapping in swine",
        "banner": {
            "uri": "https://assets.discover.pennsieve.io/dataset-assets/229/1/revisions/1/banner.png"
        },
        "firstPublishedAt": {
            "timestamp": "2022-04-15T20:25:12.50497Z",
            "epoch": "1650054312"
        },
        "versionPublishedAt": {
            "timestamp": "2022-04-15T20:25:12.512006Z",
            "epoch": "1650054312"
        },
        "license": {
            "keyword": "Creative Commons Attribution"
        },
        "version": {
            "identifier": "1"
        },
        "readme": {
            "uri": "https://assets.discover.pennsieve.io/dataset-assets/229/1/revisions/1/readme.md"
        },
        "sourceDataset": {
            "identifier": "775"
        },
        "identifier": "229",
        "records": {
            "count": "19"
        },
        "updatedAt": {
            "timestamp": "2023-03-08T17:36:15.083356Z",
            "epoch": "1678296975"
        },
        "description": "VNS evoked vagus nerve compound action potential and neck muscle electromyography data via stimulation at a 1 mm disk electrode at many locations on vagus nerve",
        "schemaVersion": {
            "identifier": "4.0"
        },
        "embargo": {
            "keyword": "false"
        },
        "revisedAt": {
            "timestamp": "2022-07-14T21:06:12.832818Z",
            "epoch": "1657832772"
        },
        "revision": {
            "identifier": "1"
        }
    },
    
### Authors for the dataset
    "contributors": [
        {
            "last": {
                "name": "Ludwig"
            },
            "curie": "ORCID:0000-0003-4889-1941",
            "name": "Ludwig, Kip",
            "affiliations": [
                {
                    "description": "Department of Biomedical Engineering, University of Wisconsin-Madison, Madison, WI, United States of America; Department of Neurosurgery, University of Wisconsin-Madison, Madison, WI, United States of America"
                }
            ],
            "uri": "https://orcid.org/0000-0003-4889-1941",
            "first": {
                "name": "Kip"
            }
        },
        
### URI accessible locations for the dataset
    "distributions": {
        "current": [
            {
                "uri": "https://app.pennsieve.io/N:organization:618e8dd9-f8d2-4dc4-9abb-c6aaab2e78a0/datasets/N:dataset:2b9d01f8-41a5-47f9-9168-e809edcae6cb"
            }
        ],
        "api": [
            {
                "uri": "https://api.pennsieve.io/datasets/N:dataset:2b9d01f8-41a5-47f9-9168-e809edcae6cb"
            }
        ]
    },
    
### Published protocols for the dataset available via Protocols.io
    "protocols": {
        "primary": [
            {
                "current": {
                    "uri": "https://www.protocols.io/view/vagus-nerve-stimulation-evoked-electroneurography-bkeyktfw"
                },
                "curie": "DOI:10.17504/protocols.io.bkeyktfw",
                "name": "Vagus Nerve Stimulation Evoked Electroneurography and Electromyography Recordings in Swine",
                "api": {
                    "uri": "https://www.protocols.io/api/v4/protocols/41144"
                }
            }
        ]
    },
    
### Information on organisms involved in the dataset.  This information includes
### identifiers from NCBI taxonomy and the taxonomic hierarchy for the species.
    "organisms": {
    
### All organisms involved in the study
        "subject": [
            {
                "strain": {
                    "name": "Landrace/Yorkshire"
                },
                "species": {
                    "curie": "NCBITaxon:9825",
                    "name": "Domestic Pig",
                    "matchingStatus": "Exact Match",
                    "parents": [
                        {
                            "curie": "ilx:0739765",
                            "name": "Pig"
                        },
                        {
                            "curie": "ilx:0739764",
                            "name": "Sus"
                        },
                    ]
                }
            }
        ],
        
### Primary organism identified for the dataset
        "primary": [
            {
                "species": {
                    "curie": "NCBITaxon:9825",
                    "name": "Domestic Pig",
                    "matchingStatus": "Exact Match",
                    "parents": [
                        {
                            "curie": "ilx:0739765",
                            "name": "Pig"
                        },
                        {
                            "curie": "ilx:0739764",
                            "name": "Sus"
                        },
                    ]
                }
            }
        ]
    },
    
### Attributes of the research subjects that are a part of the dataset.
### This is aggregated across all subjects in the dataset.
    "attributes": {
        "subject": {
            "sex": [
                {
                    "value": "male"
                },
                {
                    "value": "female"
                }
            ],
            "ageCategory": [
                {
                    "value": "adolescent"
                }
            ]
        }
    },
        
### Timestamp(s) for the dataset
    "dates": {
        "created": {
            "timestamp": "2020-07-21T23:45:49,414413Z"
        },
        "updated": [
            {
                "timestamp": "2023-05-12T20:03:14Z"
            }
        ]
    },
    
### Information for anatomical entity(s) represented in the dataset 
    "anatomy": {
        "organ": [
            {
                "curie": "UBERON:0001759",
                "name": "vagus nerve",
                "matchingStatus": "Exact Match"
            }
        ]
    },
    
### Internal processing information for the Elasticsearch document
    "provenance": {
        "ingestMethod": "WEB",
        "ingestTarget": "file:///var/data/data-cache/SCR_017041-SPARC_Datasets-KS/cleaned",
        "filePattern": "^NORM-MANIFEST-NORM-PENNSIEVE-\\w{8}-\\w{4}-\\w{4}-\\w{4}-\\w{12}\\.json$",
        "ingestTime": "20230517T012524+0000",
        "creationDate": [
            "20230517T012459+0000"
        ],
        "docId": "64642ceb93879a3172d262f2",
        "primaryKey": "N:dataset:2b9d01f8-41a5-47f9-9168-e809edcae6cb"
    }
}
</code></pre>

},
