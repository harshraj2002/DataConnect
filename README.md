# "DataConnect"

A Neo4j Knowledge Graph Builder.

A comprehensive Python application that creates and manages a multi-dataset knowledge graph in Neo4j with integrated entity-relationship modeling.

## Overview

This application imports multiple CSV datasets into Neo4j and creates a rich knowledge graph with interconnected relationships. It combines raw data import with a structured entity-relationship model for comprehensive data analysis and visualization.

## Features

### Dataset Management
- **Multi-Dataset Import**: Handles 4 CSV datasets (Dataset1-4) with automatic encoding detection
- **Platform Integration**: Maps datasets to specific platforms (InsightUX, Exsight, Afkari, InnovateX)
- **Data Cleaning**: Automatically cleans column names and handles encoding issues
- **Cross-Dataset Relationships**: Creates meaningful connections between all datasets

### Entity-Relationship Model
- **Core Entities**: Users, Analysts, Contributors, Issues, Trends, Ideas, Domains, Regions, Platforms
- **Business Relationships**: Implements real-world business logic connections
- **Attachment System**: Handles various media types (documents, videos, audio)
- **Status Tracking**: Tracks entity statuses and impact areas

## Quick Start

### Prerequisites
```bash
pip install neo4j pandas
```

### Configuration
Update the file paths in the script:
```python
dataset_paths = {
    "Dataset1": r"path/to/Dataset1.csv",
    "Dataset2": r"path/to/Dataset2.csv", 
    "Dataset3": r"path/to/Dataset3.csv",
    "Dataset4": r"path/to/Dataset4.csv"
}
```

### Database Setup
- Neo4j instance running on `localhost:7687`
- Database name: `testdb`
- Default credentials: `neo4j/Harsh@123`

## Usage

Run the complete knowledge graph creation:
```bash
python main.py
```

The script will:
1. Import all CSV datasets as labeled nodes
2. Create inter-dataset relationships
3. Build the entity-relationship model
4. Establish dataset-platform connections
5. Verify the complete graph structure

## Knowledge Graph Structure

### Dataset Nodes
- **Dataset1**: Connected to InsightUX platform
- **Dataset2**: Connected to Exsight platform  
- **Dataset3**: Connected to Afkari platform
- **Dataset4**: Connected to InnovateX platform

### Entity Relationships
- Users raise Issues
- Analysts author Trends
- Contributors propose Ideas
- Ideas impact specific areas
- Entities have attachments and statuses
- Everything traces back to originating platforms

### Connection Types
- **CORRESPONDS_TO**: Same-row relationships across datasets
- **FLOWS_TO**: Sequential data flow patterns
- **SOURCED_FROM**: Dataset-to-platform connections
- **RAISED/AUTHORED/PROPOSED**: User action relationships
- **HAS_STATUS/BELONGS_TO**: Classification relationships

## Verification

The application provides comprehensive verification including:
- Node counts by type and dataset
- Relationship pattern verification
- Platform distribution analysis
- Sample relationship examples
- Neo4j Browser query suggestions

## Neo4j Browser Queries

View all platforms and connections:
```cypher
MATCH (p:Platform)<-[:SOURCED_FROM]-(d) RETURN p,d
```

View entity relationships:
```cypher
MATCH (n)-[r]->(m) WHERE NOT labels(n)[0] IN ['Dataset1','Dataset2','Dataset3','Dataset4'] RETURN n,r,m
```

View complete knowledge graph:
```cypher
MATCH (n)-[r]->(m) RETURN n,r,m LIMIT 100
```

## Output

The application creates a comprehensive knowledge graph containing:
- 40+ dataset nodes from CSV files
- 50+ entity model nodes
- 100+ interconnecting relationships
- Platform-dataset lineage tracking
- Business logic implementation
