# Laboratorio di Basi di Dati Course<br/>*Final Projects A.Y. 2024/2025* - Specification #2

<section class="specifica">

## Project "Market"
> Version 2

### Preamble

The course projects are inspired by real-world needs. The informal specification of the problem given in the following paragraphs can be, as in any real case, incomplete and, at some points, ambiguous or contradictory. The student will therefore need to refine and disambiguate the specifications through interaction with the teacher. In some cases, the student will be required to evaluate different possible alternatives and then choose one in a reasoned manner. The reasons for all interpretative, design, and implementation choices must always be clearly documented in the project and will be discussed during the exam.

*Note*: some of the functionalities required by the specification may not be achievable with single queries, but may require the use of more advanced tools provided by the DBMS, such as procedures. In any case, such procedures would have one or more queries as the main part. The use of these advanced features greatly increases the value of a project. However, in case you decide not to use them in the implementation, it is still necessary to present the corresponding pseudocode and fully implement the related queries.



### Specifications

<section class="descrizione">



The *Market* database supports an online purchasing system similar to the various eCommerce that we all know, but *constrained* and *guided*, as it is designed to be used within a public organisation.

Two types of users will be modeled: *purchasers* and *technicians*. The system will also include an *administrator* whose sole purpose is to register other users.

The system will work as follows. *Remember that you do not need to implement this procedure, but only understand it in order to model the database that will host the data necessary to support it!*

1. **Definition of the *purchase request*.** The purchaser will initially select a *category* (for example *Desktop PC*, *Notebook*, *Desktop*,...) that identifies the type of product to purchase (*optionally the categories may have a tree structure, for example IT > Computer > Notebook*). Each product category has a series of specific *features* associated with it (e.g. amount of RAM and type of CPU for a PC, etc.). The purchaser, to complete his *purchase request*, has therefore to enter the values of all the desired characteristics relating to the selected product category (for each characteristic the *indifferent* option will always be provided). There is also be a *note* space to add any peculiar features not included among the standard ones.

2. **Product search by technical staff.** A staff member will be assigned to the *purchase request* defined in point 1, becoming the *technician in charge*. The technician in charge views the category and characteristics requested by the purchaser and then searches (externally to the system) for an actual product to order (which we shall call *purchase proposal*), associating its description (which includes at least manufacturer name, product name, product code, price, URL for further information and notes) to the *purchase request*.

3. **Review of the purchase proposal.** The purchaser reviews the purchase proposal and *approves* or *rejects* it, providing a *motivation* in the latter case. In the event of a rejected request, the process resumes from step 2, considering that the technician in charge will always be the same. The motivation for the refusal will be shown together with the request information, and the technician in charge will be able to modify the proposed product and forward it again to the purchaser.

4. **Execution of the *purchase order*.** If the purchaser approves the purchase proposal in step 3, the technical staff will proceed with the purchase (this part will not be managed by our application).


5. **Delivery and verification of the product.** When the product is delivered (sooner or later!), the purchaser has to *close* the corresponding purchase request indicating whether the product received has been *accepted*, *rejected because non-compliant* or *rejected because not working*.


</section>

There are undoubtedly various constraints that can be applied to the contents of this database. The identification of constraints and their implementation (with constraints on tables, triggers, or at least defining the code and queries necessary to perform the checks) constitute an important requirement for the development of a realistic project, and this will be taken into account during the final evaluation.

### Operations to implement

Below are schematically illustrated the operations to achieve on the database, each to be implemented through a query (or, if necessary, through multiple queries, *optionally* enclosed in a *stored procedure*). Obviously, any further refinement or enhancement of these specifications will increase the value of the project.

<section class="operazioni">



1. submission of a purchase request (including product category, all required features for that product category, and any additional notes)
2. association of a purchase request with a technician in charge
3. approval of the purchase proposal related to a purchase request
4. deletion of a purchase request from the system
5. extraction of the list of *ongoing* (not closed) purchase requests from a specific purchaser, having an associated purchase proposal but not yet approved or rejected
6. extraction of the list of purchase requests not yet assigned to any technician
7. extraction of the list of purchase requests associated with a specific technician with an accepted purchase proposal but not yet ordered
8. extraction of all details of a purchase request (initial request, potential purchase proposal, approval/refusal by the purchaser with corresponding motivation)
9. count of purchase requests globally managed by a specific technician
10. calculation of the total amount of money spent by a specific purchaser in a calendar year (*suggestion*: this refers to the prices of approved purchase proposals, ordered and with the order closed with acceptance)
11. calculation of the average order fulfillment time by the technicians (the fulfillment time is given by the difference between the moment a purchase request is entered and the moment the product is ordered). *Suggestion*: this means that you need to include some *timestamps* in the database that will be set at the appropriate moments...)


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

