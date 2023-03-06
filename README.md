# Explaination
In classical readers-writers solution if readers came continously there is no space for writers to get execuuted but inorder to execute the readers,writers in the fifo order then it will be starve free 
so ,this starve free solution is done by pseudocode written in the other file
firstly cntrl_mutex is used to detect if reader came or writer came if writer comes it will be zero in writers section so that no reader can access the critical setion or update adcount
And next rdwr_mutex signals writer when all the reader that are in critical section left and signals readers when writer completes writing
so that all instructions can be executed in fifo manner there will not be any starvation
## there is no deadlock in this code
# pseudocode
//initialising semaphores 
cntrl_mutex=1,rdwr_mutex=1,rd_mutex=1;
integer value rdcount=0;

//Pseudocode begins

WRITERS:

wait(cntrl_mutex);
//ensures either reader or writer one of the both should enter critical section
wait(rdwr_mutex);
//wait until all readers in critical section gets exuceted
signal(cntrl_mutex)
//once writer is ready to enter critical section either reader/writer can enter so it unlocks the control mutex
//critical section
signal(rdwr_mutex);
//after writing signals reader/another writer

READERS:
wait(cntrl_mutex)
//ensures either reader or writer one of the both should enter critical section
wait(rd_mutex)
//wait until a reader updates the rdcount only one reader can update at a time
rdcount++;
if(rdcount==1)
wait(rdwr_mutex) //wait until writer completes writing
signal(rd_mutex) //reader is going to enter critical section signals another reader to update the read count
signal(cntrl_mutex) // reader/writer can start executing
//critical section
wait(rd_mutex);//only one reader can access readcount
rdcount--;//reader leaving critical section
if(rdcount==0)
signal(rdwr_mutex);//if all readers in critical section get executed then next reader/writer can start executing
