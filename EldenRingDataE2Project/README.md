# Elden Ring Data End-to-End Project (> **Status:** 🚧 Work in Progress)

![Elden Ring](https://jeuxpourtous.org/wp-content/uploads/2022/09/Le-jeu-de-societe-Elden-Ring-est-officiellement-annonce.jpg)

**Playing Elden Ring with Data - A Different Way to Experience the Lands Between**

An end-to-end data engineering project that processes, cleans, and analyzes Elden Ring game data through a multi-layered architecture (Bronze, Silver, Gold) using PySpark on Databricks Free Edition. This project answers complex questions about the game through data analysis, revealing patterns and insights that enhance your gaming experience.

## 📋 Project Overview

This project implements a comprehensive data pipeline for Elden Ring game data, covering 28 CSV files with information about weapons, armor, bosses, NPCs, locations, spells, items, and more. The pipeline follows the **medallion architecture** (Bronze-Silver-Gold layers) to transform raw data into analysis-ready datasets.

### 🎮 Mission

**Experience Elden Ring through data.** Instead of just playing the game, explore it analytically - discover optimal builds, uncover hidden patterns, compare equipment effectiveness, and answer complex questions that would take hundreds of hours of gameplay to solve manually.

### 🎯 Learning Objectives

This is a **practical data engineering project** demonstrating real-world skills:
- **Data Loading**: Initial batch loading and incremental loading strategies
- **Data Transformation**: Complex data cleaning and standardization
- **Data Modeling**: Dimensional modeling for analytics (Star Schema)
- **Data Quality**: Handling messy real-world data issues
- **Data Analysis**: SQL and PySpark analytics on large datasets
- **Data Visualization**: Dashboard creation for insights
- **ETL Orchestration**: End-to-end pipeline implementation on Databricks

### Key Features

- **Multi-layered Architecture**: Bronze (raw ingestion) → Silver (cleansed & conformed) → Gold (aggregated & analytics-ready)
- **Incremental Loading**: Support for both batch and incremental data loading patterns
- **Data Quality Management**: Handles complex data quality issues including dictionary strings, nested structures, and inconsistent null representations
- **Comprehensive Coverage**: 28 CSV files covering all major Elden Ring game entities
- **Databricks Implementation**: Built on Databricks Community Edition (Free Tier)
- **PySpark Processing**: Scalable data transformations using Apache Spark
- **Analytics & Dashboards**: Pre-built queries, dimensional models, and interactive visualizations

## 🗂️ Project Structure

```
EldenRingDataE2Project/
├── Data/                          # Raw CSV data files (28 files)
│   ├── armors.csv
│   ├── ashesOfWar.csv
│   ├── bosses.csv
│   ├── creatures.csv
│   ├── incantations.csv
│   ├── locations.csv
│   ├── npcs.csv
│   ├── shields.csv
│   ├── shields_upgrades.csv
│   ├── skills.csv
│   ├── sorceries.csv
│   ├── spiritAshes.csv
│   ├── talismans.csv
│   ├── weapons.csv
│   ├── weapons_upgrades.csv
│   └── items/                     # Item subcategory files
│       ├── ammos.csv
│       ├── bells.csv
│       ├── consumables.csv
│       ├── cookbooks.csv
│       ├── crystalTears.csv
│       ├── greatRunes.csv
│       ├── keyItems.csv
│       ├── materials.csv
│       ├── multi.csv
│       ├── remembrances.csv
│       ├── tools.csv
│       ├── upgradeMaterials.csv
│       └── whetblades.csv
├── Notebooks/                     # Jupyter notebooks for each layer
│   ├── BRONZE_LAYER.ipynb        # Raw data ingestion
│   ├── SILVER_LAYER.ipynb        # Data cleansing & transformation
│   ├── GOLD_LAYER.ipynb          # Dimensional modeling & aggregations
│   └── ANALYTICS QUERIES.ipynb   # Analysis and insights
└── docs/                          # Documentation
    ├── DATA SOURCES AND STRUCTURE.md
    └── DATA QUALITY ISSUES (INITIAL ANALYSIS USING EXCEL).md
```

## 📊 Data Sources

**Total: 28 CSV files** (15 main entities + 13 item categories)

### Current Data Source
- **Kaggle Dataset**: [Elden Ring Ultimate Dataset](https://www.kaggle.com/datasets/robikscube/elden-ring-ultimate-dataset)
- **Completeness**: Working with available data; completeness status being evaluated

### Future Enhancement Plans
- **Web Scraping**: Plan to scrape [Elden Ring Wiki (fextralife)](https://eldenring.wiki.fextralife.com/) to:
  - Validate and complete existing data
  - Add missing items and attributes
  - Update with latest game patches and DLC content
  - Cross-reference and improve data quality

### Main Entities (15 core files)
- **Weapons** 
- **Shields** 
- **Armors** 
- **Bosses** 
- **Creatures** 
- **Locations** 
- **NPCs** 
- **Sorceries** 
- **Incantations** 
- **Talismans** 
- **Skills** 
- **Spirit Ashes** 
- **Ashes of War** 

### Item Categories (13 files)
Ammos, Bells, Consumables, Cookbooks, Crystal Tears, Great Runes, Key Items, Materials, Multi-use Items, Remembrances, Tools, Upgrade Materials, Whetblades

## 🏗️ Architecture

### Bronze Layer (Raw Data Ingestion)
- **Purpose**: Load raw CSV files with minimal transformation
- **Processing**: Schema inference, basic type casting, metadata addition
- **Output**: Parquet files preserving source data structure

### Silver Layer (Cleansed & Conformed)
- **Purpose**: Clean and standardize data for consistency
- **Key Transformations**:
  - Parse dictionary strings (`{'Str': 15, 'Dex': 14}`)
  - Standardize null representations (`'-'`, `'N/A'`, `''` → `NULL`)
  - Parse list strings and nested structures
  - Clean number formatting (remove commas)
  - Extract complex multi-phase values (e.g., boss HP phases)
- **Output**: Cleaned, typed, and normalized Parquet files

### Gold Layer (Analytics & Dimensional Models)
- **Purpose**: Create business-ready dimensional models and aggregations
- **Key Outputs**:
  - Dimensional models (facts and dimensions)
  - Aggregated statistics
  - Relationship tables (weapon-skill, armor-location, etc.)
  - Pre-computed analytics tables
- **Output**: Optimized Parquet files for analysis

## 🔧 Technologies Used

- **Databricks Community Edition**: Cloud-based data engineering platform (Free Tier)
- **PySpark**: Distributed data processing framework
- **Python 3.x**: Primary programming language
- **Notebooks**: Interactive development and documentation
- **Apache Parquet**: Columnar storage format
- **Delta Lake**: Data lake storage (via Databricks)

## 🚀 Getting Started

### Prerequisites

- **Databricks Account**: Sign up for free at [Databricks Community Edition](https://community.cloud.databricks.com/)
- **Python 3.8+**: For local development (optional)

### Setup

1. **Create a Databricks workspace** (Community Edition)
2. **Upload the project files** to Databricks File System (DBFS)
3. **Import notebooks** to your Databricks workspace
4. **Create a cluster** (free tier allows up to 15GB memory)
5. **Run notebooks** in the following order:
   - BRONZE_LAYER.ipynb
   - SILVER_LAYER.ipynb
   - GOLD_LAYER.ipynb
   - ANALYTICS QUERIES.ipynb (IN PROGRESS)

### Running the Pipeline on Databricks

1. **BRONZE_LAYER.ipynb**: Ingest raw CSV data into Delta tables
2. **SILVER_LAYER.ipynb**: Clean and transform data with PySpark
3. **GOLD_LAYER.ipynb**: Create dimensional models and aggregations
4. **ANALYTICS QUERIES.ipynb**: Run analysis queries and prepare for dashboards

## 📝 Data Quality Issues & Solutions

| Issue | Description | Solution |
|-------|-------------|----------|
| **Dictionary Strings** | Dictionaries stored as strings | Parse using `ast.literal_eval()` |
| **Null Representations** | Multiple null formats (`'-'`, `'N/A'`, `''`) | Standardize to SQL `NULL` |
| **List Strings** | Lists stored as strings | Parse and explode into rows |
| **Number Formatting** | Numbers with commas (`'6,080'`) | Remove commas, cast to integer |
| **Nested Structures** | Lists of dictionaries | Multi-stage parsing |
| **Complex HP Values** | Multi-phase boss HP | Regex extraction by phase |

## 📈 Analytics Capabilities

### Complex Questions Answered Through Data

**Build Optimization:**
- What's the most efficient strength build path from level 1 to 150?
- Which weapon has the highest damage-to-weight ratio for dexterity builds?
- What's the optimal armor combination for maximum defense with medium roll?

**Boss Strategy:**
- Which bosses drop the most valuable items per difficulty level?
- What's the statistical correlation between boss HP and rune rewards?
- Which Spirit Ashes are most effective against specific boss types?

**Resource Efficiency:**
- What's the most efficient smithing stone path to +25 weapons?
- Which locations have the highest density of upgrade materials?
- What's the ROI of different remembrance exchange options?

**Game Progression:**
- What's the optimal location progression for item collection?
- Which incantations/sorceries provide the best FP-to-damage ratio?
- How do DLC items compare to base game items statistically?

### Dashboards (In Progress)
- Interactive visualizations for game statistics
- Equipment comparison and recommendation engine
- Location and boss analytics
- Character build optimization tools
- Resource efficiency calculators

## 🎯 Current Status

**Phase 1: Foundation (Completed)**
- ✅ Data sources documented (28 CSV files from Kaggle)
- ✅ Data quality issues identified and documented
- ✅ Bronze layer: Batch data loading to Delta tables
- ✅ Silver layer: Data cleaning & transformation logic
- ✅ Gold layer: Dimensional modeling (Star Schema)
- ✅ Databricks Community Edition setup and configuration
- ✅ Core analytics queries implementation

**Phase 2: In Progress**
- 🚧 Advanced analytics queries and complex aggregations
- 🚧 Interactive dashboards and visualizations
- 🚧 Performance optimization and query tuning
- 🚧 Comprehensive documentation completion

**Phase 3: Future Roadmap**
- 📋 Web scraping from Elden Ring Wiki (fextralife)
- 📋 Data validation and enrichment
- 📋 Real-time dashboard updates
- 📋 Machine learning models for build recommendations

## 📚 Documentation

Detailed documentation available in the `docs/` folder:
- [DATA SOURCES AND STRUCTURE.md](docs/DATA%20SOURCES%20AND%20STRUCTURE.md) - Complete data schema reference
- [DATA QUALITY ISSUES.md](docs/DATA%20QUALITY%20ISSUES%20(INITIAL%20ANALYSIS%20USING%20EXCEL).md) - Identified data quality challenges


## 🙏 Acknowledgments

- **Data Source**: [Elden Ring Ultimate Dataset](https://www.kaggle.com/datasets/robikscube/elden-ring-ultimate-dataset) by Robikscube on Kaggle
- **Future Data**: Planning to scrape and integrate data from [Elden Ring Wiki (fextralife)](https://eldenring.wiki.fextralife.com/)
- **Platform**: Built on Databricks Community Edition
- **Purpose**: Practical data engineering learning project


---

**Note**: This project is for educational and analytical purposes. All Elden Ring content is property of FromSoftware and Bandai Namco Entertainment.
