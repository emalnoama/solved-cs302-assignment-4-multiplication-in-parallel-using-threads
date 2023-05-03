Download Link: https://assignmentchef.com/product/solved-cs302-assignment-4-multiplication-in-parallel-using-threads
<br>
<h1>Description</h1>

For this assignment, you will multiply two numbers together in parallel using threads. The input for the program will be two numbers separated by a whitespace. You need to store these two numbers into two vectors of type short, so you may need to read in as a string or by character and convert each character into an integer and store into a vector object. When you have this portion completed, you will have two vectors and the index of the digit denotes the place value of the number, for example if I have two numbers

<table width="257">

 <tbody>

  <tr>

   <td width="32">3</td>

   <td width="32">8</td>

   <td width="32">9</td>

   <td width="32">6</td>

   <td width="32">1</td>

   <td width="32">5</td>

   <td width="32">2</td>

   <td width="32">4</td>

  </tr>

  <tr>

   <td width="32"><strong>[0]</strong></td>

   <td width="32"><strong>[1]</strong></td>

   <td width="32"><strong>[2]</strong></td>

   <td width="32"><strong>[3]</strong></td>

   <td width="32"><strong>[4]</strong></td>

   <td width="32"><strong>[5]</strong></td>

   <td width="32"><strong>[6]</strong></td>

   <td width="32"><strong>[7]</strong></td>

  </tr>

 </tbody>

</table>

38961524 and 345761, then your vectors would look like the following number1 =

<table width="192">

 <tbody>

  <tr>

   <td width="32">3</td>

   <td width="32">4</td>

   <td width="32">5</td>

   <td width="32">7</td>

   <td width="32">6</td>

   <td width="32">1</td>

  </tr>

  <tr>

   <td width="32"><strong>[0]</strong></td>

   <td width="32"><strong>[1]</strong></td>

   <td width="32"><strong>[2]</strong></td>

   <td width="32"><strong>[3]</strong></td>

   <td width="32"><strong>[4]</strong></td>

   <td width="32"><strong>[5]</strong></td>

  </tr>

 </tbody>

</table>

number2 =

<h1>Contents of main</h1>

Using these two numbers contained in these vectors, you will need to do long multiplication (like you did in grade school). Except you will do the multiplications in parallel, so for example, one thread will multiply the digit 5 to all of the digits in number1, another thread will multiply digit 6 with all of the digits of number1, and so on. You will join the threads if either you maxed out the number of threads or if all digits of number2 have been multiplied to number1; if after joining all the threads and there is still more work to be done, then keeping spawning threads and assign each thread a digit from number2 to multiply to number1. You will need a vector of type thread to maintain all the threads that are currently running.

After each thread finishes its job, it will push its result onto a 2D vector that maintains all the partial results, this is a shared variable so you may need to use the mutex locking and unlocking functions to make sure any race conditions are handled. This partial results 2D vector and number1 and number2 can all be global vector objects. Once you have all the partial results in your 2D vector and all of your threads are done, you will do long addition using these partial results, you won’t need to multi parallelize this, so you can do this in main without spawning threads.

<h1>Specifications</h1>

<ul>

 <li>Comment your code and your functions</li>

 <li>Make sure you never spawn more threads than your system can handle, use thread::hardware_concurrency() function to determine the amount of threads that can be runned on whatever system you’re using</li>

 <li>Make sure your output has all the leading zeros removed</li>

</ul>

1

<ul>

 <li><strong>IF YOU ARE GOING TO USE THE SCHOOL SERVER TO RUN YOUR CODE, DO NOT USE BOBBY.CS.UNLV.EDU OR SALLY.CS.UNLV.EDU!!! PLEASE USE CARDIAC.CS.UNLV.EDU!!! THANKS!!!</strong></li>

</ul>

<h1>Example Output</h1>

$ g++ -std=c++11 -pthread ParallelMult.cpp $ ./a.out

Enter number1: 345264

Enter number 2: 75611127480

The product is: 26105800318254720

$ ./a.out

Enter number1: 0

Enter number 2: 546376384

The product is: 0

$ ./a.out

Enter number1: 44743934854395034859043854309

Enter number 2: 43543958943905843095843905843584

The product is: 1948328062288575065474002625085484591217696136757287438403456

<h1>Written Portion</h1>

Additionally to your source code, you will be responsible for a 1 page write up, where you want to explain the following

<ul>

 <li>What system/compiler was used to run your program How did you implement the multi-threaded algorithm</li>

 <li>Does parallelization speed up the problem?</li>

 <li>Does adding more threads to the problem always cause a speed up? When does it and when does it not?</li>

 <li>Which parts of your code can be parallelized? Could the portion of your code that might not have been parallelized become parallelized?</li>

</ul>

<h1>Submission</h1>

Upload your source file using the following naming convention LastName_FirstName_A4.cpp and your write up to the moodle site by the deadline

2