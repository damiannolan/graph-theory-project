# The Prototype Database - CRUD

The following document contains information about how to interact with the prototype database included in this repository. Examples of CRUD Operations (Create, Read, Update, Delete) and screenshots of the graph are provided below. Cypher allows for relatively straight forward Creation, Retrieval, Updating and Deletion of data with its declaritive SQL inspired syntax.

## Create

Below is an exmample of creating a node for 3rd Year Group B Lab for Graph Theory on a Tuesday afternoon and creating the relationships associated with it.

Create a node with the label of Lab:

    $ create (l:Lab { lab: 'Graph Theory', group: 'B'}) return l;

Associate the Lab with it's respective Module, Room and Time on a particular Day using Relationships:

    $ match (m:Module {module: 'GRAPH THEORY'}), (l:Lab {lab: 'Graph Theory', group: 'B'}), 
      (r:Room {room:'379'}), (d:Day {day: 'Tuesday'})
      create (l)-[:TopicOf]->(m), (l)-[:Location]->(r), (l)-[:Time {time: '12:00-13:00'}]->(d);

![CreateLab](http://i.imgur.com/SK2rV5U.png)

## Read

Below is an example query of how to match all modules and their respective lecturers for Year 3 of Software Development

    $ match (y:Year)-[:Includes]->(m:Module)<-[:Teaches]-(l:Lecturer) where y.year = 'Year 3' return y, m, l;

![ReadModulesLecturers](http://i.imgur.com/vCwQc0d.png)

## Update

Update a Module node to set its name correctly:

    $ match (m:Module) where m.module = 'WRONG_NAME' set m.module = 'GRAPH THEORY' return m;

Update a Relationship property to set its time correctly:

    $ match (l:Lab)-[t:Time]->(d:Day) where l.lab = 'Graph Theory' and l.group = 'B' set t.time = '12:00-13:00'
      return l, d;

![UpdateExample](http://i.imgur.com/XfgxiGy.png)

## Delete

Delete a Module node

    $ match (m:Module) where m.module = 'WRONG_NAME' delete m;

Delete a relationship between a set of nodes

    $ match (l:Lecturer { lecturer: 'Martin Hynes'})-[t:Teaches]-(m:Module { module: 'DATABASE MANAGEMENT'})
      delete t;

## More Complex Queries

When taking advantage of the power of Cypher we can deduce easiliy what times a particular room is occupied and by what Module or Lecture.

    $ match (m:Module)<-[:TopicOf]-(x)-[:Location]->(r:Room)<-[]-()-[:Time]->(d:Day) 
      where r.room = '994' return m, r, x, d;

![TimesRooms](http://i.imgur.com/Y3cDEEB.png)

___

Return a graph of all Lectures/Labs and their locations that take place on a Friday

    $ match (m:Module)<-[:TopicOf]-(x)-[:Time]-(d:Day)-[]-()-[:Location]-(r:Room) where d.day = 'Friday' 
      return m, x, d, r;

![FridayClasses](http://i.imgur.com/OcG9GT7.png)

___

By querying the graph for all Years, Modules and their respective Lecturers we can get some interesting results that show us that 1st Year Student have an entirely different set of Lecturers to years 2, 3 and 4.

    $ match (y:Year)-[]->(m:Module)<-[:Teaches]-(l:Lecturer) return y, m, l;

![YearsModulesLecturers](http://i.imgur.com/kXbPrPu.png)

___