# Table of Contents
- [Database Model Selection](#database-model-selection)
  - [Relational Database Model](#relational-database-model)
  - [Non-Relational Database Model](#non-relational-database-model)
  - [Selected Model](#selected-model)
- [Database Update Frequency](#database-update-frequency)
- [Performance Considerations](#performance-considerations)
- [Database Management Systems](#database-management-systems)
  - [Selected DBMS](#selected-dbms)
- [Hardware Infrastructure](#hardware-infrastructure)
  - [Hardware Components](#hardware-components)
- [Data Loss Prevention Systems](#data-loss-prevention-systems)
- [Database Schema](#database-schema)
  - [Data Size](#data-size)
  - [Query Complexity](#query-complexity)
  - [Potential API Competitors](#potential-api-competitors)
    - [Edamam API](#edamam-api)
    - [Spoonacular API](#spoonacular-api)
    - [NutritionIX API](#nutritionix-api)
    - [USDA Food Data Central API](#usda-food-data-central-api)
- [Summary](#summary)
- [Database Schema Design](#database-schema-design)
  - [Overview](#overview)
  - [Entity-Relationship Diagram (ERD)](#entity-relationship-diagram-erd)
  - [Entities and Relationships](#entities-and-relationships)
    - [Food table](#food-table)
    - [Supplier table](#supplier-table)
    - [Classification table](#classification-table)
    - [Medical Table](#medical-table)
    - [Allergy table](#allergy-table)
    - [Recipe table](#recipe-table)
  - [Connecting tables and lists](#connecting-tables-and-lists)
  - [Datatypes](#datatypes)
  - [Constraints and Triggers](#constraints-and-triggers)
  - [Views](#views)

## Acronyms
- **SQL**: Structured Query Language
- **ACID**: Atomicity, Consistency, Isolation and Durability
- **API**: Application Programming Interface
- **CPU**: Central Processing Unit
- **RAM**: Random Access Memory
- **DBMS**: Database Management Systems
- **AMD**: Advanced Micro Devices
- **HDD**: Hard Disk Drive
- **SSD**: Solid-State Drive
- **URL**: Uniform Resource Locator
- **MVP**: Most Valued Player
- **AFCD**: Australian Food Composition Database
- **NAND**: Not-And

# Database Model Selection
When building a database from scratch, we must consider the type of model structure we are to use. There are many options we may choose, however for our scope, we will be best suited and look further into relational and non-relational models. Both of these options provide many benefits as well as possess some drawbacks, therefore, we must have a comprehensive understanding of the scope of our database before we can confidently select one.

## Relational Database Model
Based on the research conducted, taking a relational approach is best when the data is fixed and predictable in terms of its structure, size, and access frequency. The model’s data structure takes a tabular form, encompassing rows and columns, where the rows represent each instance of data, and every column refers to an attribute. Relationships can be established between instances of different tables with the use of primary and foreign keys, allowing for the data retrieval among associated tables. The tabular structure allows for SQL (Structured Query Language) to be used for querying, allowing information of instances to be retrieved, filtered, and sorted in the desired manner.

The data integrity of a relational model is well grounded, with full ACID (Atomicity, Consistency, Isolation and Durability) compliance. This allows for various elements that work in tandem to ensure all database transactions are processed reliably and minimize the impacts of unexpected events. Atomicity safeguards the transactions that occur throughout the database, acting as a singular entity, where if any part of the transaction fails, the entirety of it gets rolled back maintaining the integrity of all the related elements. Similarly, Consistency guarantees that for every transaction that occurs, the state of the database will remain valid before and after the given transaction. Isolation allows for multiple transactions to occur simultaneously throughout the database. This is possible as each of them occur in their own isolated states further maintaining the integrity of the transactions by reducing the potential of corruption. Finally, the Durability aspect ensures that all successful transactions are saved and will be resilient to many types of system failure, allowing for data to be easily recovered in the case of unexpected events.
Futureproofing the database is important in terms of scalability in the event that the workload increases, there’s increased user demand (a larger number of clients or API [Application Programming Interface] calls) or just general data growth. Common approaches for scaling up the relational database involve vertical (Scaling up) or horizontal scaling (Scaling out). Scaling vertically involves upgrading the hardware resources as this includes upgrading the CPU (Central Processing Unit), adding/upgrading more RAM (Random Access Memory) or adding/upgrading storage devices all of which are explained in more detail in the performance section. However, this can be difficult if there is a lack of physical space or constraints in the budget. Horizontally scaling better manages the workload by appropriately distributing it across multiple servers. This load balancing is achieved by applying techniques such as Database Sharding or Replication, that break the data into smaller partitions or create multiple copies respectively, before redistributing them across separate servers. In addition, cloud services exist where systems are readily available and tailored in advance to provide the necessary features to run and utilize databases. With cloud services, it is super easy to scale the available resources they provide at the expense of fees.

## Non-Relational Database Model
On the other hand, non-relational databases are more flexible, allowing for data to change shape or size and allows for a greater variety of data to be stored including; images, videos, and documents. There are many data models that a non-relational structure can utilize including; key-value, document, graph etc. The key-value model is simple and fast used for direct access using keys, where each data instance is stored as key-value pairs. This model is useful for caching, real-time applications as well as session management. A document model stores information in formats such as .json and .bson where each document can have varying fields or structures, hence being well suited for semi-structured or unstructured information. A graph model focuses more on the relationships between data instances and is represented as nodes, edges, and properties. Due to the structure of this model, it's more tailored towards social networks or recommendation engines.
Depending on the selected NoSQL database, ACID transactions may be supported, allowing for transactional guarantees in maintaining data integrity upon conducting complex operations. Eventual Consistency is a concept that is applied to this type of model that ensures that all data updates across a database will eventually arrive at a collective consistent state. The more flexible nature of non-relational databases allows for greater schema flexibility whilst maintaining data quality. NoSQL databases offer a great deal of logging and error handling features that can help in identifying and addressing issues as they occur in order to increase data integrity. Replication features exist in these databases that can help create some redundancy by constructing data copies on several nodes, allowing for data to be recovered if lost.
Scaling the system and improving performance for a non-relational database takes a similar approach to scaling a relational one, where either a vertical or horizontal scaling method can be taken. Horizontal scaling is done by distributing the data across multiple nodes (through Sharding/Partitioning) allowing for greater handling of larger datasets and general load by the server. Vertical scaling can also be done by providing more hardware resources to the server that includes CPUs, RAM, and Storage devices.

## Selected Model
The database team at Food Remedy API has concluded to go through with a Non-relational database model. We have selected this model due to the flexible nature of creating and modifying the database schema, image storage, serving real-time data to users, dealing with big data, performing analytics, and availability to error handling and logging capabilities.

# Database Update Frequency
Multiple approaches can be considered for updating the database. The first option involves implementing automatic update scripts which would occur at regular pre-defined intervals. This approach ensures that the database remains up to date without the need of manual intervention. This will not only be efficient but also be highly consistent with minimal risk of misinformation being retained in the database. If poorly implemented, it may introduce catastrophic failures in the database which would result in major downtimes, especially if no backups are conducted. Producing a working update procedure will require additional resource allocation and developmental time to get it perfected, which may result in a lack of immediate updates upon the deployment of the database. Changes in development team member composition may result in challenges for understanding and maintaining the update scripts in the future. This is a major consideration due to the project being conducted as a part of a unit, where all team members will change every 3-6 months.
An alternative approach is a manually updating of the database, which would be performed whenever it is deemed necessary by manually reviewing change logs provided by the external sources. While this approach offers control for when the updates occur, inconsistencies and delays may occur if not handled appropriately. This approach is more resource intensive requiring human intervention, can introduce inconsistencies in data entries, and is unsuitable for long-term preservation of the database.
The third option entails a more dynamic method which involves developing a system to check if external sources have been changed and update the database accordingly. This will only update when changes to the sources are detected, only executing the update on the particular segment of the database. Taking this approach is slightly more complex however is an extremely efficient mechanism that will reduce the workload of the system for performing updates as they are targeted.
Determining which updating process to utilize for the Food Remedy API Database is dependent on factors such as; resource availability, urgency for retaining up-to-date information, size of the database, longevity of the product, team composition etc, project scope etc. The urgency of maintaining up-to-date information, resource availability, and the desired level of automation. Each approach has its own benefits and considerations that should be evaluated based on the specific requirements of the database and the organization's needs.

# Performance Considerations
The performance of the database relies on a few factors including; the selected database management system, hardware infrastructure, database schema, data size, and query complexity.

## Database Management Systems
Database Management Systems, also known as DBMS, are software applications which provide tools to structure, store, manipulate, organize, and retrieve data from a source. This software acts as the middleman between various levels of a system such as data storage, users, applications, etc. There are many DBMS options to choose from, however will be dependent on the type of database model that is being pursued as they greatly differ in the way the data is stored, organized, and accessed.

### Relational DBMS
Some popular database management systems that can be used for relational databases can include; MySQL, Microsoft SQL Server, or PostgreSQL just to name a few.

#### MySQL
**Key Benefits**
- MySQL provides better security.
- The official website of MySQL offers a free download and use of MySQL.
- Widely compatible with most if not all operating systems.
- Based on client-server architecture, it can act as a connector, enabling connections between front-end and back-end architecture.
- A common DBMS platform where users most likely have some form of experience in.

**Key Limitations**
- Less scalable when compared to other DBMS platforms.
- Can sometimes have difficulty dealing with complex transactions (such as when nesting is present).
- Lacks some advanced features that other DBMS enterprise platforms may offer, specifically in the analytics department.
- Limited performance optimizations.

#### Microsoft SQL Server
**Key Benefits**
- Robust security features including; role-based access, encryption, authentication, etc.
- Easily scalable through both vertical and horizontal methods.
- Seamless integration with IDEs.
- Easy to learn and utilize through an intuitive graphical UI.
- Widespread availability of features allowing for complex and in-depth management.

**Key Limitations**
- Requires more resources to operate when compared to other DBMS platforms, which can lead to lesser than expected performance.
- Licensing costs.
- Some compatibility issues when it comes to window environments and cross-platforms.

#### PostgreSQL

**Key Benefits**
- Highly reliable and stable.
- Great for applications where data security and transactional guarantees are critical.
- Offers support for various SQL features like joins, partitions, and replication.
- Supported Languages: .Net, C, C++, Java, Perl, Python, TC.
- Query Language: SQL

**Key Limitations**
- Relies heavily on memory (RAM) to perform optimally.
- Sometimes have compatibility issues across different versions of the software (PostgreSQL).
- More complex queries may hinder the performance of the system.
- Setting up backups using replication can be difficult and more complex when compared to other DBMS platforms.

### Non-Relational DBMS
For non-relational databases, we have alternatives such as MongoDB, Cassandra, and Redis.

#### MongoDB
**Key Benefits**
- Great support for scalability and flexibility.
- Supports both semi-structured and unstructured data.
- Offers fast performance with low latency.
- Great for storing long-term data.

**Key Limitations**
- Relies on memory and hence the performance can be bottlenecked on the RAM hardware.
- Depending on the complexity of the schema, can sometimes prove difficult integrating it into the DBMS.
- Lacks in the support for joins and multi-document transactions.

#### Cassandra
**Key Benefits**
- Minimizes points of failure through distributing data amongst multiple nodes.
- Linear scalability through the addition of more nodes.
- Excels in performance gains through horizontal scaling.
- Able to handle large read/write throughput making it suitable for large databases.

**Key Limitations**
- Can sometimes struggle with complex queries and would then require denormalization to try and bump performance up.
- Admin work and setup can prove difficult due to the configuration requirements.
- There can be an impact on performance if secondary indexing is utilized.

#### Redis
**Key Benefits**
- Suitable for rapid read/write operations.
- Suitable for various data structures including; lists, hashes, sorted sets, strings, bitmaps, etc.
- Supports replication and redundancy through features such as Master-slave replication.
- Offers great scalability through horizontal scaling by sharding (partitioning) the data across multiple nodes.
- Great utilization of caching to improve application performance by reducing load on the central system.

**Key Limitations**
- Can sometimes struggle with complex queries when compared to other DBMS platforms.
- Requires more focus on managing memory to maintain performance.
- Primarily operating off memory can cause some damage to the database’s integrity if unexpected restarts or crashes occur.

## Selected DBMS
Taking into consideration the pros and cons of each DBMS along with having selected our database model, we have opted to go through with MySQL. MySQL offers greater accuracy to transactional results when compared to other DBMS options. MySQL is ACID compliant in nature, increasing the reliability of the database while remaining highly secure. In addition, a big portion of our justification in choosing MySQL is the hands-on experience that many in the Food Remedy API team already have with the DBMS. So, despite MySQL being designed and optimized for relational databases, it suits many of our needs and hence will be selected as the DBMS for the Food Remedy API database.

# Hardware Infrastructure

## Hardware Components
The available hardware to run the database server will definitely impact the overall performance when it comes to retrieving and processing queries. The most critical hardware components includes the CPU, RAM, and Storage Devices. 

The CPU is responsible for processing, where the performance is dependent on the available cores and the clock frequency of the processing chip. The greater the number of cores a CPU has, allows for more threads to be available to be used for parallel processing of queries. When selecting a CPU, we have to balance the clock speed as well as the available threads (the thread number is twice the core count) where the two main available brands are Intel and AMD (Advanced Micro Devices). AMD are more known for their workstation CPUs encompassing large number of threads allowing for computational heavy tasks to be conducted efficiently due to the multithreaded performance. They are also known to have a far greater price-performance ratio when compared to Intel CPUs. However, Intel have mostly remained on top when it comes to sheer CPU clock speeds and overall greater compatibility with other system hardware. Overall, both brands are highly reliable and will function exceptionally well granted the right model CPU is selected. 

The RAM is responsible for the handling of short-term memory caching data (such as indexes) that is frequently accessed. This overall improves query response times, reducing the need to continuously access the storage devices that are significantly slower relative to the RAM speeds. The RAM’s performance is dependent on the memory quantity of the stick as well as it’s speed, both of which impact the size of the datasets that can be accommodated as well as the processing time (data transfer) respectively. RAM also has latency that determines the access speed when responding to a request for the data. Lower latency timings improves the overall effectiveness of the RAM at a cost trade-off. RAM comes in various generations DDR3, DDR4 and now recently adopted by the consumer market, DDR5. These generations offer various improvements to performance and can only be installed on systems (motherboards) that can support the given generation. 

The selected Storage Devices also have a major impact in terms of the processing time of queries as well as the database’s potential volume. The key performance attributes of storage devices include the read/write speeds and well as the storage capacity. 

The faster these read/write speeds will allow for faster transfer rates as well as faster general I/O operations that occur when it comes to database transactions. For larger databases, the collective storage capacity can range anywhere from a couple hundred gigabytes to petabytes of storage in order to accommodate the large quantity of data. In most of not all cases, multiple storage devices will need to be linked in parallel to function as one large storage device. In addition, it’s also important to consider the reliability of certain brands of storage devices as well as the general physical durability. 

There are two different options for selecting a storage device type, including; Hard Disk Drive (HDD) and Solid-State Drive (SSD). HDDs are mechanical and often last around 3-5 years on average for general consumer-grade products. These drives are also extremely prone to failure if any marginal physical trauma is experienced such as dropping of the hard drive, power surges, constant vibrations, water damage, dust build-up etc. These drives can also have sudden unexpected failure resulting in most of not all data loss, meaning that it’s important to conduct regular backups or implement data loss prevention systems such as RAID (Redundant Array of Independent Disks). SSDs are flash memory chips that are used to store data without the need for any mechanical components. This allows for operations to be conducted significantly faster than regular hard disk drives and are far more reliable, however, are relatively more expensive to acquire when compared to HDDs for the same capacity. This difference in cost exponentially increases relative to HDDs as the capacity of the drives increases, mainly due to the manufacturing process of the NAND (Not-And) flash memory. 

## Data Loss Prevention Systems
There are many versions of RAID such as RAID 0, RAID 1, RAID 5 and more, that can be used as a data loss prevention system when to comes to storing data. Depending on the configuration, there are various advantages and tradeoffs that can be obtained, however the main purpose is to enhance data reliability and integrity of the stored data. 

- **RAID 0** (also known as stripping) splits the data across multiple drives rather than storing it all on one, resulting in faster read/write operations due to multiple drives working simultaneously. This however has no redundancy, meaning that if a hard drive were to fail, the particular data on that drive will be unfortunately lost however some of the data will be saved as it is stored on other drives. 

- **RAID 1** (also known as mirroring) creates some redundancy that is lacking in RAID 1 by creating mirror copies of the data on another drive. This creates a safeguard in case one of the drives fails and also can have some performance benefit as now two of the drives can be accessed simultaneously. 

- **RAID 5** utilizes stripping and parity bits to distribute and store data across multiple drives creating a solid foundation of redundancy however requires a minimum of three drives to be functional. This has some impact on performance however the main tradeoff is that if a drive were to fail, full recovery of the data can be made by using the other drives to reconstruct the data.

Granted we have the availability of hard drives both in terms of capacity and count, we should consider implementing a RAID setup for storing not only the database, but company documents and other crucial information. Selecting a RAID 5 configuration would be preferred due to the nature of the redundancy that would be created, allowing for full recovery of data if any one of the storage drives were to fail. 

## Database Schema
The organization for the data structure is performed in the database schema. The schema design determines the efficiency of the data storage through optimization of storage space, leading to increased speeds of data retrieval. The structure of the schema also impacts the potential of query complexity, where if designed effectively (such as appropriate indexing and applied normalization), query execution time would be minimized. Data integrity and scalability would be dependent on how the schema is structured, which may impact the system’s performance, impact the flexibility of the database and impact growth accommodation. 

## Data Size
The database size will impact various performance elements of the system. These would include; query speed, storage capacity, memory usage, backup storage, recovery methods etc. Large datasets will require transactional scans that occur to take longer, as the scans have to cover a larger surface area, hence leading to slower query executions. Big data will require greater hardware resource allocation to accommodate storage capacity (for live database storage and backups) and memory utilization. The size of the database will impact the types of available data loss prevention system that can be used (in terms of which are most efficient) as well as the types of recovery methods that can be applied in certain system failures. 

## Query Complexity
Queries can range in complexity depending on the type of data that is trying to be retrieved. It’s important to consider that the greater the complexity of the query, the poorer the system will perform in terms of execution time and resource consumption. Some complex queries may not fully utilize the pre-structured indexing of the database structure, reducing the performance of the execution time. Performing joins and aggregations will also hinder the performance of the system as additional scanning and matching needs to be done. Query complexity may also give rise to bottlenecks if hardware cannot match the necessary read/write speeds desired by the query when fetching data. 

# Potential API Competitors
It is critical for the success of Food Remedy’s API that we are aware of potential competitors in the food API market. By conducting this market analysis, it will provide us with insight into who else is targeting the same consumer base and the types of services they offer in the form of features and broadness of information. Food Remedy API will have to try and differentiate itself from the other competitors, where they will act as a baseline and can serve as benchmarks for performance. Being able to innovate, standout, and fill-in any market gap will greatly impact the success of the project in terms of customer attention and client quantity. Below are some of the highlighted competitors that will be offering similar API services and the extent to which they provide additional features. 

## Edamam API
- Provides access to a large database of recipes, nutrition data, and food-related information.
- Origin: United States
- URL: [Edamam](https://www.edamam.com/)
- Primary Functionality:
  - Consumer-oriented and large-scale applications
  - Nutrition Analysis (150+ Nutrient fields)
  - Food Database Lookup (900k food items)
  - Food Entity Extraction
  - Recipe Selection (2.3 Million recipes)
  - Meal Recommendation (Personalized with nutrient and dietary considerations)

## Spoonacular API
- Provides recipe information, meal planning, and nutrition analysis.
- Origin: United States
- URL: [Spoonacular](https://spoonacular.com/food-api)
- Primary Functionality:
  - Consumer-oriented
  - Recipe Analysis (Diets, Intolerances, Nutritional Information)
  - Meal Planning (115k Menu Items)
  - Shopping list integration for meals
  - 2600+ Ingredient items
  - Recipe selection (5000+ recipes)
  - Food Database lookup (600k+ products)

## NutritionIX API
- Offers access to nutrition information for foods and ingredients.
- Origin: United States
- URL: [NutritionIX](https://www.nutritionix.com/)
- Primary Functionality:
  - Consumer tools + Large-scale operations
  - Nutritional information
  - 880k+ food items
  - 190k+ menu items from Restaurants

## USDA Food Data Central API
- Provides authoritative nutritional data on a wide range of foods.
- Origin: United States
- URL: [USDA Food Data Central](https://fdc.nal.usda.gov/)
- Primary Functionality:
  - Large-scale operations
  - Food research, nutritional analysis
  - 440k branded foods
  - ~50-100+ nutrients/components

## Summary
In addition to gathering core information highlighted above, screenshots of UI designs, features, information presentation, field breakdowns and many other design aspects were taken in order to provide some inspiration on the UI design for Food Remedy API as well as how to structure and present our information. 

In summary, from all of the identified and selected core food API competitors, a majority of them are USA based where their databases range between 500k – 1M products. Most if not all of these companies support various levels of nutrient information that is displayed to the user depending on whether their API service is consumer or industrial based. For example, consumer-based platforms provided 10-20 unique nutrient fields that are displayed to the user, whilst for large scale APIs, there are cases where there are over 100 nutrient fields that are presented. From the 4 competitors that were researched into more detail, all of them offer suites of tools that range from meal recommendations, nutritional analysis, food database lookup, meal analysis (restaurant items included), food lists, calorie tracker etc. Overall, we need to take into consideration the scale of the data, feature sets and detail of information with regards to each competitor on the market in order to effectively compete. 

# Database Schema Design
## Overview
A comprehensive schema was developed for the initial MVP elements using various sources from Australian Food Composition Database (AFCD) and Food Remedy Airtable. The schema encompasses various interconnected tables that capture a variety of information including; food, suppliers, classifications, medical benefits, allergies, recipes, and their respective relationships.

## Entity-Relationship Diagram (ERD)
![Relational Database Schema Design](Company-Docs\Food Remedy API\Database Schema.PNG)
Figure 1 Relational Database Schema design
The visual representation of the database structure and organization can be seen in Figure 1. This will be used as a blueprint to develop a comprehensive understanding of the various relationships between data entities and attributes. The architecture displays the flow of information and data hierarchy, aiding in understanding the complete structure of the database.

## Entities and Relationships
The Australian Food Composition Database (AFCD) and Food Remedy Airtable were referred to in the creation of this schema. Specific reference files used:
- Food Remedy Airtable
- AFCD Food Details
- AFCD Nutrient
- AFCD Measure
- AFCD Recipe
- Food Standard Australia New Zealand website and Food Standard Code (https://www.foodstandards.gov.au/Pages/default.aspx)

### Food table
The primary table that was derived was the ‘Food Table’ which included referenced to both the AFCD food details and nutrients, along with all the fields present in the Airtable. Nutrients that were not integrated into the table did not adhere to the AFCD food labelling guidelines (1.28) and schedule (12). However, there are some nutrients that were deliberately included that were not covered by these guidelines specifically for medical purposes (for example - iodine for thyroid diseases). The core information captured in the table include; the food_id [PK] (type: int), food_name (type: char), food_image (URL) (type: varchar), food_details (type: varchar) and 65 nutrient attributes (type: int/numeric/decimal). 

There is a ‘one-to-many’ relationship structure established connecting the ‘Food Table’ to many of the linking tables (lists), which include; supplier list, class list, medical list, allergy list and ingredient list. The linkage is achieved by taking the primary key in the ‘Food Table’ denoted as food_id which is then correlated with all of the foreign keys in the corresponding tables. 

### Supplier table
The ‘Supplier Table’ contains various data revolving around basic supplier information. The derived fields are the minimum amounts of information needed to appropriately identify and track suppliers. The selected attributes include; supplier_id [PK] (type: int), supplier_name (type: char), supplier_address (type: varchar), supplier_suburb (type: char), supplier_postcode (type: int), supplier_state (type: char), supplier_phone_number (type: varchar) and supplier_email (type: varchar).

The ‘Supplier Table’ has a ‘one-to-many’ relationship with the ‘Supplier List’, where the ‘Supplier List’ has a relationships with the ‘Food Table’ in a ‘many-to-one’ relationship, overall resulting in many suppliers being able to reference many food items. This is conducted by referencing the supplier_id [PK] from the ‘Supplier Table’ to the supplier_id [FK] of the ‘Supplier List’. 

### Classification table
The ‘Classification Table’ is derived from AFCD food details: The food name is broken down to Raw, Process, Wild, etc. *List to expand during data cleaning. The initial core attributes include class_id [PK] (type: int), class_name (type: char), and class_desp (type: varchar). 

The ‘Classification Table’ has a ‘one-to-many’ relationship with the ‘Class List’ allowing for many classifications to exist for many different food items due to the intermediary class list. This is conducted by referencing the class_id [PK] from the ‘Class Table’ to the class_id [FK] of the ‘Class List’.

### Medical Table
The medical benefit stores are based on common food avoidance for special diseases or drugs interactions. Likewise to the ‘Classification Table’, the ‘Medical Table’ has a mbenefits_id [PK] (type: int), mbenefits_name (type: char) and mbenefits_desp (type: varchar) attributes. These are the only fields necessary for storing and referencing medical benefits. 

The ‘Medical Table’ has a ‘one-to-many’ relationship with the ‘Medical List’ allowing for many medical benefits to exist for many different food items due to the intermediary medical list. This is conducted by referencing the mbenefits_id [PK] from the ‘Medical Table’ to the mbenefits_id [FK] of the ‘Medical List’.

### Allergy table
Based on FSAZN Allergen labelling, the ‘Allergy Table’ contains the allergy_id [PK] (type: int), allergy_name (type: char) and allergy_desp (type: varchar) as the core attributes. 

There is a ‘one-to-many’ relationship between the ‘Allergy Table’ and ‘Allergy List’ allowing for many allergies to exist for many different food items due to the intermediary allergy list. This is conducted by referencing the allergy_id [PK] from the ‘Allergy Table’ to the allergy_id [FK] of the ‘Allergy List’.

### Recipe table
The derivation of the attributes in the recipe table were based on the AFCD Recipe database. The core attribute fields that were extracted include; recipe_name (type: varchar), recipe_details (type: varchar), recipe_calories (type: numeric), recipe_fat (type: numeric), recipe_protein (type: numeric), recipe_carbo (type: numeric) and recipe_reference (type: varchar). The table has a primary key denoted as recipe_id [PK] (type: int).

The ‘Recipe Table’ has a ‘one-to-many’ relationship with the ingredients linked using the recipe_id primary and foreign keys. 

### Connecting tables and lists
The remaining tables (Lists) are set in place to act is interconnects to the core and central tables. This collection of lists include; ingredient, supplier, medical, allergy and class lists. 
The ‘Supplier List’ stores relevant supplier-food information, allowing for multiple suppliers to be linked to multiple food items. This includes the food_id [FK] (type: int), supplier_id [FK] (type: int), date_update(d) (type: date), price (type: numeric) and availability (type: Boolean) fields. The ‘Supplier List’ is linked in a ‘many-to-one’ relationship establishing and a connection to the ‘Supplier Table’ through the supplier_id [FK] as connection to the ‘Food Table’ using the food_id [FK].  

The ‘Class List’ just stores foreign keys that allow to be linked to the appropriate tables, allowing for multiple food items to possess multiple classifications. The stored information includes the food_id[FK] (type: int) and class_id [FK] (type: int). The ‘Class List’ is linked in a ‘many-to-one’ relationship establishing a connection to the ‘Classification Table’ through the class_id [FK] and a connection to the ‘Food Table’ using the food_id [FK].  

The ‘Medical List’ just stores foreign keys that allow to be linked to the appropriate tables, allowing for multiple food items to possess multiple classifications. The stored information includes the food_id[FK] (type: int) and mbenefit_id [FK] (type: int). The ‘Medical List’ is linked in a ‘many-to-one’ relationship establishing a connection to the ‘Medical Table’ through the mbenefit_id [FK] and a connection to the ‘Food Table’ using the food_id [FK].  

The ‘Allergy List’ just stores foreign keys that allow to be linked to the appropriate tables, allowing for multiple allergies to be connected to multiple food items. The stored information includes the food_id[FK] (type: int) and allergy_id [FK] (type: int). The ‘Allergy List’ is linked in a ‘many-to-one’ relationship establishing a connection to the ‘Allergy Table’ through the allergy_id [FK] and a connection to the ‘Food Table’ using the food_id [FK]. 

The ‘Ingredient Table’ stores information to describe the portions of food as well as the foreign keys that links the respective tables, allowing for multiple food ingredients to be linked to multiple recipes. The stored information includes the food_id[FK] (type: int) and recipe_id [FK] (type: int), quantity (type: numeric) and measurement (type: char). The ‘Ingredient List’ is linked in a ‘many-to-one’ relationship establishing a connection to the ‘Recipe Table’ through the recipe_id [FK] and a connection to the ‘Food Table’ using the food_id [FK].  

## Datatypes
When creating a database, each field/attribute should have a datatype that is specified for several reasons. These reasons include; Memory efficiency, data integrity, security, query optimization, performance etc… Various datatypes that could be of use will be listed below:

**Integer Data Types:**
- `int` (integers): 4 bytes – 32 bits (in a 32-bit system) | 4 or 8 bytes – 32/64 bits (in a 64-bit system).
- `short` (short integers): 2 bytes – 16 bits.
- `long` (long integers): 8 bytes – 64 bits.

**Floating-Point Data Types:**
- `float` (single-precision floating-point): 4 bytes – 32 bits.
- `double` (double-precision floating-point): 8 bytes – 64 bits.

**Character Data Types:**
- `char` (characters): Singular byte – 8 bits (singular character).
- `string` (text): Vary in size based on length.

**Boolean Data Type:**
- `bool` (Boolean): Singular byte (typically).

**Date and Time Data Types:**
- `date` (date): 3-4 bytes.
- `time` (time): 3-4 bytes.
- `datetime` (date and time): Size varies depending on specific information captured.

**Binary Data Types:**
- `binary` (binary data): Size varies based on length.
- `blob` (binary large object): Size varies depending on the type of data stored (for example, images).

The datatypes in our database schema can be summarized for fields that require text or numerical data inputs. 'Int', 'decimal', and 'numeric' datatypes are used for attributes such as quantity, IDs, nutrient values, prices, and postcodes. While 'char' and 'varchar' hold a specified number of characters to deal with attributes such as names, descriptions, emails, measurements, etc. Additionally, 'date' and 'bool' datatypes are used to address fields such as availability and dates.

The datatypes for all the table fields have been meticulously chosen to minimize the storage space that the database will take up. Some datatypes, such as char and varchar, can have specified lengths that would be reserved where the values chosen were dependent on the field. For example, the supplier_state’s datatype was set to char(20), limiting the string length to 20 characters. Most, if not all, states would be less than 20 characters and hence it is unnecessary to allocate a larger number than 20. This same process is applied to all other attributes that may take a specified string length, where further tailoring can be done to better optimize the databases.

## Constraints and Triggers
A database’s integrity is maintained by applying constraints and triggers. Constraints are typically in the form of rules that are applied to data in the database that define limitations/requirements that need to be met when new data is being entered into the database. Triggers are events that are pre-defined in scripts or procedures that will respond to certain events that may occur in a database. Adhering to the defined constraints and developing triggers will help overall increase the reliability and integrity of the database.

Below are the constraints imposed onto the database:

- **Primary Keys:** Applies a unique identifier to an entry for a given table. Useful for efficient data retrieval.
- **Foreign Keys:** Acts as a referential that corresponds to values that are connected to a primary key in a different table.
- **Unique:** When applied, will prevent duplicate values in specific columns from being created.
- **Not Null:** When applied, will prevent certain entry values from being left empty.
- **Default:** When applied, will set a default value to a column’s entry if no other value is specified.

As of this current stage, triggers have yet to be developed, however, we potential triggers that could be useful for maintaining the database. Such triggers could include:

- **Validation:** Events that occur when a new entry is to be inserted in order to check if the data meets all of the constraints and requirements.
- **Updating:** Events that occur when a new entry is inserted into the database to update other records or tables.
- **Logging:** Events that occur which will log changes to the database, important for debugging, troubleshooting, monitoring, auditing, change management, etc.
- **Confirmation:** Events that occur before an action is processed, such as deleting data. This will help in preventing accidental removal of vital data.
- **Cleaning:** Events that occur when some data is deleted, to ensure consistency throughout the database is maintained, cleaning up unnecessary data that is related to the deleted data.

## Views
Developing a multitude of database schema views will offer different perspectives on the data that is stored in the core tables. Each view will serve as a specific purpose for enhancing data access, management, and analysis. Below are some important views that should be considered.

### User-Focused:
- **Standard:** Regular presentation of data in one or more tables.
- **Filtered:** Display subsections of data based on particular criteria.
- **Aggregate:** Compute and display results.

### Performance & Optimization:
- **Indexed:** Utilization of precomputed results.
- **Materialized:** Complex query result repurposing.
- **Partitioned:** Partition wide data access.

### Security & Access Control:
- **Security:** Limited data visibility dependent on user access roles.
- **Masked:** Mask sensitive data.

### Reporting & Analysis:
- **Denormalized:** Combining data from various table sources.
- **Historical:** Displaying the original data format.

### Schema & Metadata:
- **Schema:** Database structure information.
- **Data Dictionary:** Metadata information.

### Auditing & Logging:
- **Audit Trail:** Displaying actions that have been logged.
- **Logging:** Displayed modifications to data that have been logged.

### External Data Source:
- **External Table:** Viewing external sources in a unified location.

### Self-Service:
- **Self-Service Views:** Custom view creation.
