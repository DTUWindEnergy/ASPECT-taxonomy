[![CI](https://github.com/DTUWindEnergy/ASPECT-taxonomy/workflows/Sheet2RDF/badge.svg)](https://github.com/DTUWindEnergy/ASPECT-taxonomy/actions?query=workflow%3ASheet2RDF)

# [ASPECT: wind energy v**A**riable**S** **P**aramet**E**rs and **C**ons**T**ants](http://data.windenergy.dtu.dk/controlled-terminology/aspect/)
This repository is meant for maintaining and updating the taxonomy (i.e. controlled vocabulary) of v**A**riable**S** **P**aramet**E**rs **C**ons**T**ants (ASPECT) used in wind energy community. In general, controlled vocabularies such this one allow an accurate and controlled approach in describing assets such datasets.

We use `sheet2rdf` and `OntoStack` to build and serve `ASPECT` taxonomy.
We use `purl.org` to provide persistant URLs for `ASPECT` terms and properties:
- [purl.org/apsect](purl.org/apsect), e.g. [purl.org/aspect/wind_speed](purl.org/aspect/wind_speed)

# sheet2rdf

This repository hosts automatic workflow, executed by means of Github actions, and underlying shell and python scripts which:

- [Fetches Google Sheet](https://docs.google.com/spreadsheets/d/1IzJ9cCVmoU2tcZ-P4xr405LE36aqhleiL6rvibAsCEo/edit#gid=1472229997) from Google Drive, which contains definitions of concepts (i.e., variables, parameters and constants), and converts it to `xlsx` and `csv` and stores these files to this repository
- Converts fetched sheet to machine-actionable and FAIR RDF vocabulary using [xls2rdf](https://github.com/sparna-git/xls2rdf)
- Tests the resulting RDF vocabulary using [qSKOS](https://github.com/cmader/qSKOS/)
- Commits conversion results and tests logs to this repository
- and deploy RDF vocabulary to OntoStack to be served to humans and machines

# OntoStack

OntoStack is a set of orchestrated micro-services configured and interfaced such that they can intake vocabularies and resolve their terms and RDF properties upon requests either by humans or machines.

Some of OntoStack micro-services are:

- [Jena Fuseki](https://jena.apache.org/documentation/fuseki2/) a graph database
- [SKOSMOS](http://www.skosmos.org/) a web-based SKOS browser acting as a front-end for the vocabularies persisted by the graph database
- [Træfik](https://doc.traefik.io/traefik/) an edge router responsible for proper serving of URL requests

**ASPECT** is served by DTU Wind Energy instance of `OntoStack`:
https://data.windenergy.dtu.dk/ontologies/view


# Taxonomy implementation
The taxonomy is implemented in following services:
- [NEWA Microscale Atlas data access point](https://wps.neweuropeanwindatlas.eu/api/microscale-atlas/v1/docs)
- [NEWA Mesoscale Atlas data access point](https://wps.neweuropeanwindatlas.eu/api/mesoscale-atlas/v1/docs)
- [CEDAR](http://cedar.metadatacenter.org/) through integration with [BioPortal](https://bioportal.bioontology.org/ontologies/WETAXTOPICS/)

*NEWA: [New European Wind Atlas](https://www.neweuropeanwindatlas.eu/)*
# Contribute

The taxonomy is intended to be used and further developed by the community. Therefore, we welcome collaborators willing to take part in the further development of the taxonomy. If you are one of them either request to become one of the taxonomy admins and/or post GitHub issues on what we can improve in the current taxonomy.
