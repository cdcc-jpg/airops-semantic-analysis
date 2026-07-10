# AirOps Semantic Classification Output

This directory hosts the output of running the **Facettes** semantic classification pipeline on the **AirOps** raw datasets.

## Directory Contents

* **`classification_report.md`**: Detailed report on discovered mappings and scores.
* **`sbo_bridges.ttl`**: The compiled SBO bridge mapping rules.
* **`silo1_retail_classified.ttl`**: Classified retail catalog triples.
* **`silo2_chrono_classified.ttl`**: Classified chronolog validation triples.
* **`silo3_repairs_classified.ttl`**: Classified workshop repairs invoices.
* **`silo4_social_classified.ttl`**: Classified social feed mentions mapped to concepts.

## Interactive Visualization

An interactive, animated SVG dashboard has been built to visually demonstrate how these silos connect into a single unified player profile.

To view the visualizer:
1. Open the [index.html](index.html) file directly in your web browser, OR
2. Spin up a local server:
   ```bash
   python3 -m http.server 8000
   ```
   And visit: [http://localhost:8000](http://localhost:8000)

## How to Import

All `.ttl` files are standard RDF graphs and can be imported directly into RDF4J, Apache Jena, or GraphDB.
