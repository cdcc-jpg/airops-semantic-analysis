# AirOps Semantic Classification & Mapping Report
*Created automatically using the Facettes 3-stage Neural Schema Matching pipeline.*

This report documents the semantic alignments discovered between raw physical data silos (Layer 2) and target AirOps OWL ontologies (Layer 1).

---

## 📁 Silo 1: Retail Inventory
* **Layer 2 Signature Hash**: `e95c1c149280b5cf6d8307871e5b125c6717b5282bd38475d88a05b1df5b433a`
* **L2 Data Triples**: `1260` triples
* **Classified L1 Triples**: `1750` triples
* **Exported File**: [silo1_retail_classified.ttl](silo1_retail_classified.ttl)

### Discovered Bridges & Mappings
| Source Element (L2) | Target Element (L1) | Re-ranked Confidence | Description / Nuance |
| :--- | :--- | :--- | :--- |
| `ItemRecord` | `AirsoftReplica` | `0.5331` | Domain-guided mapping: Retail Item Record → [RepairInvoice, AirsoftReplica] |

### Generated SPARQL CONSTRUCT Rules
```sparql
PREFIX h: <https://github.com/cdcc-jpg/ontologies#>
PREFIX src: <http://example.org/data-ontology/retail/>
CONSTRUCT {
    ?repairInvoice a h:RepairInvoice ;
            h:repairID ?item_sku ;
            h:repairedReplica ?airsoftReplica .
    ?airsoftReplica a h:AirsoftReplica ;
            h:hasModelName ?item_name ;
            h:hasBrand ?brand_name ;
            h:hasPowerSource ?power_source .
}
WHERE {
    ?source a src:ItemRecord ;
            src:brand_name ?brand_name ;
            src:item_name ?item_name ;
            src:item_sku ?item_sku ;
            src:power_source ?power_source .
    BIND(URI(CONCAT("http://example.org/inst/RepairInvoice_", MD5(STR(?source)))) AS ?repairInvoice)
    BIND(URI(CONCAT("http://example.org/inst/AirsoftReplica_", MD5(STR(?source)))) AS ?airsoftReplica)
}
```

---

## 📁 Silo 2: Chrono Field Logs
* **Layer 2 Signature Hash**: `4ae3767f32610f4e256e27550339e1fb614cf5afc21fa9dd4a9641154302a0f6`
* **L2 Data Triples**: `1512` triples
* **Classified L1 Triples**: `2500` triples
* **Exported File**: [silo2_chrono_classified.ttl](silo2_chrono_classified.ttl)

### Discovered Bridges & Mappings
| Source Element (L2) | Target Element (L1) | Re-ranked Confidence | Description / Nuance |
| :--- | :--- | :--- | :--- |
| `ChronoRecord` | `ChronoEvent` | `0.7908` | Domain-guided mapping: Chrono Record → [ChronoEvent, FieldZone, RepairInvoice, AirsoftReplica] |

### Generated SPARQL CONSTRUCT Rules
```sparql
PREFIX h: <https://github.com/cdcc-jpg/ontologies#>
PREFIX src: <http://example.org/data-ontology/field-logs/>
CONSTRUCT {
    ?chronoEvent a h:ChronoEvent ;
            h:hasChronoStatus ?test_status .
    ?fieldZone a h:FieldZone ;
            h:hasPlayerCapacity ?player_id ;
            h:hasMaxJouleLimit ?measured_muzzle_energy .
    ?repairInvoice a h:RepairInvoice ;
            h:platformModel ?replica_spotted ;
            h:repairedReplica ?airsoftReplica .
    ?airsoftReplica a h:AirsoftReplica ;
            h:hasFPS ?velocity_fps .
}
WHERE {
    ?source a src:ChronoRecord ;
            src:measured_muzzle_energy ?measured_muzzle_energy ;
            src:player_id ?player_id ;
            src:replica_spotted ?replica_spotted ;
            src:test_status ?test_status ;
            src:velocity_fps ?velocity_fps .
    BIND(URI(CONCAT("http://example.org/inst/ChronoEvent_", MD5(STR(?source)))) AS ?chronoEvent)
    BIND(URI(CONCAT("http://example.org/inst/FieldZone_", MD5(STR(?source)))) AS ?fieldZone)
    BIND(URI(CONCAT("http://example.org/inst/RepairInvoice_", MD5(STR(?source)))) AS ?repairInvoice)
    BIND(URI(CONCAT("http://example.org/inst/AirsoftReplica_", MD5(STR(?source)))) AS ?airsoftReplica)
}
```

