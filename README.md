# Fall 2024 Principles of Databases — Assignment 4

* **Do not start this project until you’ve read and understood these instructions. If something is not clear, ask.**

---

## ❖ Introduction ❖

For this assignment, you will write responses to nine questions based on different topics from our textbook, *Database Systems — The Complete Book* and to one question based on your notes. Reply to each question in the provided region using Markdown syntax.

---

## ❖ Questions ❖

### 1. [2.4] What is the difference between a Cartesian Product, a Natural Join, and Theta-Joins?

#### Cartesian product
A cartesian product is a tuple set where every tuple from one set joins with every tuple from another set. If there are any attributes in both sets with the same name, thaen the reulting set will have one or both of them renamed to avoid ambiguity. If the set R has r number of tuples, and set S has s number of tuples, then the resulting set Q has a number of records q = r*s.
#### Natural Join
A Natural Join pairs two tuple sets on matching attributes. The resulting set will contain tuples from two tuple sets where a tuple from each set has identical values in all matching attributes of another set. Unlike Cartesian Product, common attributes will appear only once in the resulting set. The maximum number of tuples in the Natural Join between set R with r tuples, and set S with s tuples is q=r*s, just like in a Cartesian Product. However, the minimum number of tuples resulting from the Natural Join is zero, if there are no common values in matching attributes or no common attributes at all. The dangling tuple in a tuple set is considered a tuple that is not paired with another set. 
#### Theta Join
While Natural Join pairs tuples from relation sets based on common values in all common attributes, the join performed on other conditions are called Theta Joins. This condition can be any arbritrary condition set for a join. It does not require common attributes. The resulting set from a Theta Join will include attribues from both relations, some of which will need to be renamed to avoid ambiguity just like in a Cartesian Product. Just like in a Natural Join, the minimum number of tuples in the result set is zero. The join condition can be specified as any bollean condition, or any combination of boolean conditions possibly related to different attributes from each set. 

### 2. [2.5] What is a Referential Integrity Constraint?

A referential integrity constraint is where one tuple of a relation appears in another related tuple of a different relation.

###  3. [2.5] What is a Key Constraint?

A key constraint does not allow an attribute of two or more tuples to have the same value.

### 4. [4.1] What is an Entity/Relationship Model? What purpose does it serve in the process of creating/designing databases?

Replace this content with your answer

### 5. [4.4] What is a Weak Entity Set?

Replace this content with your answer

### 6. [5.2.7; 6.3.8] Explain the concepts of Outerjoin, Natural Right Outer Joins, Natural Left Outer Joins, and Full Outer Joins.

Replace this content with your answer

### 7. [6.6.3] What is the difference between the SQL command `TRANSACTION` and the execution of any statement in SQL?

Replace this content with your answer

### 8. [8] What is a Virtual View and what are its advantages?

Replace this content with your answer

### 9. [8.3] What is an *index* and what are its advantages?

Replace this content with your answer

### 10. Explain the concept of an MVC, or model, view, controller, framework for designing full stack applications

Replace this content with your answer

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
