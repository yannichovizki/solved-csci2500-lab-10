Download Link: https://assignmentchef.com/product/solved-csci2500-lab-10
<br>
<ol>

 <li><strong>Checkpoint 1: </strong>For the first checkpoint, download the s MIPS code. Walk through the code to understand what it does. Consider uncommenting the debugging blocks of code to display what is in memory address $s0 at each loop iteration.</li>

</ol>

Once you understand the code, comment out the debugging output for the time being. The problem with the given code is that the control overhead is too high, i.e., we load, add, and store, then jump to our latch basic block. Excluding the jumps, we have 25% overhead.

To optimize this code, replicate the contents of the loop_body basic block three more times (for a total of four load/add/store combinations). Make sure you use the correct offsets and increment value in the loop_latch basic block. Verify that your code still works by again adding the debugging statements.

Note that this technique is called <em>loop unrolling</em>.

<ol start="2">

 <li><strong>Checkpoint 2: </strong>For the second checkpoint, note that we load our values exclusively into register $t0. Thinking back to Homeworks 2 and 4, there is no reason why we could not use more of the temporary registers. Make this adjustment in the given code by cycling through registers $t1, $t2, etc. And note by doing so, we effectively remove dependencies that are not true dependencies.</li>

</ol>

This technique is simply called <em>register renaming</em>.

<ol start="3">

 <li><strong>Checkpoint 3: </strong>For the third checkpoint, we can use a technique to <em>minimize stalls </em>by reordering our instructions. Note that we have a familiar (and problematic) pattern, i.e., a load followed by an add. The problem with this pattern is that it has to stall the pipeline since the data is not ready until the MEM stage, but we need that data prior to the ALU stage of the next instruction. Our instruction stream therefore requires a nop instruction between the load and the increment instructions. Reorder the instructions such that no such nop instruction is required.</li>

</ol>

Finally, given all of the above optimizations, how much have all of these transformations reduced the runtime for this code sequence?