Download Link: https://assignmentchef.com/product/solved-csci203-csci803-assignment-2-operation-of-a-supermarket-by-a-discrete-event-simulation
<br>
You have been hired by a major supermarket chain to model the operation of a proposed supermarket by using a Discrete Event Simulation. The shop has several servers (or checkouts), each of which has a different level of efficiency due to the experience of the server operator. It also takes longer to serve credit card customers. The service time of each customer is calculated as follows:

<strong><em>                service_time  =  (tally_time  x  efficiency)  +  payment_time </em></strong>        where:

<table width="462">

 <tbody>

  <tr>

   <td width="189">                  <strong><em>tally_time:</em></strong></td>

   <td width="273"><em> time it takes to tally up the customer’s goods</em></td>

  </tr>

  <tr>

   <td width="189">                   <strong><em>efficiency:</em></strong></td>

   <td width="273"> <em>the efficiency of the server</em></td>

  </tr>

  <tr>

   <td width="189">                  <strong><em>payment_time:</em></strong></td>

   <td width="273"> <em>0.3 for cash or 0.7 for credit card</em></td>

  </tr>

 </tbody>

</table>

<strong>The input file “ass2.txt” contains the records of each customer entering the shop and consist of:  </strong>

<ol>

 <li><strong>arrival time </strong><em>(at the server queue), </em></li>

 <li><strong>tally time </strong><em>(time it takes to scan the customer’s items and add up the cost) </em></li>

 <li><strong>payment method </strong><em>(cash or card).</em></li>

</ol>

<strong>Your program should: </strong>

<ol>

 <li>Open the text file “ass2.txt” (Note: “ass2.txt” should be a hardcoded as a constant.) 2. Read the efficiencies of each server.</li>

 <li>Read and process the customer arrival and service time data.</li>

 <li>Print service statistics on the screen.</li>

</ol>

<strong>Note: </strong>

<ol>

 <li>This shop has a single queue of customers waiting to be served.</li>

 <li>The servers are initially all idle.</li>

 <li>If more than one idle server is available, the next customer is served by the server with the best efficiency (i.e. the smallest efficiency value).</li>

 <li>Customers must be served or queued in the order in which they arrive.</li>

 <li>You should not attempt to read in all the arrival data at the start of the simulation.</li>

</ol>

At the end of the simulation, after the last customer in the file has been served, your program should print out the following information:

<ol>

 <li>The number of customers served.</li>

 <li>The time that it took to serve all the customers.</li>

 <li>The greatest length reached by the customer queue.</li>

 <li>The average length of the customer queue.</li>

 <li>The average time spent by a customer in the customer queue. (If a customer is served immediately, their queue time is 0.0).</li>

 <li>The percentage of customers who’s waiting time in the customer queue was 0 (zero).</li>

 <li>For each server:

  <ol>

   <li>The number of customers they served</li>

   <li>The time they spent idle.</li>

  </ol></li>

</ol>

You must choose appropriate data structures and algorithms to accomplish this task quickly. You will lose marks if you use STL, or equivalent libraries, to implement data structures or algorithms.  Note: A larger input data file may be used for the final assessment of your program.

Step-1 (Week-7 demo)

For step 1 you are to implement the simulator’s <em>customer queue</em> and <em>event queue</em>.

Implement the <em>customer queue</em> (FIFO queue). It should have a maximum size of 500 records. Each record in the customer queue should contain two doubles and a boolean (i.e. <em>arrival time, tally time </em>and <em>payment method</em>). Your customer queue should have functions for adding an item (enqueue), removing an item (dequeue), and for testing if the queue is empty. (Note: C++ and Java coders should also add a constructor for initialsing the queue.)

FIFO Queue




Test your customer queue by declaring an instance of it in the main(). Use a for loop to add 10 records to the queue. Set the <em>arrival time</em> for each record between 1 and 100 using rand() or random(). The other fields can be set to 0 or false. Also, print the <em>arrival times</em> on the screen as you add them. Now use a while loop to remove all the records from the customer queue and print the <em>arrival times</em> on the screen. Is the output correct?

