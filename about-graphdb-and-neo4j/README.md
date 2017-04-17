# What are Graph Databases and Neo4j?

Graph databases are databases which use graph structures for storing and collating data to represent meaningful information for a given data set.

In Graph databases vertices are referred to as nodes and perhaps the most key concept for storing data is how edges between vertices or nodes are known as relationships. Relationships depicted via edges directly relate data items within the store and can be uses for traversal of a node tree within a database.

Other types of database such as SQL based databases compute relationships at a rather expensive query time whereas Graph databases store relationships as 'first-class citizens' to make 'join-like' queries of a database as in-expensive as possible.
Thus, Graph databases are considered to be NoSQL databases, however they offer much more complexity than that of a Document Store such as MongoDB or CouchDB.
To those who are experienced and comfortable with concepts such as entity relationship diagrams, the idea of storing data in a Graph-like manner should come quite naturally.

## Neo4j

Neo4j is an open-source NoSQL graph database implemented in Java and Scala. It has been under development since 2003 and available publicly since 2007. The entirity of Neo4j's source code is available on their [Github](https://github.com/neo4j/neo4j) where they have over 40,000 commits from over 140 different contributors. With Neo4j graphs are composed of two basic elements - Nodes and Relationships. Nodes and Relationships can be easily compared to vertices and edges of a traditional graph respectively. Nodes and Relationships allow for complex patterns throughout graph databases and can be much more expressive than static tables. Because it JVM based, Neo4j makes for a very useful database to be used cross platform and also offers Clustering and ACID Transactions like that of a SQL database.

## Cypher Query Language

CQL - Cypher Query Language or more commonly known as 'Cypher' is a declaritive query language created by Neo Technology for Neo4j but has since been made available and adopted by other graph databases such as SAP HANA and AgensGraph.
Much of Cypher's syntax is inspired from SQL so being familiar with a database such as MySQL will give users a decent base level of know how when adopting Cypher.
Being a declaritive language, Cypher allows users to state what they want to retrieve from a graph and not how to achieve doing it. Cypher allows for expressive and efficient querying and updating of data.
With Cypher Nodes are expressed using round brackets or parentheses: ( ), relationships as square brackets: [ ] and properties using curly braces: { }.
