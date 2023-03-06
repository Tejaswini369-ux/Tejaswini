# Explaination
In classical readers-writers solution if readers came continously there is no space for writers to get execuuted but inorder to execute the readers,writers in the fifo order then it will be starve free 
so ,this starve free solution is done by pseudocode written in the other file
firstly cntrl_mutex is used to detect if reader came or writer came if writer comes it will be zero in writers section so that no reader can access the critical setion or update adcount
And next rdwr_mutex signals writer when all the reader that are in critical section left and signals readers when writer completes writing
so that all instructions can be executed in fifo manner there will not be any starvation
# there is no deadlock in this code
