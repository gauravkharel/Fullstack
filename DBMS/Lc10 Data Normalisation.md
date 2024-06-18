Lc10. Data Normalisation

Normalisation is a step towards DB optimisation.

Functional Dependency (FD)
It's a relationship between the primary key attribute (usually) of the relation to that of the other attribute of the relation.
X -> Y, the left side of FD is known as a Determinant, the right side of the production is known as a Dependent.

## Types of FD
1. Trivial FD
	A → B has trivial functional dependency if B is a subset of A. A->A, B->B are also Trivial FD.
1. Non-trivial FD
	A → B has a non-trivial functional dependency if B is not a subset of A. A intersection B is NULL.

## Rules of FD (Armstrong’s axioms)
	1. Reflexive
	If ‘A’ is a set of attributes and ‘B’ is a subset of ‘A’. Then,
	A→ B holds. If A ⊇ B then A → B.
1. Augmentation
	If B can be determined from A, then adding an attribute to this functional dependency won’t change anything.
	If A→ B holds, then AX→ BX holds too. ‘X’ being a set of attributes.
3. Transitivity
	If A determines B and B determines C, we can say that A determines C.
	if A→ B and B→ C then A→ C.

### Why Normalisation?
To avoid redundancy in the DB, not to store redundant data.

### What happen if we have redundant data?
Insertion, deletion and updation anomalies arises.

## Anomalies
Anomalies means abnormalities, there are three types of anomalies introduced by data redundancy.
1. Insertion anomaly
	When certain data (attribute) can not be inserted into the DB without the presence of other data.
2. Deletion anomaly
	The delete anomaly refers to the situation where the deletion of data results in the unintended loss of som other important data.
3. Updation anomaly (or modification anomaly)
	The update anomaly is when an update of a single data value requires multiple rows of data to be updated.
	Due to updation to many places, may be Data inconsistency arises, if one forgets to update the data at all the
4. intended places.
	Due to these anomalies, DB size increases and DB performance become very slow.
	To rectify these anomalies and the effect of these of DB, we use Database optimisation technique called

## NORMALISATION.

What is Normalisation?
Normalisation is used to minimise the redundancy from a relations. It is also used to eliminate undesirable characteristics like Insertion, Update, and 

Deletion Anomalies.
Normalisation divides the composite attributes into individual attributes OR larger table into smaller and links them
using relationships.

The normal form is used to reduce redundancy from the database table.

### Types of Normal forms
1. 1NF
	Every relation cell must have atomic value.
	Relation must not have multi-valued attributes.

2. 2NF
	Relation must be in 1NF.
	There should not be any partial dependency.
	All non-prime attributes must be fully dependent on PK.
	Non prime attribute can not depend on the part of the PK.

3. 3NF
	Relation must be in 2NF.
	No transitivity dependency exists.
	Non-prime attribute should not find a non-prime attribute.
	BCNF (Boyce-Codd normal form)
	Relation must be in 3NF.
	FD: A -> B, A must be a super key.
	We must not derive prime attribute from any prime or non-prime attribute.

### Advantages of Normalisation
- Normalisation helps to minimise data redundancy.
- Greater overall database organisation.
- Data consistency is maintained in DB.
