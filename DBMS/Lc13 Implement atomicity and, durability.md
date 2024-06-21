# Lc13. Implement atomicity and, durability

## shadow copy scheme
![](Pasted%20image%2020240621162008.png)

1. Based on making copies of DB (aka, shadow copies).
2. Assumption only one Transaction (T) is active at a time.
3. A pointer called db-pointer is maintained on the disk; which at any instant points to current copy of DB.
4. T, that wants to update DB first creates a complete copy of DB.
5. All further updates are done on new DB copy leaving the original copy (shadow copy) untouched.
6. If at any point the T has to be aborted the system deletes the new copy. And the old copy is not affected.
7. If T success, it is committed as,
1. OS makes sure all the pages of the new copy of DB written on the disk.
2. DB system updates the db-pointer to point to the new copy of DB.
3. New copy is now the current copy of DB.
4. The old copy is deleted.
5. The T is said to have been COMMITTED at the point where the updated db-pointer is written to disk.

## Log-based recovery methods
![](Pasted%20image%2020240621162952.png)
1. The log is a sequence of records. Log of each transaction is maintained in some stable storage so that if any failure occurs, then it can be recovered from there.
2. If any operation is performed on the database, then it will be recorded in the log.
3. But the process of storing the logs should be done before the actual transaction is applied in the database.
4. Stable storage is a classification of computer data storage technology that guarantees atomicity for any given write operation and allows software to be written that is robust against some hardware and power failures.
#### Deferred DB Modifications
	- Ensuring atomicity by recording all the DB modifications in the log but deferring the execution of all the write operations
	- until the final action of the T has been executed.
	- Log information is used to execute deferred writes when T is completed.
	- If system crashed before the T completes, or if T is aborted, the information in the logs are ignored.
	- If T completes, the records associated to it in the log file are used in executing the deferred writes.
	- If failure occur while this updating is taking place, we preform redo.
#### Immediate DB Modifications
- DB modifications to be output to the DB while the T is still in active state.
- DB modifications written by active T are called uncommitted modifications.
- In the event of crash or T failure, system uses old value field of the log records to restore modified values.
- Update takes place only after log records in a stable storage.
- Failure handling
	- System failure before T completes, or if T aborted, then old value field is used to undo the T.
	- If T completes and system crashes, then new value field is used to redo T having commit logs in the logs.
