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
![WhatsApp Image 2024-11-14 at 10 52 06 AM](https://github.com/user-attachments/assets/e0f7b1d2-aa68-4906-b72f-f7d8093cdea4)

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
![WhatsApp Image 2024-11-14 at 10 52 07 AM](https://github.com/user-attachments/assets/a5276368-3362-4cf1-a284-a32740629b91)

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

# Data Warehouse Table Types

## 1. Dimension Tables
- Contains descriptive attributes about business entities
- Characteristics:
  - Relatively static data over time
  - Smaller in size compared to fact tables
  - Contains primary key and descriptive attributes
  - Used for filtering and grouping data
  - Supports hierarchical relationships

### Dimension Table Components:
1. Primary Key
   - Generally numerical
   - Source system keys typically not used directly
2. Hierarchy Fields
   - Fields for each level of dimension hierarchy
3. Attribute Fields
   - Additional descriptive information
   - Related to hierarchy levels

### Handling Changes in Dimension Tables (SCD - Slowly Changing Dimensions):
1. Type 1: Overwrite
   - Original data replaced by new data
2. Type 2: Add New Record
   - Preserves history by adding new rows
3. Type 3: Add New Columns
   - Modify table structure to track changes

## 2. Fact Tables
- Contains transactional/measurement data
- Characteristics:
  - Changes frequently over time
  - Larger in size
  - Contains foreign keys to dimension tables
  - Contains numerical measures
  - Represents business events or transactions

### Fact Table Components:
1. Foreign Keys
   - References to dimension tables
2. Measures
   - Numerical values for analysis
3. Degenerate Dimensions
   - Transaction attributes that don't warrant a dimension

### Types of Measures:
1. Fully Additive
   - Can be aggregated across all dimensions
   - Example: Number of transactions, quantity sold
2. Semi-Additive
   - Can be aggregated across some dimensions
   - Example: Account balance, inventory levels
3. Non-Additive
   - Cannot be meaningfully aggregated
   - Example: Ratios, percentages

# Schema Types
1. Star Schema
   - Dimension tables directly connected to fact table
   - Simple and efficient
2. Snowflake Schema
   - Normalized dimension tables
   - More complex but saves storage

# OLAP (Online Analytical Processing)

## Overview
- Standard technique for analyzing large volumes of data
- Transforms raw data into meaningful business dimensions
- Facilitates reporting, aggregation, and trend analysis

## OLAP Cube
- Core building block for OLAP analysis
- Enables fast aggregation queries
- Multidimensional data representation

## OLAP Operations:
1. Slice and Dice
   - Filter and segment data
2. Roll-up and Drill-down
   - Navigate hierarchy levels
3. Drill-within and Drill-across
   - Analyze within/across dimensions
4. Pivot
   - Rotate view of data

## OLAP Server Types
1. ROLAP (Relational OLAP)
   - Uses relational databases
   - More scalable for large datasets
   - Slower query performance
2. MOLAP (Multidimensional OLAP)
   - Uses specialized storage structures
   - Faster query performance
   - Limited scalability

## Key Features of OLAP Tools
1. Summarization
   - Multiple aggregation levels
   - Flexible hierarchy navigation
2. Visualization
   - Interactive charts and graphs
   - Multidimensional views
3. Navigation
   - Intuitive dimensional exploration
   - Support for concurrent users
4. Dimensionality
   - Multiple dimension support
   - Quick data refresh
5. Query Processing
   - Efficient query engine
   - Fast response times
   - Advanced query capabilities

## Question and answers:
Q1: How do the four data warehouse characteristics provide better organization for decision support systems?

A1: The four key characteristics of data warehouses provide superior organization through:
1. Subject-oriented: Focuses on specific business subjects rather than operations, enabling better analysis
2. Integrated: Consolidates data from multiple sources into consistent formats
3. Time-variant: Maintains historical data for trend analysis
4. Non-volatile: Data remains stable once loaded, ensuring consistent analysis
These characteristics together support decision-making by providing clean, consistent, historical business data in an analysis-friendly format.

Q2: What is the architecture of a data warehouse and its components?

A2: A data warehouse architecture consists of these key components:
#### do previous

Q3: What are the steps and approaches for data cleansing?

A3: Data cleansing involves these steps:
1. Data Auditing
- Identify data quality issues
- Profile data patterns

2. Data Cleaning
- Remove duplicates
- Fix structural errors
- Handle missing values
- Standardize formats

3. Verification
- Validate cleaned data
- Cross-check with business rules

4. Reporting
- Document changes made
- Track cleaning metrics

Q4: Explain star schema and snowflake schema.

A4: 
Star Schema:
- Central fact table connected directly to dimension tables
- Denormalized dimension tables
- Simpler queries and better performance
- More storage space required

Snowflake Schema:
- Fact table connected to normalized dimension tables
- Dimension tables broken down into subdimensions
- Reduces data redundancy
- More complex queries but less storage space

Q5: What are different storage design structures of a cube and their differences?

A5: Three main cube storage structures:
1. MOLAP (Multidimensional OLAP)
- Stores data in multidimensional arrays
- Fastest query performance
- Requires more storage space

2. ROLAP (Relational OLAP)
- Stores data in relational tables
- More scalable for large datasets
- Slower query performance

3. HOLAP (Hybrid OLAP)
- Combines MOLAP and ROLAP
- Stores detailed data in relational format
- Aggregates in multidimensional format

Q6: What are various OLAP operations and how does cascading improve query performance?

A6: Key OLAP operations:
1. Roll-up (aggregation)
2. Drill-down (disaggregation)
3. Slice (single dimension)
4. Dice (multiple dimensions)
5. Pivot (rotation)

Cascading improves performance by:
- Executing operations in optimal order
- Reducing intermediate results
- Minimizing memory usage
- Leveraging pre-computed aggregates

Q7: What are the shortcomings of ER modeling for analytical applications and how does dimensional modeling enhance it?

A7: ER Modeling shortcomings:
1. Complex for analysis
2. Not optimized for queries
3. Difficult to understand
4. Poor performance for aggregations

Dimensional Modeling enhancements:
1. Simpler structure
2. Query-optimized design
3. Better performance
4. Easier to understand and use

Q8: What is the effective way of modeling metadata in a data warehouse?

A8: Effective metadata modeling includes:
1. Business Metadata
- Business terms
- Rules and policies
- Data ownership

2. Technical Metadata
- Source-to-target mappings
- Transformation rules
- Data lineage

3. Operational Metadata
- Load statistics
- Usage patterns
- Performance metrics

Q9: Why is a separate data warehouse needed in addition to OLTP systems?

A9: Separate data warehouses are necessary because:
1. Different purposes
- OLTP: Operational processing
- DW: Analysis and reporting

2. Performance optimization
- OLTP: Transaction-oriented
- DW: Query-oriented

3. Data structure
- OLTP: Normalized
- DW: Denormalized for analysis

4. Data retention
- OLTP: Current data
- DW: Historical data

Q10: How would you design an efficient algorithm to store a star schema with n dimensional tables and fact table?

A10: Efficient algorithm steps:
1. Indexing Strategy
- Create bitmap indexes for dimension keys
- Use composite indexes for fact table
- Implement partitioning

2. Storage Optimization
- Compress dimension tables
- Partition fact table by date
- Pre-aggregate common queries

3. Loading Process
- Parallel load for dimensions
- Bulk load fact table
- Update indexes efficiently

4. Query Optimization
- Materialized views for common joins
- Statistics maintenance
- Query rewrite capabilities
