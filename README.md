# CPU-less parallel execution of lambda calculus in digital logic
This repository contains a demonstrational implementation of CPU-less parralel execution of lambda calulcus in digital logic consisting of 3 files.

1. logisim-evolution.jar 
2. LambdaCalculus.circ
3. ExampleExecution.txt

This README document will show the steps required to simulate an example execution and read it's output.

For a video demonstration of how to load, execute and read an example execution click the link below.
https://youtu.be/s3cJ1NrnWbM

# How To Load And Execute
First open logisim-evolution.jar. In the top left of the application select File --> Open and find and select the LambdaCalculus.circ file downloaded from this github

![First Step](https://github.com/user-attachments/assets/e63e638c-a126-49e2-aef9-630e8d2472aa)

Once you have opened LambdaCalculus.circ select the left most RAM component highlighted in red. Then in the component properties menu select contents (click to edit) to open the contents of the Hex Editor.

![SecondStep](https://github.com/user-attachments/assets/2b2a1fd8-a902-4dd3-a0b6-fdc3e25337c9)

In the Hex Editor select Open and open ExampleExecution.txt. Alternativley you may wish to enter your own expression which you may do by opening a different .txt document or manually changing memory locations wihtin the hex editor.

![ThirdStep](https://github.com/user-attachments/assets/d725b99c-3e86-4177-8a2d-1550e4e366ea)

Finally select Simulate and ensure Simulation Enable is ticked. Then either begin simulation by pressing Ctrl+T to manually trigger a clock tick or tick the box next to Ticks Enabled to cause a clock pulse every so many Hz definable in the tick frequency pop out menu. (Note higher frequencies may cause simulation errors depending on the power of your device)

![FourthStep](https://github.com/user-attachments/assets/d8ecc54a-0106-448d-bc97-6753911c87fd)

After the simulation has been complete the newley reduced expression can be found in the rightmost RAM component.

![FithStep](https://github.com/user-attachments/assets/cced908e-b3db-438a-83c9-96bcb4661838)

# Reading Inputs And Outputs
Each RAM location represents a singular node as a 12 bit binary value. The 11th bit represents the inital state of the resolve flag, bits 10-8 represent the expression type bits 7-4 represnt the nodes child left pointer and bits 3-0 represent the nodes child right pointer. Expression Types have been encoded into 3 bits using the following key:

1. 000: Undefined
2. 001: Name
3. 010: Application
4. 011: Function
5. 100: GoTo

Finally the memory address of the 12 bit binary value in each RAM component represents the unique node ID of the node that should contain these values. Note the first node in any tree must be stored in the root node (Node with Unique Node ID == 0) and you will be unable to edit or read from nodes disconnected from the tree structure.

As an example if we want our tree to be a single name expression in node 0 with Child Left and Right equal to F (15) our RAM component should contain the 12 bit binary value 1FF in memory location 0.

The example execution stored in ExampleExecution.txt represents the tree detailed in the PACT submission paper sharing this Github's name. A good way to visualise the tree structure is to create a spreadsheet of node ID's expression types and child pointers and use that to construct a tree diagram.

![Initial Graph](https://github.com/user-attachments/assets/f2c699fb-3771-4557-b9e8-3d307fa112dd)

When the simulation has finished you can convert the rightmost RAM back into a tree diagram to find the result. Note that all these nodes will have a raised resolve flag meaning the 11th most bit will be a raised. So in the previous example with the single node graph, node 0 was a name and was instantiated with the line 1FF. the output RAM address 0 will contain 9FF due to the raised resolve flag.

Again here is the output of example execution again mimicing the tree detailed in the PACT submission paper
![Final Graph](https://github.com/user-attachments/assets/a8396cf0-57b4-464f-9f7f-62659d74df48)

# Reading Node Internal Values
Certain LED's, Output Wires and Memory Components have been included to allow you to see the graph changing during execution. Each node outputs to a 1 bit LED which displace the statue of its resolve flag, a 3 bit output wire which displays its current expression type using the prior stated key and the contents of its RAM component all highlighted in the image below.

![LEDArrangment](https://github.com/user-attachments/assets/88f07a4a-fa4c-44a6-a2b0-ecde71207ace)
