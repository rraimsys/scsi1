
# SCSI Interface 
  
- The secondary storage has to implement the SCSI talk and SCSI listen 
- Think of like, every device which connects to the www has to talk IP and TCP 
- Client  - Initiator - Target - Servers - [ imitators talk to targets] 
- When can an entity be both initiator and target at same time? 
- Wrapper around SCSI commands called CDB 
- Why we need a transport layer? What if I want to issue SCSI commands over continents? 
- Device has to acknowledge the data by telling STATUS OK 

  [Link](https://www.cse.scu.edu/~tschwarz/coen180/LN/scsi.html)
  

# SCSI terminology 
  - target : integration of addresses which could be see 
  - initiator : Which finds the target and asks the target to do things 
  - task      :  integration of work items [ commands ]  [ meta data - called as tag ] 
  - task tag - identify the tag 
  - outstanding task  : pending task [ task = collection of commands ] 
  - LBA - [ mapping of exposed address to imitator to the hardware address ] 
  - LUN - each of the addressable entities in a target 
  - IOP - linked commands [ move and read ] [ no two seeks at a times ] 
  -   tagged [ target must accept a series of requests from different initiators ] 
  -   Use disk scheduling [ know which initiator issues the commands [ tags ] 
  -  *What is a command Queue*? 
  -    *Head of Q tag, Simple Q tag* , *Ordered Q tag*
  - SIMPLE QUEUE TAG [ is type of command which can be associated with a command ] 
  -  ORDERED QUEUE TAG [ think of ordering ] - Thinks of it as a pthread_barrier 
  - **SCSI Sense Key**  [ command queue - has untagged commands - the target gets a queue tag ] Abort 
  - *Abort Tag, Abort, Reset, Async Event Notification, Clear Queue[ stop the IOP ] * 
  - Ready to transfer, read32 commands. 
  

## SCSI Functionality 
- client selects a target 
- targets are slower   [ targets are secondary storage ] 
- Since the target is slower
-  target decides - when to process the SCSI commands 
- Why does the target WANTS to process the commands? 
- Re selection - target notices, does it's job, and tells it's ready to process 
- READ comes from slower device - Writes come from faster device 
![enter image description here](https://i.ibb.co/Vtk44xk/scsi1.png)
  

 - Why there is an extra step in the Write sequence? 
 ![enter image description here](https://i.ibb.co/9wFscky/scsi2.png)
  

- client wants big amounts of data granularity 
- does not wants to be bothered [ target ] 
- break the I/O and offset pairs - The HBA does it 
- 5GB per second - What if there is a need of controller incase of internet? 
- ![enter image description here](https://i.ibb.co/SJpkrs5/scsi3.png)

- *the target talks back to the client* directly - useful for internet 

![enter image description here](https://i.ibb.co/JQsJmF9/scsi4.png)


- *flow control is not needed in case of reads*

## SCSI Architecture 

![enter image description here](https://i.ibb.co/F5sC92Y/scsi5.png)
  

![enter image description here](https://i.ibb.co/FWFyHYq/scsi6.png)

  

