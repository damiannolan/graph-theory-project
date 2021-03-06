# GMIT Timetable

The GMIT timetabling system stores vasts amount of data for a wide range of courses. For the purpose of this project I found it appropriate to use the Software Development course as an example.

## What Data is Needed?

To model an accurate representation of the GMIT timetable there is a certain amount of information needed that is crucial to it being possible. While the GMIT Timetable Site offers a huge amount of information I felt for this prototype demonstration that the most important data is: 

- Course Name
- Year
- Module Names
- Lecturer Names
- Time
- Location - i.e. Room Number

## Strategy

Designing and modeling a database schema that worked for this data was perhaps the most difficult task, while scraping the data is time consuming it was necessary to put the same amount of time into exploring different designs and models that could work for representing the timetable data in a graph store.

After much trial and wondering what was the best way to store these different pieces of data on the graph, I came up with what I feel like is a decent first draft model for the graph schema. I designed this model with the intension of being able to query certain fragments of the data quick and efficiently with Cypher queries that were not overly complex.
With this in mind, I chose that it was necessary to have a separate node for every lecture and lab that takes place throughout the week, otherwise it is easy to lose data integrity.

Using the schema below I feel it provides a useful structure of data that makes for simple querying and traversal of nodes using the relationships created between them.

## Schema
### Nodes

- Course
- Years (1-4)
- Modules
- Lecturer
- Room
- Lecture or Lab
- Day (Monday - Friday)

### Relationships

- Course *HAS* -> Years
- Year *INCLUDES* -> Module
- Lecturer *TEACHES* -> Module
- Lecture/Lab *TOPIC OF* -> Module
- Lecture/Lab *LOCATION* -> Room
- Lecture/Lab *TIME (with timeslot property)* -> Day

### Example

Below is an example of the way in which data is modeled in the graph. The query returns an example of how the entire schema looks and showcases the Graph Theory module's timetable for 3rd year Software Development students.
I feel its necessary to give a sample size of the graph to portray the schema as returning all nodes and relationships in the database isn't very aesthetically pleasing to the view.

    $ match (c:Course)-[]->(y:year)-[]->(m:Module)<-[]-(l)-[:Teaches|:Location|:Time]->(x)
      where m.module = 'GRAPH THEORY' return c, y, m, l, x;

![Schema](http://i.imgur.com/wijPegU.png)

## Obtaining the Data

All the data used in the prototype database has been obtained by myself personally from the [GMIT Timetable Site](http://timetable.gmit.ie). To do this I spent a lot of time scraping data by viewing the webpages source code in Chrome and filtering the data in Sublime Text via find and replace with some helpful use of basic regular expressions.
I then created a helper document which I used for setting up bulk commands for inserting data into the graph.
