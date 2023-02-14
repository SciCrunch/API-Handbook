---
description: How to access the SPARC Vocabularies via SciGraph
---

# Accessing SPARC Vocabularies via the SPARC Knowledge Graph

The best method for accessing the full SPARC Vocabularies that underlies the SPARC KG is via SciGraph.  The SPARC Vocabularies comprise the following components:

\--The NIFSTD Ontology:  a set of community ontologies with neuroscience specific extensions developed by the [Neuroscience Information Framework.](https://neuinfo.org)

\--Additional ontologies imported for the SPARC Project (e.g., FMA, EMAPA)

\--Additional vocabularies contributed by SPARC users for  annotating SPARC data and 3D scaffolds and to create the SPARC Connectivity Knowledge Base (SCKAN).



The easiest way to use the SPARC vocabularies is through our SciGraph [REST API](https://scicrunch.org/api/1/sckan-scigraph/docs/?url=https://scicrunch.org/api/1/sckan-scigraph/swagger.json).

You will need a SciCunch API key. You can get one by [registering for a SciCrunch account](https://scicrunch.org/register) and then [creating an api key](https://scicrunch.org/account/developer).

See the [API documentation](https://scicrunch.org/api/1/sckan-scigraph/docs/?url=https://scicrunch.org/api/1/sckan-scigraph/swagger.json) for more. If you get a 401 error you can open [https://scicrunch.org](https://scicrunch.org/) in another tab an refresh the page.

Examples of query results can be seen at [http://ontology.neuinfo.org/trees/examples](http://ontology.neuinfo.org/trees/examples).

The call to SciGraph that generated a given tree visualization of a result can be seen in the html header of the page under link rel `http://www.w3.org/ns/prov#wasGeneratedBy`

