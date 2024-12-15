# Fall 2024 Principles of Databases — Assignment 4

* **Do not start this project until you’ve read and understood these instructions. If something is not clear, ask.**

---

## ❖ Introduction ❖

For this assignment, you will write responses to nine questions based on different topics from our textbook, *Database Systems — The Complete Book* and to one question based on your notes. Reply to each question in the provided region using Markdown syntax.

---

## ❖ Questions ❖

### 1. [2.4] What is the difference between a Cartesian Product, a Natural Join, and Theta-Joins?

#### Cartesian product
A cartesian product is a tuple set where every tuple from one set joins with every tuple from another set. If there are any attributes in both sets with the same name, then the resulting set will have one or both of them renamed using dot notation (such as relation.attribute) to avoid ambiguity. If the set R has r number of tuples, and set S has s number of tuples, then the resulting set Q has a number of tuples q = r*s.
#### Natural Join
A Natural Join pairs two tuple sets on matching attributes. The resulting set will contain tuples from two tuple sets where a tuple from each set has identical values in all matching attributes of another set. Unlike Cartesian Product, common attributes will appear only once in the resulting set. The maximum number of tuples in the Natural Join between set R with r tuples, and set S with s tuples is q=r*s, just like in a Cartesian Product. However, the minimum number of tuples resulting from the Natural Join is zero, if there are no common values in matching attributes or no common attributes at all. The dangling tuple in a tuple set is considered a tuple that is not paired with another set and does not appear in the results of a Natural Join. 
#### Theta Join
While Natural Join pairs tuples from relation sets based on common values in all common attributes, the join performed on other conditions as well are called Theta Joins. This condition can be any arbritrary condition set for a join. It does not require common attributes. The resulting set from a Theta Join will include attribues from both relations, some of which will need to be renamed to avoid ambiguity just like in a Cartesian Product. Just like in a Natural Join, the minimum number of tuples in the result set is zero. The join condition can be specified as any boollean condition, or any combination of boolean conditions possibly related to different attributes from each set. In that sense, the Theta Join is similar to a Cartesian Product with an arbritrary condition eliminating some tuples, which means unlike Cartesian Product, the result of the Theta Join may have dangling tuples.

### 2. [2.5] What is a Referential Integrity Constraint?

A referential integrity constraint guarantees that a value appearing in a specific tuple in the attribute or attribute set also appears in the related context. This other context is usually represented by attributes in another relation. For instance, if we have two relations R with an attribute a and S with an attribute b, a referential integrity constraint can be set so for each tuple in R a value of attribute a appears in a tuple of relation S in attribute b. An example would be a student roster for a class where the value of an attribute StudentID for each tuple in a ClassRoster relation must exist as a value of studentID attribute in one of the tuples of the relation Students where the relation Students holds all students enrolled in the program. In relational algebra, it can be written as $\pi_{StudentID}(ClassRoster) \subseteq \pi_{StudentID}(Students)$. Such constraint also indicates that there may be some students that are not part of the class roster, though everyone in the class roster must be a student. The referential integrity constraint may also include multiple attributes. In practice, the attributes of S that are being pointed by the referential integrity constraint of R are usually primary keys of S.

###  3. [2.5] What is a Key Constraint?

A key constraint does not allow an attribute set of two or more tuples of the same relation to have the same value set. The key constraint can be expressed algebraically using SIGMA constraint notation. The other attributes that are not part of the key may have matching values in different tuples. For example, if we have a relation Students with an attribute StudentSSN (Social Security Number) that contains all students enrolled in the school and relation Professors with an attribute ProfessorSSN both being the keys in their respective relation, in algerbraic notation, that a student cannot be a professor can be written as $\sigma_{\text{Students.StudentSSN = Professors.ProfessorSSN}}(Students \times Professors) = \emptyset$. 

### 4. [4.1] What is an Entity/Relationship Model? What purpose does it serve in the process of creating/designing databases?

An entity/relationship model is a graphical representation of a data structure. It has entity sets, relationships, and attributes. An entity set represents a set of abstract objects. Each entity has associated attributes that represent properties of an entity. Relationships connect entity sets to each other. The entity/relationship model may be visually implemented as a diagram or graph called an 'Entiy-Relationship (ER) diagram'. Different types of entities and relationships will be represented by different symbols on the ER diagram. For example, entities are represented by rectangles, relationships by rhombuses, and attributes by ovals. The relationship keys are represented by attributes that are underlined. The purpose of the entity-relationship model is to present an abstract or high-level design when designing or creating a database rather than specifying elements directly implemented as part of the database schema. Some of the elements represented in the model may be converted into database schema elements in several different ways. Even so, the ER model shows a hierarchy of entity sets and relationships, for instance, specifying weak entities and relationships and showing relationship cardinality.

