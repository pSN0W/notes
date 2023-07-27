# Introduction to DBMS
- Data : Fact that can be recorded
- Database : Collection of related data that represents some real world entity (It is important that you database gets updated)
- Information : Meaningful / Processed data

## Why not just store it in file
- Lets say you are storing name, phone number and email of your friend. The easiest way to store data will be putting it in a text file. Now lets say the problem with this
	- If you have multiple such text files then you will need to know location of all such text files. This might be problematic. **Location Problem**
	- Now if you want to share just phone number with one of your friend then you will need to create one more file with only phone number so you have **data redundancy** that means same data is available at multiple places.
	- Now lets imagine what happens when you update the phone number so you will need to update it in all those places. **inconsistency**

## What is DBMS and how does it help
- Previously in the file type of system you were directly interacting with the database. That had its problem of Location Transparency. **USER <--> DB**
- DBMS is like a intermediary between the two and it provides a level of abstraction for the user so you don't need to keep track of where the files are **USER<--> DBMS <--> DB** 
- With DBMS if you want just phone number you can write a simple query and then return a view of the dataset.
- DBMS makes it easier to deal with storage and retrieval of data

# File System VS DBMS
- In file system kind or architecture the user which has the file can read and write from it. Lets say you want to access some 1KB data but it is stored somewhere in a 25GB file so you will first need to download the 25GB and then you can use the 1KB but wilh DBMS you can write a query to extract the exact data.
- With file system you will need to know about the metadata of the file and the location of the file to get the information you desire while with DBMS writing a query does the job.
- **Concurrency**: With DBMS you can have multiple read at the same time I don't know if it is possible for file system. Generally it results in difference between the data.
- **Security**: With DBMS you can have a role based security while with file system this is not possible.
- **Redundancy**: Data duplicate is reduced in case of DBMS

# Data Abstraction
![[Pasted image 20230719122048.png]]
There are three level of abstraction of the data
- **External Schema**: This is where you define how the user view the data as different user can have different view. Student and Faculty can view different columns associated with the data.
- **Conceptual Schema**: This is how you database are connected. This is where you define the ER models and how different tables are related with each other. Backend Engineer work here
- **Physical Schema**: This is how your data is physically stored. Which disks are used to store the data. This deals with file storage, even if you are keeping data in table in disc it is stored as files only.

