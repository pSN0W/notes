u# Create Neighborhood
## 1 process
- Took more than 1hrs 30 mins
## 20 process
- Using tqdm process map.
- sometimes htop looks like this
- ![[Pasted image 20230701013804.png]]
- Time taken 6:56 seconds. Want it to be <5
- Wth is this?
- ![[Pasted image 20230701013940.png]] Ignoring it for now since will be using multiprocessing anyway.
- ![[Pasted image 20230701014033.png]]
- With chunksize set to 100
- ![[Pasted image 20230701022621.png]]
- Chunk Size 20
- ![[Pasted image 20230701024209.png]]
## 30 Processes
- ![[Pasted image 20230701133753.png]]
## 10 Processes
![[Pasted image 20230701144500.png]]
## 1 Process

![[Pasted image 20230701153323.png]]
## Without any process

![[Pasted image 20230701175021.png]]
## Without Grid
- It takes around 21 minutes
## MP 20

# Predict Time
## batch_size 512
- took around 40 mins