### 5. [4.4] What is a Weak Entity Set?

A weak entity set is an entity set whose key is composed of one or more attributes that belong to another entity set. A weak entity key does not have to contain attributes that belong to that weak entity. Uniqueness of tuples in a weak entity is enforced by attributes from another entity, possibly combined with attributes from the weak entity. In that sense, the weak entity is considered subordinate to another entity. A subordinate weak entity is connected to a parent entity by binary many-one relationships, which also needs to have referential integrity going from the weak entity to the parent entity. If a weak entity is connected to a supporting parent entity by multiple relationships, the key of the weak entity includes the combination of keys supporting each relationship. A tuple in the weak entity may not exist without acorresponding tuple in the parent entity. A weak entity is displayed on the ER diagram using a double border rectangle and weak relations are displayed by a double border rhombus.

### 6. [5.2.7; 6.3.8] Explain the concepts of Outerjoin, Natural Right Outer Joins, Natural Left Outer Joins, and Full Outer Joins.

#### Outerjoin

The Outerjoin is a way to represent dangling tuples (See answer to question 1) in the tuple set resulting from a join. Joins that are not Outerjoins do not include any values for dangling tuples in the resulting set, while Outerjoins include tuples that are made by combining/padding dangling tuples with NULL values in an attribute set from another entity in a join. Different types of Outerjoins indicate which entity set(s) will have dangling tuples represented in the result of the join.

#### Natural Right Outerjoin

The Natural Right Outerjoin includes the tuples from Natural Join as well as dangling tuples from the right side combined with NULLs for all attribute values representing the left side of the join. The result of the Natural Right Outerjoin does not include the nonmatching tuples from the left side.

#### Natural Left Outerjoin

The Natural Left Outerjoin includes the tuples from Natural Join as well as dangling tuples from the left side combined with NULLs for all attribute values representing the right side of the join. The result of the Natural Left Outerjoin does not include the nonmatching tuples from the right side.

#### Full Outerjoin

A Full Outerjoin includes the combination of related tuples as well as dangling tuples from each side combined with Null values for all attributes representing the other side of the join. In some way, it is a combination of the right and left Outerjoin.

### 7. [6.6.3] What is the difference between the SQL command `TRANSACTION` and the execution of any statement in SQL?

The concept of a transaction in SQL may ensure serialization (order of execution and prevention of dirty reads) and will ensure atomicity. In other words, when commands that change data run as part of the same transaction, the database ensures that either all changes done by all commands are propagated to data, or none of them do. The 'TRANSACTION' command in SQL indicates a start of a transaction. All subsequent commands are considered part of the transaction until one of two commands is issued. A COMMIT command indicates the end of the transaction and tells the database to save changes permanently to the database. A ROLLBACK command also indicates the end of a transaction, and indicates to the database to not save the changes done by commands as part of the transaction as if they never happened. A failure in execution of a statement that is part of a transaction may cause rollback of all statements that are part of the same transaction. A large number of in transaction changes may cause database resources to lock temporarily until the transaction is completed. If the start of a transaction is not explicitely defined, individual statement behavior will depend on specific database implementation. For example, in MySQL, the autocommit mode is enabled by default, which means that each individual statement will commit automatically upon completion, and will rollback automatically if it fails unless transaction is explicitely specified with a TRANSACTION command. Once transaction is commited, it cannot be simply rolled back, but rather needs to be reversed by an update if reversal is needed. In summary, if a transacton needs to include multiple statements that update data, an explicit command is needed to start a transaction and end a transaction. An individual command may be set to commit automatically without the need for an explicit start and end transaction commands.

### 8. [8] What is a Virtual View and what are its advantages?

