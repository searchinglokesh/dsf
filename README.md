# Data Warehousing

## Definition
- A technology that enables gathering, storing, and presenting data in a form suitable for human exploration
- Handles multiple data formats from different locations
- A subject-oriented, integrated, time-variant, and non-volatile collection of data supporting enterprise decision-making

## DBMS vs Data Warehouse Comparison

| Characteristic | DBMS | Data Warehouse |
|----------------|------|----------------|
| Purpose | Supports day-to-day operations | Supports information analysis |
| Updates | Transaction updates crucial | Mostly retrievals, fewer updates |
| Concurrency | Heavy | Light |
| Design | Normalized design essential | Normalized design appropriate |
| Data Access | Small amount per transaction | Large amounts for analysis |
| Time Focus | Present | Past, present, and future |
| Data Type | Atomic data | Aggregate data |
| Data State | Changing, incomplete data | Static, historical data |

## ROLAP vs MOLAP
- **ROLAP**: Enhanced to handle DBMS-like operations
- **MOLAP**: Uses specialized storage mechanisms optimized for data warehousing

## Architecture Components

### 1. Data Sources
- Repository integrating data from multiple sources
- Sources may be in different geographical locations

### 2. ETL (Extract Transform Load)
- Ensures periodic extraction of fresh data
- Includes data cleaning during extraction
- Transforms data to match warehouse schema
- Loads transformed data into warehouse

### 3. Metadata Repository
- Management tools for warehouse administrators
- Contains warehouse schema
- Includes administrative monitoring tools

### 4. Data Marts
- Subset of enterprise data warehouse
- Department-specific data
- Cost-effective implementation
- Useful for proof of concept

### 5. Physical Storage
- Distributed across multiple servers due to volume
- Metadata replicated on each server

### 6. OLAP Server
- Processes OLAP queries and data mining requests
- Accesses data from physical locations
- Number of processing units determined by architect

### 7. Front-End Tools
- Interface between analyst and warehouse
- Enables OLAP queries and data mining
- Provides visualization capabilities

## Data Characteristics

### 1. Subject-Oriented Data
- Organized by subject rather than application

### 2. Integrated Data
- Combines multiple heterogeneous sources
- Integration aspects:
  - Consistent naming conventions
  - Consistent measurement variables
  - Consistent encoding structures
  - Consistent physical attributes
- Integration occurs at data staging level

### 3. Time-Variant Data
- Provides historical perspective
- Contains time element in key structures
- Represents data flow through time
- Typically stores 5-10 years of data

### 4. Non-Volatile Data
- Data cannot be overwritten, only extended
- No updates or edits after entry
- Fresh loading and refreshing for queries

## Data Analysis Operations

### Drilling Down
- Allows analysts to view more detailed information
- Enables exploration of neighboring views
- Provides access to granular data levels

### Rolling Up
- Enables aggregation along dimensions
- Used for higher-level summaries
- Supports broader perspective analysis

## Core Data Characteristics

### 1. Subject-Oriented Data
- Organized by subject rather than application
- Focuses on business entities and metrics

### 2. Integrated Data
- Sources:
  - Relational databases
  - Flat files
  - OLTP files
- Integration features:
  - Consistent naming conventions
  - Standardized measurements
  - Uniform encoding structures
  - Consistent physical attributes
- Integration occurs at data staging level

### 3. Time-Variant Data
- Maintains historical perspective
- Time element in all key structures
- Tracks data flow through time
- Typical retention: 5-10 years

### 4. Non-Volatile Data
- Write-once, extend-only model
- No data updates or edits after entry
- Fresh loading and refreshing for queries

## Detailed Components

### 1. Data Sources
Four main categories:
1. Production Data
   - Primary operational data
2. Internal Data
   - Private spreadsheets
   - Internal documents
   - Customer profiles
   - Departmental databases
3. Archived Data
   - Historical operational data
   - Periodically stored records
4. External Data
   - Information from outside sources
   - Critical for executive decision-making

### 2. Physical Data Sources
- Infrastructure for data storage
- Hardware and storage systems

### 3. Front-End Tools
- User interface components
- Analysis and reporting tools

### 4. Metadata Repository and Administrative Tools
- System management tools
- Data dictionary
- Administrative controls

## Data Marts

### Definition
- Logical subset of data warehouse
- Focused information set
- Designed similarly to main warehouse
- Addresses specific user needs

### Types

#### 1. Subset Data Mart (Top-Down)
- Created from enterprise data warehouse
- Process:
  1. Build complete enterprise warehouse
  2. Extract relevant subsets
  3. Serve specific user groups
- Maintains consistency with main warehouse

#### 2. Incremental Data Mart (Bottom-Up)
- Building blocks approach
- Process:
  1. Create individual data marts
  2. Deploy incrementally
  3. Integrate into enterprise warehouse
4. More flexible implementation strategy

# Data Warehouse ETL Process

## Extraction Types

### 1. Full Extraction
- Extracts complete source data
- Used for initial loads
- More resource-intensive

### 2. Incremental Extraction
- Extracts only changed/new data
- More efficient for regular updates
- Requires change tracking mechanisms

## Data Transformation
- Validates data reliability
- Ensures data consistency
- Verifies data validity

## Loading Approaches

### 1. Initial Load
- First-time complete data load
- Establishes baseline data

### 2. Incremental Load
- Periodic loading of new data
- Updates since last load
- Maintains current data state

### 3. Full Refresh
- Complete deletion of existing data
- Fresh load of all data
- Reset of warehouse contents

# Logical Data Modeling

## Comparison: ER vs Dimensional Modeling

| Aspect | ER Modeling | Dimensional Modeling |
|--------|-------------|---------------------|
| Purpose | OLTP systems | OLAP systems |
| Focus | Operational database | Data warehouse |
| Optimization | Data insertion & updates | Complex queries & analysis |
| Structure | Normalized, complex | Denormalized, simpler |
| Schema | Many related tables | Star or snowflake schema |
| Components | Entities, attributes, relationships | Facts, dimensions, measures |

## Dimensional Model Components

### 1. Facts
- Central focus of analysis
- Business metrics/events
- Used for detailed analysis

### 2. Measures
- Continuous values (usually numeric)
- Different analytical perspectives
- Quantifiable metrics

### 3. Dimensions
- Contextual background
- Descriptive attributes
- Analysis categories

### 4. Granularity
Determined by:
- Included dimensions
- Hierarchy levels
- Lowest level of stored detail

### 5. Keys
#### Natural Keys
- Generated by source system
- Original identifiers

#### Surrogate Keys
- Generated by warehouse
- No inherent meaning
- Used for:
  - Production identification
  - Joining tables
  - Systematic generation during extraction

## Schema Tables

### 1. Dimension Tables
Characteristics:
- Contains dimension details
- Relatively static
- Smaller size
- Descriptive attributes

### 2. Fact Tables
Characteristics:
- Contains measures
- Frequently updated
- Larger size
- Numerical values

This structure enables efficient data warehousing and analysis while maintaining data integrity and accessibility.
