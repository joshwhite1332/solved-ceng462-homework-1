Download Link: https://assignmentchef.com/product/solved-ceng462-homework-1
<br>
This assignment aims to assist you to expand your knowledge on informed search in the cases of A* and Iterative Deepening A* algorithms.

<h1>1           Problem Definition</h1>

In this assignment, you are going to solve a Tower of Hanoi puzzle <em>given in any valid state </em>by using A* and Iterative Deepening A* algorithm.

As computer scientist, we love this puzzle and use it everywhere! So, there is a great chance that you’ve seen Tower of Hanoi already as an example for recursion or time complexity etc. However, let’s remember the original definition again, to refresh your memory about the terms and rules of Tower of Hanoi puzzle.

Figure 1: Tower of Hanoi with 5 disks replaced to left-rod initially

<em>Tower of Hanoi </em>is a game consisting of a 3 rods with <em>N </em>disks with varying sizes. Initially, all disks are placed onto a rod in the ascending order of their sizes, so it looks like a neat, canonical shape (see Figure 1). The purpose of the game is moving whole stack of disks to another rod without violating the following rules:

<ul>

 <li>Only one disk can be moved at a time.</li>

 <li>A disk can be moved only if it is on the top of its rod.</li>

 <li>No larger disk can be placed of a smaller one at any time. In other words, the ascending order regarding the size of disks should not be disturbed on any rod during the entire game.</li>

</ul>

Here is an example of initial configuration for a Tower of Hanoi puzzle with 3 disks:

Figure 2: Example configuration as initial state for Tower of Hanoi with 3 disks

where the rods are labeled as “A”, “B” and “C” left to right, and the disk are enumerated from 1 to 3 matching with their sizes (greater number means greater size). In this example, all disks are placed onto the rod “A”. Assuming that the goal rod is “C”, the final state should look like following:

Figure 3: Example configuration as final state for Tower of Hanoi with 3 disks

Unlike the original puzzle, in this assignment, you will also be given initial configurations which represent a valid intermediate state for the original Tower of Hanoi puzzle. Therefore, the initial state given in the input may look like below:

Figure 4: Another example configuration as initial state for Tower of Hanoi with 3 disks

<h1>2           Specifications</h1>

<ul>

 <li>You are going to implement A* and Iterative Deepening A* algorithms (you can refer the lecture slides for pseudocodes.) in python.</li>

 <li>You will use the following function as the heuristic function:</li>

</ul>

<em>f</em>(<em>x,y</em>) = <em>x </em>+ 2 × <em>y                                          </em>(1)

where <em>x </em>is the total number of disks in the “non-goal” rods and <em>y </em>is the number of disks in the goal rod such that their sizes are smaller than any other disk in the other rods.

<ul>

 <li>The task will be given from standard input and the result will be printed to standard output.</li>

 <li>Input will consist of:

  <ul>

   <li>The method you are going to use for the given task (“A*” or “IDA*” for Iterative Deepening A*)</li>

   <li>M as the maximum total estimated cost allowed in the method</li>

   <li>N defining the number of disks,</li>

   <li>The goal rod where the disks are placed in the correct order at the final state,</li>

   <li>The following 3 lines will include the placement of the disks with their enumerated ids in the rod “A”, “B” and “C” at the beginning (<strong>bottom to top and separated with “,”</strong>). If no disk placed onto the related rod, a blank line will be given.</li>

  </ul></li>

 <li>Output will consist of “SUCCESS” or “FAILURE” stating whether the goal is reached or not respectively. If the solution exists with given constraint of total estimated cost, all configurations on the path from the initial configuration to the goal configuration will be printed as well, following a blank line after the indicator of “SUCCESS”.</li>

 <li>Output of a configuration must look like:</li>

</ul>

<table width="634">

 <tbody>

  <tr>

   <td width="84">A−<em>&gt;</em>[2,1]</td>

   <td width="56">B−<em>&gt;</em>[]</td>

   <td width="494">C−<em>&gt;</em>[3]</td>

  </tr>

 </tbody>

</table>

Content of a rods as lists (bottom to top), separated with the tab character, and a new line character at the end is included. To ease to understand and comply this format, here is the pattern I used with the format() method in the python:

“A-&gt;{}tB-&gt;{}tC-&gt;{}
”

<ul>

 <li>While expanding a node you are required to try to move a disk in the <strong>lexical order </strong>(First “A” to “B”, then “A” to “C”, then “B” to “A” and so on.)</li>

 <li>When searching for the state with the minimum cost you will select the <strong>first </strong>one for tie-breaking.</li>

</ul>

<strong>IMPORTANT NOTE: </strong>Complying the output format and the last 2 items is crucial for the blackbox evaluation. Please avoid any violation of them, in order not to lose any points redundantly.

<h1>3           Sample I/O</h1>

<strong>Input 1:</strong>

A∗

4

3

C 2

1

3

<strong>Output 1:</strong>

SUCCESS

A−<em>&gt;</em>[2] B−<em>&gt;</em>[1] C−<em>&gt;</em>[3]

A−<em>&gt;</em>[] B−<em>&gt;</em>[1] C−<em>&gt;</em>[3, 2]

A−<em>&gt;</em>[] B−<em>&gt;</em>[] C−<em>&gt;</em>[3, 2 ,                  1]

<strong>Input 2:</strong>

A∗

3

5

B

5 ,3 ,2 ,1

4

<strong>Output 2:</strong>

FAILURE

<strong>Input 3:</strong>

<table width="673">

 <tbody>

  <tr>

   <td width="673">IDA∗103 A3 ,2 ,1</td>

  </tr>

 </tbody>

</table>

<strong>Output 3:</strong>

SUCCESS

A−<em>&gt;</em>[] B−<em>&gt;</em>[3, 2 ,                 1] C−<em>&gt;</em>[]

A−<em>&gt;</em>[1] B−<em>&gt;</em>[3, 2] C−<em>&gt;</em>[]

A−<em>&gt;</em>[1] B−<em>&gt;</em>[3] C−<em>&gt;</em>[2]

A−<em>&gt;</em>[] B−<em>&gt;</em>[3] C−<em>&gt;</em>[2, 1]

A−<em>&gt;</em>[3] B−<em>&gt;</em>[] C−<em>&gt;</em>[2, 1]

A−<em>&gt;</em>[3] B−<em>&gt;</em>[1] C−<em>&gt;</em>[2]

A−<em>&gt;</em>[3, 2] B−<em>&gt;</em>[1] C−<em>&gt;</em>[]

A−<em>&gt;</em>[3, 2 ,               1] B−<em>&gt;</em>[] C−<em>&gt;</em>[]

<strong>Input 4:</strong>

<table width="673">

 <tbody>

  <tr>

   <td width="673">IDA∗53 A3 ,2 ,1</td>

  </tr>

 </tbody>

</table>

<strong>Output 4:</strong>

FAILURE