---

## 📁 Silo 3: Tech Repairs
* **Layer 2 Signature Hash**: `8925ace72631241d1231d3c2477f973495bf9e1e700b24dd9a56fa74bb36aba5`
* **L2 Data Triples**: `2016` triples
* **Classified L1 Triples**: `2500` triples
* **Exported File**: [silo3_repairs_classified.ttl](silo3_repairs_classified.ttl)

### Discovered Bridges & Mappings
| Source Element (L2) | Target Element (L1) | Re-ranked Confidence | Description / Nuance |
| :--- | :--- | :--- | :--- |
| `RepairRecord` | `RepairInvoice` | `0.8428` | Domain-guided mapping: Tech Invoice Repair Record → [GameEvent, RepairInvoice, AirsoftReplica] |

### Generated SPARQL CONSTRUCT Rules
```sparql
PREFIX h: <https://github.com/cdcc-jpg/ontologies#>
PREFIX src: <http://example.org/data-ontology/repairs/>
CONSTRUCT {
    ?gameEvent a h:GameEvent ;
            h:hasTimestamp ?intake_date .
    ?repairInvoice a h:RepairInvoice ;
            h:repairID ?repair_id ;
            h:detectedFailure ?tech_diagnosis ;
            h:installedUpgrade ?upgrade_parts_installed ;
            h:repairID ?repair_status ;
            h:repairedReplica ?airsoftReplica .
    ?airsoftReplica a h:AirsoftReplica ;
            h:hasModelName ?platform_model .
}
WHERE {
    ?source a src:RepairRecord ;
            src:intake_date ?intake_date ;
            src:platform_model ?platform_model ;
            src:player_id ?player_id ;
            src:repair_id ?repair_id ;
            src:repair_status ?repair_status ;
            src:tech_diagnosis ?tech_diagnosis ;
            src:upgrade_parts_installed ?upgrade_parts_installed .
    BIND(URI(CONCAT("http://example.org/inst/GameEvent_", MD5(STR(?source)))) AS ?gameEvent)
    BIND(URI(CONCAT("http://example.org/inst/RepairInvoice_", MD5(STR(?source)))) AS ?repairInvoice)
    BIND(URI(CONCAT("http://example.org/inst/AirsoftReplica_", MD5(STR(?source)))) AS ?airsoftReplica)
}
```

---

## 📁 Silo 4: Social Scrape
* **Layer 2 Signature Hash**: `d6ec10038d676062df2ded03d5a905d0e563ca0a02197272b5d95fcba8578a9d`
* **L2 Data Triples**: `920` triples
* **Classified L1 Triples**: `648` triples
* **Exported File**: [silo4_social_classified.ttl](silo4_social_classified.ttl)

### Discovered Bridges & Mappings
| Source Element (L2) | Target Element (L1) | Re-ranked Confidence | Description / Nuance |
| :--- | :--- | :--- | :--- |
| `SocialRecord` | `SocialMention` | `0.7850` | Domain-guided mapping: Social Stream Mention Record → [SocialMention] |

### Generated SPARQL CONSTRUCT Rules
```sparql
PREFIX h: <https://github.com/cdcc-jpg/ontologies#>
PREFIX src: <http://example.org/data-ontology/social-mentions/>
CONSTRUCT {
    ?socialMention a h:SocialMention ;
            h:userCallsign ?user_callsign ;
            h:rawComment ?raw_comment ;
            h:detectedSlangTopic ?detected_slang_topic .
}
WHERE {
    ?source a src:SocialRecord ;
            src:detected_slang_topic ?detected_slang_topic ;
            src:raw_comment ?raw_comment ;
            src:user_callsign ?user_callsign .
    BIND(URI(CONCAT("http://example.org/inst/SocialMention_", MD5(STR(?source)))) AS ?socialMention)
}
```

---

