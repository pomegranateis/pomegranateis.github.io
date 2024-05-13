---
Title: DBS101 Flipped Class 1
categories: [DBS101, Flipped_Class]
tags: [DBS101]
---

# Topic : Datebase Users and Database Administrators

---
## What I Did
For our first flipped class today, we were divided into groups for discussing about database users and administrators. More specifically, it was two groups discussing about different type of database users and the other two discussing about database administrator(DBA) which we find out later on that it is also basically a type of a database user.

Our group got assigned to research on DBA so we referred notes provided in vle side by side with the help of some of the search engines and the online textbook provided. After 20 minutes, as assigned by our tutor we went to our other group with new members to discuss what we learned from our previous group members. After sharing all our ideas, we took turns presenting our learnings and our doubts to the whole class.

These are what we found out, learned and discussed on DBA. They include an introduction to DBA, its life cycle, its roles and functions. We dug deeper and found out DBA had lots of different types as well.
## What I Learned
### Database Administrator
A Database Administrator is a professional responsible for the design, implementation, maintainance and management of an organisation's databases. Their role involves ensuring the security,integrity and performance of the databases while also optimising them for efficiency.

DBA ensures databases are safe and data is protected from unauthorized access. They create backup and recovery plans to prevent data loss in disasters or attacks. DBAs work with vendors to choose and install new database systems. Nowadays, the tasks
traditionally associated with DBA are performed by DevOps personnel.

#### Database Administrator Life Cycle
(referred from the notes provided on vle)
##### Planning
Planning is the first step. In this stage, we try to understand what the stakeholders require and how we can use the database to support business needs. The DBA collaborates with other stakeholders to find out what data is needed. Then they plan how to design and set up the system and set goals for the database.

##### Analysis
During the analysis stage, the focus is on the organization's data. The goal is to determine how to organize the data to meet the system's new requirements. This involves reviewing existing databases, data dictionaries, and models.

##### Design
The design stage creates a model for the organization's data needs. This includes defining the tables, fields, relationships, dictionaries and Data Flow Diagram.

##### Implementation
In the implementation stage, we put the database system into action based on the design plan from the planning stage. This means creating tables, importing data, and setting up user accounts. User accounts are set with various hierarchies and access permissions. 

##### Maintenance
The system needs maintenance to work well. This means checking and maintaining it to avoid problems. This includes performing regular backups and monitoring performance. Also, the DBA optimizes the queries to improve efficiency.

##### Update
Over time, the needs of the organization could change. So, accordingly DBA would need to make changes to the database system. This could involve making changes to the data model. For example, adding new fields or updating systems to support new business processes.

#### Roles and Responsibilities of DBA
There are various roles and responsibilities of a Database Administrator:

- Managing the relationship with the database vendors and service providers.
 
- Conducting regular audits of the database systems. It is done to ensure the proper functioning and security of the database.
 
- Providing technical support to the end-users and other IT staff regarding database issues.
 
- Developing and implementing policies and maintaining them. It is done to ensure that databases are managed effectively.
 
- Working with people who need data to create a database that fits their needs. Developing database solutions to meet the needs of the stakeholders.
 
- Identifying and troubleshooting database issues and resolving them in a timely manner.
 
- Creating and maintaining data dictionaries and data flow diagrams.
 
- Ensuring that databases are optimized for efficient data storage and retrieval.

#### Different Types of DBA 
- Application DBA 
- Backup and Recovery
- Data Architect DBA
- Development DBA
- Database Security
- High Availibility
- Performance Tuning
- Production DBA
- Reporting DBA
- Warehouse DBA

