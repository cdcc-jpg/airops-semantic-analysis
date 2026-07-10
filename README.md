# AirOps Semantic Classification Output

This directory hosts the output of running the **Facettes** semantic classification pipeline on the **AirOps** raw datasets.

## Directory Contents

* **`classification_report.md`**: Detailed report on discovered mappings and scores.
* **`sbo_bridges.ttl`**: The compiled SBO bridge mapping rules.
* **`silo1_retail_classified.ttl`**: Classified retail catalog triples.
* **`silo2_chrono_classified.ttl`**: Classified chronolog validation triples.
* **`silo3_repairs_classified.ttl`**: Classified workshop repairs invoices.
* **`silo4_social_classified.ttl`**: Classified social feed mentions mapped to concepts.

## How to Import

All `.ttl` files are standard RDF graphs and can be imported directly into RDF4J, Apache Jena, or GraphDB.
