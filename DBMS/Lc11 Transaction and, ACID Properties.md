# Lc11. Transaction and, ACID Propeties

## Transaction
- A unit of work done against the DB in a logical sequence. 
- The sequence is important aspect of transaction as if something breaks, the transaction is either go back to the initial state after failure or, complete it. There's no in the middle kind of stuffs happening here. 
As in the above picture demonstrate the way it is done. 

## Acid properties (Atomicity, Consistency, Isolation, Durability)
Ever transaction in the db requires to follow ACID properties which helps ensuring the integrity of data.
1. Atomicity
	-> Every operations of the transaction should be reflected in the database. 
1. Consistency:
	-> The db stays in a good state(consistency), before and after transaction
	-> Integrity constraints must be maintained before and after transaction
1. Isolation:
	->Transactions in db happens in isolation which do not bother or, interrupt other transactions that is happening. 
1. Durability:
	-> After transactions are done, it is saved in db forever. DB updates persists.

![[Pasted image 20240611184439.png]]
## Transaction states in DB
1. Active state: The first state in any transaction. All the read/write operations are performed here.
	 a. If T(Transaction) is done **without any error**, the state changes to **partially committed state**
	 b. If T **occurs error**, the state changes to **Failed state**
2. Partially committed state: After the transaction is executed  the changes are saved in the buffer in the main memory. If the changes made are **permanent** on the DB then the state will transfer to the **committed state** and, if there is a **failure in transaction**, the T will go in the **failed state.** 
3. Committed state: When **updates are made permanent** on the DB. Then the T is said to be in the **committed state**. Rollback can’t be done from the committed states. New consistent state is achieved at this stage.
4. Failed state: When T is being executed and some failure occurs. Due to this it is impossible to continue the execution of the T.
5. Aborted state: When T reaches the failed state, all the changes made in the buffer are reversed. After that the T rollback completely. T reaches abort state after rollback. DB’s state prior to the T is achieved.
6. Terminated state: A transaction is said to have terminated if has either committed or aborted.