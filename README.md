# CPU-less parralel execution of lambda calculus in digital logic
his repository contains a demonstrational implementation of CPU-less parralel execution of lambda calulcus in digital logic consisting of 3 files.

1. logisim-evolution.jar 
2. LambdaCalculus.circ
3. ExampleExecution.txt

This README document will show the steps required to simulate and example execution and read it's output.
# How to load and execute
First open logisim-evolution.jar. In the top left of the application select File --> Open and find and select the LambdaCalculus.circ file downloaded from this github

![First Step](https://github.com/user-attachments/assets/e63e638c-a126-49e2-aef9-630e8d2472aa)

Once you have opened LambdaCalculus.circ select the left most RAM component highlighted in red. Then in the component properties menu select contents (click to edit) to open the contents of the Hex Editor.

![SecondStep](https://github.com/user-attachments/assets/2b2a1fd8-a902-4dd3-a0b6-fdc3e25337c9)

In the Hex Editor select Open and open ExampleExecution.txt. Alternativley you may wish to enter your own expression which you may do by opening a different .txt document or manually changing memory locations wihtin the hex editor.

![ThirdStep](https://github.com/user-attachments/assets/d725b99c-3e86-4177-8a2d-1550e4e366ea)

Finally select Simulate and ensure Simulation Enable is ticked. Then either begin simulation by pressing Ctrl+T to manually trigger a clock tick or tick the box next to Ticks Enabled to cause a clock pulse every so many Hz definable in the tick frequency pop out menu.

![FourthStep](https://github.com/user-attachments/assets/d8ecc54a-0106-448d-bc97-6753911c87fd)
