# Lab 2
[Fork](https://docs.github.com/en/get-started/quickstart/fork-a-repo) this repo and clone it to your machine to get started!

## Team Members
- Richard Ochoa Jr.
- Ana Sanson Raquel

## Lab Question Answers

Question 1: How did the reliability of UDP change when you added 50% loss to your local
environment? Why did this occur?
It received faster but some of the packets were lost. That’s because there’s no confirmation of data transfer when using UDP. 


Question 2: How did the reliability of TCP change? Why did this occur?

All the numbers were sent in the correct sequence because TCP repeatedly sends packets until the other side receives it.


Question 3: How did the speed of the TCP response change? Why might this happen?

The speed of the TCP response was slower. It’s because it keeps sending all packets over and over until the other side receives it. 

1. What is argc and *argv[]?
argc is the count of inputs from the command line and argv is an array of command line inputs.

2. What is a UNIX file descriptor and file descriptor table?
File descriptor: is the unique non-negative number assigned to an open file in a computer system that identifies it. It describes a data resource and how to get to it. Every open file in a computer has at least one file descriptor. 
File description table: is an int array of file descriptors. Each file descriptor is a pointer to file table entries. 

https://www.engeniustech.com/reliable-packet-transmission-with-udp/#:~:text=UDP%20(User%20Datagram%20Protocol)%20is,verification%20of%20the%20data%20transfer.
https://www.engeniustech.com/reliable-packet-transmission-with-udp/#:~:text=UDP%20(User%20Datagram%20Protocol)%20is,verification%20of%20the%20data%20transfer.


3. What is a struct? What's the structure of sockaddr_in?
A struct groups together variables like a class with no member functions. sockaddr_in contains serv_addr and cli_addr.

4. What are the input parameters and return value of socket()
The input parameters for socket() are AF_INET for the domain, SCOK_STREAM to choose TCP type, and 0 to choose the IP. The function returns the socket’s descriptor that identifies the socket.

https://www.geeksforgeeks.org/socket-programming-cc/ 

5. What are the input parameters of bind() and listen()?
For bind() the input parameters are socket, address, address_len

In the code the socket is sockfd, the address is (struct sockaddr *) &serv_addr, and the address_len is sizeof(serv_addr)

https://www.ibm.com/docs/en/zos/2.4.0?topic=functions-bind-bind-name-socket

For listen() the input parameters are int s, int backlog. Where s is a descriptor of the bound, unconnected socket and backlog is the maximum length that the connections pending may reach.

In the code, s is sockfd and backlog is 5. 

https://www.mkssoftware.com/docs/man3/listen.3.asp


6.  Why use while(1)? Based on the code below, what problems might occur if there are multiple simultaneous connections to handle?
	The while loop ensures that only one client is connected to the socket at a time. If there were multiple simultaneous connections, the read() function might get a mix of different messages in one and won’t be able to interpret the scrambled message.


7. Research how the command fork() works. How can it be applied here to better handle multiple connections?

The command fork() duplicates the process. In other words, ir is called by one process and returns in two. Thus there’s a parent (original) and a child (new). The parent receives the pid of the child and the child returns 0. If an error occurs, there is no child created and the parent receives -1. After using fork() an exact duplicate of the parent process is created but it has its own copies of file descriptors. 

https://www.section.io/engineering-education/fork-in-c-programming-language/
https://stackoverflow.com/questions/15102328/how-does-fork-work

When using fork() the child process runs at the same time as the parent process. Thus, it will help us to better handle multiple connections by creating a new child process that runs simultaneously to other clients’ execution. 

https://www.geeksforgeeks.org/design-a-concurrent-server-for-handling-multiple-clients-using-fork/


8. This program makes several system calls such as 'bind', and 'listen.' What exactly is a system call?

A system call is the execution of a function that is validated by the socket layer and sent to the protocol layer to carry out tasks for the socket.

https://developer.ibm.com/articles/au-tcpsystemcalls/ 

