# Laboratorio di Basi di Dati Course<br/>*Final Projects A.Y. 2024/2025* - Specification #1

<section class="specifica">

## Project "Soccorso"
> Version 1.0

### Preamble

The course projects are inspired by real-world needs. The informal specification of the problem given in the following paragraphs can be, as in any real case, incomplete and, at some points, ambiguous or contradictory. The student will therefore need to refine and disambiguate the specifications through interaction with the teacher. In some cases, the student will be required to evaluate different possible alternatives and then choose one in a reasoned manner. The reasons for all interpretative, design, and implementation choices must always be clearly documented in the project and will be discussed during the exam.

*Note*: some of the functionalities required by the specification may not be achievable with single queries, but may require the use of more advanced tools provided by the DBMS, such as procedures. In any case, such procedures would have one or more queries as the main part. The use of these advanced features greatly increases the value of a project. However, in case you decide not to use them in the implementation, it is still necessary to present the corresponding pseudocode and fully implement the related queries.



### Specifications

<section class="descrizione">



The *Soccorso* database represents a generic database for receiving and managing *rescue requests*. The type of assistance offered does not concern us: we will only focus on the general way of managing this kind of request. 

The database will contain information on two categories of users: *administrators* (who configure the system, route the requests and monitor them) and *operators* (to whom the requests will be sent and who will handle them personally). 
Administrators will be able to create accounts for new administrators and operators. For both user categories, in addition to personal data, it should be possible to enter extra information such as the *licenses* held (driving, nautical,...) and a (generic) list of *skills* (for example, an operator might have a nursing diploma, another might be an electrician, etc.) useful for deciding their assignment to missions. 

To carry out rescue operations, operators will have have access to to *vehicles* (cars, ambulances, fire trucks... depending on the type of emergency that will actually be managed by the system) and *equipments* (medical kits, ladders, fire extinguishers,...). Such elements will be recorded in the database (to be very general, they will only have a name and a description), and administrators will be able to add, modify, or delete them.

The *rescue requests* stored in the database must necessarily be accompanied by a brief description, the indication of the location (address, coordinates, etc.), the name and email address of the *reporter*, and may optionally be accompanied by a photo. Furthermore, to avoid spam and various attacks, the system must at least keep track of the IP address from which the requests originate. Finally, every *submitted* request, before becoming *active*, must be *validated*. For this purpose, a long and random string will be associated with the request, which will then be used to construct a link sent via email to the reporter. Clicking this link will mark the request as active in the database.

Requests, based on their management status, can be in an active state (sent and validated), ongoing (managed), and closed (completed).
Active requests can be ignored (canceled) or managed by creating a *mission*. Such a mission will be associated with the triggering request, a goal, a location, a *team* (composed of at least one *team leader* operator and zero or more other operators), zero or more vehicles, zero or more equipments, as well as obviously a start timestamp.

Administrators will be able to insert *updates* (blocks of descriptive text) into a mission at any time, each associated with the input timestamp.

Finally, the administrators (following an appropriate communication from the operators) will be able to mark a mission as completed (closed), entering the end date/time, a generic *success level* (also depending on the type of rescue, we can generally use a number ranging from 0=failure to 5=full success), and optional comments related to the intervention carried out. 

Every element involved in the missions (operators, vehicles, equipments) must also be equipped with its own mission history in which it has been involved.



</section>

There are undoubtedly various constraints that can be applied to the contents of this database. The identification of constraints and their implementation (with constraints on tables, triggers, or at least defining the code and queries necessary to perform the checks) constitute an important requirement for the development of a realistic project, and this will be taken into account during the final evaluation.

### Operations to implement

Below are schematically illustrated the operations to achieve on the database, each to be implemented through a query (or, if necessary, through multiple queries, *optionally* enclosed in a *stored procedure*). Obviously, any further refinement or enhancement of these specifications will increase the value of the project.

<section class="operazioni">