A virtual view is a relation that does not physically exist in the database, but rather is the result of a query that behaves like a relation. Virtual views do not store data, but instead runs the query that is part of its definition everytime when its attributes need to be accessed. If the query in the virtual view definition is based on the actual relation, change of data in the underlying relation will automatically change results of the inquiries from the virtual view. While a virtual view can always be queried from, CRUD operations other than read can only be used if the virtual view complies with certain rules which depend on database implementation. For example, a view that is defined as a query from a single physical relation and contains all attributes that are part of the primary and foreign key as well as attributes that have other constraints usually may be updated or tuples can be deleted from it. Attributes of a view may directly correspond to the attributes of a relation used in the view query definition, but they do not have to do so. One advantage of the view is keeping code shorter and easier to understand if the view can be used instead of a subquery in other statements. A view also allows a developer to hide a physical database structure from a person using the view or hides specific tuples or attributes based on the conditions that are part of the view definition. A view may be constructed to prevent updates to tuples in the underlying relations for security reasons. Dropping the view does not change data in the relations used in the view definition query. Dropping the relations used in the view definition will invalidate the view, but will not necessarily drop it.

### 9. [8.3] What is an *index* and what are its advantages?

An index is a data structure related to a relation that makes searching of data in relations faster. A simple index on an attribute of a relation will contain sorted data from that attribute, where each data value also points to a specific tuple where that value is located. An index is always associated with a specific relation, and does not span multiple relations. The index may include multiple attributes from a relation. Some database implementations may automatically create indexes on attributes that are part of the primary key and foreign key constraints. Internally, indexes are usually stored in a binary tree structure, which have the same time complexity on searches as a regular sorted list, but is more efficient when data is added or deleted. Because indexes contain values from relation tuples, changes of the tuple values may require changes to the values stored inside index, which may also mean resorting the index values. That means some of the CRUD operations that perform changes may work slower if the index is present on a relation. However, the Read operation and search for values in a particular attribute will be much faster if that attribute is indexed. For mainstream business applications, where the most common operation is read or search, this may be very useful. The primary motivation for creating an index is to avoid reading every tuple from a relation when looking for a set of values. The indexes provide most benefit when created on attributes which are queried most often. Most database implementations will require dropping the index when the related table is dropped. However, dropping the index will not affect the values in the table.

### 10. Explain the concept of an MVC, or model, view, controller, framework for designing full stack applications

The MVC framework separates design process of full stack application into three different main components. These components are: model, controller, and view. The model includes the physical and logical representation of data, as well as the logic to access and manipulate the data. The end-users that interact with the application do not see the model. The model may contain high level design that includes relations, attributes, relationships, and other data components such as keys, constraints, and views. It can also include implementation-specific details, which will provide specifics for ACID and CRUD operations. In other words, the model usually represents the back - end of the application. The view includes anything related to user interaction and user interface. This includes visualizations, and pages where users can enter and see data on the screen. For example, it may include webpages in HTML, style sheets in CSS, javascript code that may do field validation. The view does not contain application logic, only the logic related to user interaction. It is used to separate user functions from the model, and the view does not interact with the model directly. The view is called the front - end of the application. The controller passes information between the model and the view, and sits between them as well. It also contains transformation logic that makes model data presentable to the user and handles view initiated events that require data retrieval or modification in the model. So while the user sees information in the view component, the user interaction are passed to the controller for further processing. While the data security resides with the model, the controller would facilitate data access based on user inputs. That allows the model to be independent from both the controller and the view. Some popular architectures such as LAMP, often implement MVC framework. The main advantage of a MVC is that it promotes reusability and modularity of the code. It also separates user interactions from application logic, which allows adding new features on the front or back end without affecting other parts of the application. It also makes the application easier to design and troubleshoot because a function would be isolated in only one component. The MVC approach improves team collaboration because different team members can work on different components in parallel without affecting each other. However, the MVC model may also increase application complexity due to the increased number of components and developers may need to take time to learn it if they have not used it before. It may also have potential performance issues due to the longer path between the user inputs and the data. Even so, the MVC architecture became very popular due to its advantages related to scalability and modularity.

---

## ❖ Due ❖

Sunday, 15 December 2024, at 10:00 AM.

---

## ❖ Grading ❖

| Item        | Points |
|-------------|:------:|
| Question 1  | `10`   |
| Question 2  | `10`   |
| Question 3  | `10`   |
| Question 4  | `10`   |
| Question 5  | `10`   |
| Question 6  | `10`   |
| Question 7  | `10`   |
| Question 8  | `10`   |
| Question 9  | `10`   |
| Question 10 | `10`   |

---

## ❖ Submission ❖

**NO late submissions will be accepted.**

You will need to issue a pull request back into the original repo, the one from which your fork was created for this project. See the **Issuing Pull Requests** section of [this site](http://code-warrior.github.io/tutorials/git/github/index.html) for help on how to submit your assignment.

**Note**: This assignment may **only** be submitted via GitHub. **No other form of submission will be accepted**.
