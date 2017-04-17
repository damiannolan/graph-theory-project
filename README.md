# Graph Theory

## Overview
This repository contains a collection of documentation regarding the implemenation and design model of a Graph Database for a third level institute timetabling system. For the purpose of this demonstration the existing GMIT (Galway-Mayo Institute of Technology) timetabling system shall be used as an example.

In this repository you will also find a zipped directory containing a prototype of the Graph Database under review.

## Introduction

The following documentation gives a brief insight into the world of Graph Databases and [Neo4j](https://neo4j.com/).
We will taking a look into the way in which information is stored and the impact that Graph Databases have on the way in which we model data and indeed think about and interpret it.

The purpose of this project is to learn about Neo4j and Graph Databases along with how to design and model a set of data in a robust and logical manner in which it can be queried using [CQL - Cypher Query Language](https://neo4j.com/developer/cypher-query-language/).

In light of this we take a look at how one might approach modeling a Third Level Institute timetabling system such as that of GMIT's. GMIT is home to a large number of programmes which fall under a wide variety of different departments. For this project, the BSc. in Software Development course will be showcased in the prototype database hosted in this repository.

- [What are Graph Databases and Neo4j?](about-graphdb-and-neo4j)
- [How is Data Stored?](how-data-is-stored)
- GMIT Timetable 
- General Thoughts and Conclusion

### Prerequisites 

Before moving any further it is advised you are setup and ready to use Neo4j with the prototype database provided. 

- Simply download and install [Neo4j](https://neo4j.com/download/)
- Clone this repository
- Unzip the file - gmit-software-timetable-graphdb.zip
- Launch Neo4j, select the database location and click start