#### Functions of DBA
The main functions of DBA are:
###### Database design and implementation
This is one of the most important functions of DBA. DBAs understand the requirements of the organisation to determine the data needs to be stores, its structure, relationships and constraints. They try to create a high-level conceptual model of the database schema using ERDs. For easy implementation on DBMS, they translate the conceptual model into a logical schema. Side by side they add normalization techniques to ensure that the database schema is free from redundancy.They might also determine the physical storage structures and access methods to optimize database performance. This helps create a very close to ideal database schema in the chosen DBMS platform. Testing and optimizing the database schema to ensure that it meets the requirements and performs effiiciently. Documentation of the database design also falles under this function to serve as reference for stakeholders using/maintaining the database.
#####  Data Security
This function involves measures to protect the integrity and availibility of data stored in databases. DBAs are responsible for managing user access to databases by assigning appropriate permissions and privileges based on users' roles and responsibilities. They implement encryption techniques to protect sensitive data both at rest and in transit. DBAs may also employ techniques such as data masking and obfuscation to conceal sensitive information from unauthorized users or during non-production activities like testing and development. They set up auditing and logging mechanisms to track database activities and monitor for suspicious or unauthorized access attempts as well. They implement security best practices and configurations to harden the database server and minimize its attack surface. DBAs  then ensure that data backups are performed regularly and securely stored in offsite locations to prevent data loss due to disasters, hardware failures, or cyberattacks. They also develop and test disaster recovery plans to ensure the timely recovery of data in case of emergencies. With this they also mostly ensure that the database environment complies with relevant industry regulations and data protection laws such as GDPR, HIPAA, PCI DSS, etc.
### This is all about what we discussed thoroughly about DBA. After swapping groups, we got to learn about the other topic which is about different types of Database Users. What I learned from my friends were:

#### Database Users
Database users are individuals or entities who interact with a database system to retrieve, manipulate, or manage data stored within it.

These users can be broadly categorized into several roles based on their level of interaction and responsibilities within the database environment:


##### Database Administrator (DBA)
Although I shared alot about DBA previously, these are some thoughts which have been missed and pointed out by my friends. 

Database Administrator (DBA) is a person/team who defines the schema and also controls the 3 levels of database. The DBA will then create a new account id and password for the user if he/she need to access the database. DBA is also responsible for providing security to the database and he allows only the authorized users to access/modify the data base.

- DBA also monitors the recovery and backup and provide technical support.
- The DBA has a DBA account in the DBMS which called a system or superuser account.
- DBA repairs damage caused due to hardware and/or software failures.
- DBA is the one having privileges to perform DCL (Data Control Language) operations such as GRANT and REVOKE, to allow/restrict a particular user from accessing the database.

##### Naive / Parametric End Users 
Parametric End Users are the unsophisticated who don’t have any DBMS knowledge but they frequently use the database applications in their daily life to get the desired results. For examples, Clerks in any bank is a naive user because they don’t have any DBMS knowledge but they still use the database and perform their given task.
##### System Analyst
System Analyst is a user who analyzes the requirements of parametric end users. They check whether all the requirements of end users are satisfied.
##### Sophisticated Users
Sophisticated users can be engineers, scientists, business analyst, who are familiar with the database. They can develop their own database applications according to their requirement. They don’t write the program code but they interact the database by writing SQL queries directly through the query processor.
##### Database Designers
Database Designers are the users who design the structure of database which includes tables, indexes, views, triggers, stored procedures and constraints which are usually enforced before the database is created or populated with data. He/she controls what data must be stored and how the data items to be related. It is responsible for Database Designers to understand the requirements of different user groups and then create a design which satisfies the need of all the user groups.
##### Application Programmers
Application Programmers also referred as System Analysts or simply Software Engineers, are the back-end programmers who writes the code for the application programs. They are the computer professionals. These programs could be written in Programming languages such as Visual Basic, Developer, C, FORTRAN, COBOL etc. Application programmers design, debug, test, and maintain set of programs called “canned transactions” for the Naive (parametric) users in order to interact with database.
##### Casual Users / Temporary Users
Casual Users are the users who occasionally use/access the database but each time when they access the database they require the new information, for example, Middle or higher level manager.
##### Specialized users
Specialized users are sophisticated users who write 
specialized database application that does not fit into the traditional data-
processing framework. Among these applications are computer aided-design 
systems, knowledge-base and expert systems etc.

## How can the Flipped Class be Improved
I as a participant of this program would like to honestly state that for our first time doing this kind of class activity, it went quite well and was as useful as a class taken by a lecturer teaching the students. I feel like the students will get the hang of it steadily after three or four of these flipped classes.

So I would kindly like to mention that I actually have no improvements to be shared. x