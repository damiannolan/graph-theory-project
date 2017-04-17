# How is Data Stored? 

### A Deeper Look at Cypher and How Data is Stored

Neo4j employs the Property Graph Model to store and manage its data. The rules of the Property Graph Model are as follows: 

- Data is represented in **Nodes**, **Relationships** and **Properties**
- Both Nodes and Relationships can contain Properties
- Relationships connect nodes - they are essentially the edges of a graph
- Properties are key-value pairs
- Nodes are repsented by circles and Relationships by arrows
- Relationships have directions: either Unidirectional or Bidirectional

As we previously mentioned Nodes in Cypher are depicted using a form of ASCII-Art whereby they are shown as two round brackets (). Nodes in a graph store can be identified via Labels. Variable names much like aliases in SQL are placed before the colon.

The following node is given the label of User and a variable name of 'x'
- (x:User)

Likewise a relationship can be given a Relationship Type and also a variable name
- [x:FOLLOWS]

Properties are expressed within curly braces
- (:User { name: 'John Doe'})

Together we can build a simple enough Cypher Query

    $ match (x:User { name: 'John Doe'})-[:FOLLOWS]->(y:User { name: 'Jane Doe'}) return x, y;

The direction of the relationship above is that John follows Jane, it is not to be assumed that Jane follows John.