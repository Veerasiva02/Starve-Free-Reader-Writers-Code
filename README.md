# Starve-Free-Reader-Writers-Code
# Solution
The solution for starve free readers-writers problem is using priority queue. By using the FIFO priority queue we can ensure starvation doesn't happen.
# Code :
semaphore x,y,s;//All should be initialised to 1
int Count=0;
Readers :

wait(x);
wait(y);
if(Count==0) wait(s); 
Count++;
signal(y);
signal(x);
//Reading 
wait(y);
Count--;
if(Count==0) signal(s);  
signal(y);

Writers :

wait(x); 
wait(s);
signal(x);
//Writing
signal(s);