1. Submission of a rescue request.
2. Creation of a mission connected to an active rescue request.
3. Closing of a mission.
4. Extraction of the list of operators not involved in ongoing missions.
5. Calculation of the number of missions carried out by an operator.
6. Calculation of the average time taken to complete missions (*from creation to closure*) in a specific year or for each team leader.
7. Calculation of the number of requests coming from a certain reporting subject (identified by the email address) or from a certain IP address in the last 36 hours.
8. Calculation of the total time spent on missions by a certain operator (*i.e., the sum of the durations of the missions he was involved in*)
9. Extraction of missions carried out in the same location as a given mission over the past three years.
10. Extraction of the list of rescue requests closed with a not fully positive result (success level less than 5).
11. Extraction of the operators most involved in rescue requests closed with a not entirely positive result (*calculated as in the previous query*).
12. Extraction of the history of missions in which a certain vehicle was involved.
13. Calculation of the usage hours of a certain equipment (*let's assume that the usage time corresponds to the total duration of the mission in which it was assigned*).



</section>

It is possible to include additional procedures that are deemed useful.

</section>

<section class="indicazioni break">

# Directions for Project Development

### Technologies

The DBMS to be used for the implementation of the project is MySQL. MariaDB is an acceptable alternative.

*Optionally*, the created database can be equipped with an interface written in a programming language of choice (Java or PHP) through which to invoke the requested queries (providing any necessary parameters) and view the results.

### Project Development and Documentation

The specifications may not be exhaustive or completely defined. Every feature added or refined, also through an interaction with the stakeholder, will be adequately evaluated. All the design choices must be discussed and motivated.

The project must be carried out according to the following phases:

1. Formalization and analysis of requirements.
2. Conceptual design using the Entity-Relationship model.
3. Description of all constraints that cannot be expressed in the ER model.
4. Restructuring and optimization of the ER model.
5. Translation of the ER model into the corresponding relational model.
6. Actual implementation of the relational model and all constraints through SQL.
7. Implementation of queries, procedures, functions, etc. through SQL.

All the phases just described must be accompanied by appropriate documentation **in electronic format** that illustrates what has been accomplished and the choices made.

In particular, the documentation must necessarily include the ER diagrams resulting from steps (2) and (4), duly commented, and the relational model of the database obtained in step (5), highlighting the keys of the various tables and the relationships between them.

The final database, resulting from steps (6) and (7), must be delivered in the form of an *SQL script* containing the database structure (CREATE statements, including any procedures, functions, and views) and the code for the queries necessary to implement the required functionalities.

**The code of each query must be preceded by its identification number and the text of its definition**, as stated in this specification.
*Optionally*, the script may also include test data (INSERT statements).
*Suggestion*: you can use the export functions available in tools like *phpMyAdmin*, *DBeaver*, or *MySQL Workbench*, or directly the *mysqldump* command, to export a *dump* of the database containing both the structure and the data. Moreover, for convenience, in most cases you can also incorporate the definition of queries into the database dump, defining them as views or stored procedures with meaningful names like "Query_1," etc.

By way of example, within the course projects repository, there is a base document structured according to the aforementioned guidelines, from which you can derive your own documentation.

The parts of the specification marked as *optional*, if omitted, will not make the project insufficient but will not allow it to achieve the highest marks either. In case you decide to implement them, the result should not be necessarily perfect or complete, but they should clearly demonstrate your commitment to deal with an advanced topic.

In the case of workgroups composed of multiple members, *the actual contribution of each member* to the project  **must** be declared in the documentation (indicating, for example, who mainly worked on conceptual modeling, who created the database with SQL, who worked specific queries, etc.). During the examination, each group member will describe its part of the project.  

### Project Submission

The *documentation* and the *code* of the project, described in the previous sections,
must be submitted to the teacher **at least a week before** the exam date,
simply by sending it via email.

During the exam, any issues encountered in the project will be discussed, and a demonstration of the functioning of some queries and/or the interface created may be requested (it is therefore advisable to bring a laptop with the project installed and functioning).

### Project Evaluation

To evaluate the project, the following aspects will be considered:

1. General compliance and proper refinement (where necessary) of the specifications.
2. Accuracy and compliance with the specifications of the models created.
3. Technical correctness of the physical implementation of the database (structure, constraints).
4. Technical correctness of the queries and their compliance to the required functionalities.
5. Adequacy of the documentation.

This evaluation will be combined with the result of the project discussion.  

### Additional Information

This specification is available in Web Engineering course repository at the address https://github.com/LaboratorioBasiDiDati-Univaq/LBD_Project_Specifications. 
Additional information on the specifications can be obtained directly via email by writing to giuseppe.dellapenna@univaq.it.

Please note that projects should be carried out by *small* student groups (two/three members is the recommended number). Exceptions to this rule must be agreed with the teacher.  
</section>