Now implement the simulator’s event queue (i.e. a priority queue). The event queue’s records should contain an <em>event type</em> (int or enum), <em>event time</em> &amp; <em>tally time </em>(doubles), and   <em>payment method</em> (boolean).  You can assume the maximum number of events in the event queue is 100. The record with the minimum <em>event time</em> has the highest priority.




Test the event queue by declaring an instance of it in the main(). Use the while loop (implemented previously) to remove records from the customer queue and add them to the event queue. Set the <em>event time</em> with the customer’s <em>arrival time</em>. Set the other fields to zero. Then implement a while loop in the main() to remove (dequeue) each record from the event queue and print the <em>event time</em> on the screen. Is the output correct?

<u>Note:</u> For step-1 (to get the 2 demo marks) you can implement the customer and event queues using any method you like. However, for the final submission, to get full marks, you should ensure all data structures and algorithms are optimised for speed.

<strong>           </strong>

<strong> </strong>

<h2>Step-2 (Server array implementation)</h2>

The server array should have a maximum of 20 servers. Each server should have a busy flag (boolean), an efficiency factor (double) and other data members for calculating the stats. C++ and Java coders should implement the server array with a class, preferably, and provide public functions for adding, and removing customers to/from the servers, finding the fasted idle server, etc. according to the specs on page 1. <strong> </strong>

<h2>Step-3 (Processing in the data)</h2>

When you have the <em>customer queue</em>, <em>event queue</em> and <em>server array</em> correctly completed, delete the main() test code from step 1 and replace it with code for reading the input data file “ass2.txt” and processing the data, as explained on page 1. The following algorithm shows how a typical discrete time simulator can be implemented:

<em>main() </em>

<em>          Declare variables and instances and do initialisations </em>

<em>          Open the input data file;  if not found print error and exit  </em>

<em>        Read first CustomerArrival event from file and add it to the event queue     While the event queue is not empty . . . </em>

<em>                    Get the next event from the event queue and set CrntTime to the event time                      If the event type = CustomerArrival event . . .                                   if an idle server is available . . . </em>

<em>                                            Find fastest idle serve                                                 set the server’s idle flag to busy                                                 calculate the server’s finish time from event’s customer data                                                add ServerFinish event to the event queue </em>

<em>                             Else </em>

<em>                                       Add event’s customer to the customer queue </em>

<em>                              End if </em>

<em>                              If not EOF . . . </em>

<em>                                            Read next customer arrival from file                                  add CustomerArrival event to the event queue </em>

<em>                              End if </em>

<em>                    Else // event type must be a ServerFinish event . . . </em>

<em>                                Get server no. from event, set server[no] to idle and do server’s stats                              If customer queue is not empty . . . </em>

<em>                                            Get next customer from the customer queue                                             Find fastest idle serve                                                 set the server’s idle flag to busy.                                        calculate the server’s finish time                                             add ServerFinish event to the event queue </em>

<em>                              End if </em>

<em>                    End if </em>

<em>          End while </em>

<em>          Print stats </em>

<em>End main()</em><strong>                                                 </strong>

<strong> </strong>

<h2>Step-4 (Optimisation and stats)</h2>

When you have the discrete time simulation working correctly, add the necessary data members and variables needed for calculating all the required stats, as explained on page 1, and optimise your simulator for speed.

<h2>Step-5 (Specifications)</h2>

In a comment block at the bottom of your program (no more than 20 lines of text) list all the data structures and algorithms used by your program to process the input data. Include any enhancements you did to speed up your program (if any). For this step, marks will be awarded based on how accurately and clearly you describe your program.

<strong> </strong>

<h1>Compilation</h1>

All programs submitted must compile and run on banshee:

<h2>C:     gcc ass2.c  C++:      g++ ass2.cpp Java:    javac ass2.java Python: python ass2.py</h2>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<ul>

 <li>Programs which do not compile on banshee with the above commands will receive zero marks. It is your responsibility to ensure that your program compiles and runs correctly.</li>

</ul>

<strong> </strong>