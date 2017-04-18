# The Prototype Database - CRUD

The following document contains information about how to interact with the prototype database included in this repository. Examples of CRUD Operations (Create, Read, Update, Delete) and screenshots of the graph are provided below. Cypher allows for relatively straight forward Creation, Retrieval, Updating and Deletion of data with its declaritive SQL inspired syntax.

## Create

Below is an exmample of creating a node for 3rd Year Group B Lab for Graph Theory on a Tuesday afternoon and creating the relationships associated with it.

Create a node with the label of Lab:

    $ create (l:Lab { lab: 'Graph Theory', group: 'B'}) return l;

Associate the Lab with it's respective Module, Room and Time on a particular Day using Relationships:

    $ match (m:Module {module: 'GRAPH THEORY'}), (l:Lab {lab: 'Graph Theory', group: 'B'}), (r:Room {room:'379'}), (d:Day {day: 'Tuesday'})
    create (l)-[:TopicOf]->(m), (l)-[:Location]->(r), (l)-[:Time {time: '12:00-13:00'}]->(d);

![CreateLab](http://i.imgur.com/5lgcZSg.png)

## Read

Below is an example query of how to match all modules and their respective lecturers for Year 3 of Software Development

    $ match (y:Year)-[:Includes]->(m:Module)<-[:Teaches]-(l:Lecturer) where y.year = 'Year 3' return y, m, l;

![ReadModulesLecturers](http://i.imgur.com/vCwQc0d.png)

