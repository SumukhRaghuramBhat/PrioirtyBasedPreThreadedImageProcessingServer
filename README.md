# PrioirtyBasedPreThreadedImageProcessingServer

Developing an image processing server that inter-
acts with clients through a pool of worker threads using the producer consumer
model. The server consists of a main thread and a set of worker threads with
the main thread running at a higher priority than the worker threads. 

The main thread repeatedly accepts connection requests from clients and places the
resulting connected descriptors in a bounded buffer. Each worker thread repeat-
edly removes a descriptor from the buffer, services the client, and then waits
for the next descriptor. All the threads are scheduled with the FIFO policy.
The image server applies image processing operations on the image input by
the client. These image processing operations are derived from the open source
OpenCV library.


1. Multi-threaded producer-consumer: An array is used to implement a
bounded buffer. Producer and consumer threads write and read data
from this buffer synchronizing with locks and condition variables using
the Pthread API

2. Real time scheduling and priorities in Linux: Demonstrates how to assign
real time priority and scheduling policy to threads on Linux. Note that
this code needs root permission to run (sudo in Ubuntu).

3. Delay: Spins in a loop for delay seconds. Useful to emulate the execution
of long-running threads.
