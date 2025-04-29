# cs3500-lab-5--signals-solved
**TO GET THIS SOLUTION VISIT:** [CS3500 Lab 5- Signals Solved](https://www.ankitcodinghub.com/product/cs3500-operating-systems-solved-2/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;109947&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;4&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (4 votes)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CS3500  Lab 5- Signals Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (4 votes)    </div>
    </div>
Lab 5: Signals

Introduction

In this lab we will use system calls and xv6 paging to a tracing and alert mechanism in xv6.

Resources

Similar to the previous assignment, please go through the following resources before beginning this lab assignment:

1. The xv6 book: Chapter 4 (Traps and System Calls): sections 4.1, 4.2, 4.5

2. Source files: kernel/trampoline.S and kernel/trap.c

Note

As part of this assignment, we have provided a clean version of the xv6 repo, with the required files included in it. Please implement your solutions in this repo only. We have also attached the LATEXtemplate of this document. Please write your answers in this file and submit the generated PDF (NOT the .tex).

1 Wake me up when Sep ··· (40 points)

From emails to WhatsApp notifications, we often rely on alerts for certain events. In this section, you will add such an alarm feature to xv6 that alerts a process as it uses CPU time.

1. (2 points) Think of scenarios where such a feature will be useful. Enumerate them.

Solution:

2. (38 points) More generally, you’ll be implementing a primitive form of user-level interrupt/fault handlers. You could use something similar to handle page faults in the application, for example. Feel free to refer to the hints at the end of this section.

1

(a) (10 points) Add a new sigalarm(interval, handler) system call. If an application calls sigalarm(n, fn), then after every n “ticks” of CPU time that the program consumes, the kernel should cause the application function fn to be called. (A “tick” is a fairly arbitrary unit of time in xv6, determined by how often a hardware timer generates interrupts.)

Also create a simple sigreturn() system call which does nothing but returns 0 for the time being. Inoke sigreturn at the end of the alarm handler function fn.

HINT: You need to make sure that the handler is invoked when the process’s alarm interval expires. You’ll need to modify usertrap() in kernel/trap.c so that when a process’s alarm interval expires, the process executes the handler. To this end, you will need to recall how system calls work from the previous labs (i.e., the code in kernel/trampoline.S and kernel/trap.c). Mention your approach as the answer below. Which register contains the user-space instruction address to which system calls return?

Solution:

(b) (8 points) Complete the sigreturn() system call, which ensures that when the function fn returns, the application resumes where it left off.

As a starting point: user alarm handlers are required to call the sigreturn() system call when they have finished. Have a look at the periodic() function in user/alarmtest.c for an example. You should add some code to usertrap() in kernel/trap.c and your implementation of sys sigreturn() that cooperate to cause the user process to resume properly after it has handled the alarm.

Your solution will require you to save and restore registers. Mention your approach as the answer below. What registers do you need to save and restore to resume the interrupted code correctly? (HINT: it will be many).

Solution:

Once you have implemented your solution, modify Makefile accordingly and then run alarmtest. If it passes test0, test1 and test2, run usertests to make sure you didn’t break any other parts of the kernel. Following is a sample output of alarmtest and usertests if the alarm invocation and return have been handled correctly.

$ alarmtest test0 start ……..alarm! test0 passed test1 start …alarm!

..alarm!

…alarm!

..alarm!

…alarm!

..alarm!

…alarm!

..alarm!

…alarm! ..alarm! test1 passed test2 start

…………….alarm!

test2 passed

$ usertests …

ALL TESTS PASSED

$

1.1 Additional hints for test cases

test0: Invoking the handler

Get started by modifying the kernel to jump to the alarm handler in user space, which will cause test0 to print “alarm!”. At this stage, ignore if the program crashes after this. Following are some hints:

• The right declarations to put in user/user.h are:

int sigalarm(int ticks, void (*handler)()); int sigreturn(void);

• Recall from your previous labs the changes that need to be made for system calls.

• sys sigalarm() should store the alarm interval and the pointer to the handler function in new fields in struct proc (in kernel/proc.h).

• To keep track of the number of ticks passed since the last call (or are left until the next call) to a process’s alarm handler, add a new field in struct proc for this too. You can initialize proc fields in allocproc() in kernel/proc.c.

• Every tick, the hardware clock forces an interrupt, which is handled in usertrap() in kernel/trap.c. You should add some code there to modify a process’s alarm ticks, but only in the case of a timer interrupt, something like:

if(which_dev == 2) …

• It will be easier to look at traps with gdb if you configure QEMU to use only one CPU, which you can do by running:

make CPUS=1 qemu-gdb

test1/test2: Resuming interrupted code

Most probably, your alarmtest crashes in test0 or test1 after it prints “alarm!”, or alarmtest (eventually) prints “test1 failed”, or alarmtest exits without printing “test1 passed”. To fix this, you must ensure that, when the alarm handler is done, control returns to the instruction at which the user program was originally interrupted by the timer interrupt. You must ensure that the register contents are restored to the values they held at the time of the interrupt, so that the user program can continue undisturbed after the alarm. Finally, you should “re-arm” the alarm counter after each time it goes off, so that the handler is called periodically. Here are some hints:

• Have usertrap() save enough state in struct proc when the timer goes off, so that sigreturn() can correctly return to the interrupted user code. • Prevent re-entrant calls to the handler: if a handler hasn’t returned yet, the kernel shouldn’t call it again. test2 tests this.

Submission Guidelines

1. Implement your solutions in the provided xv6 folder. Write your answers in the attached LATEXtemplate, convert it to PDF and name it as YOUR ROLL NO.pdf. This will serve as a report for the assignment.

2. Put your entire solution xv6 folder, and the YOUR ROLL NO.pdf in a common folder named YOUR ROLL NO LAB5.

3. Compress the folder YOUR ROLL NO LAB5 into YOUR ROLL NO LAB5.tar.gz and submit the compressed folder on Moodle.

4. NOTE: Make sure to run make clean, delete any additional manual and the .git folder from the xv6 folder before submitting.

Submission Guidelines

1. Implement your solutions in the provided xv6 folder. Write your answers in the attached LATEXtemplate, convert it to PDF and name it as YOUR ROLL NO.pdf. This will serve as a report for the assignment.

2. Put your entire solution xv6 folder, and the YOUR ROLL NO.pdf in a common folder named YOUR ROLL NO LAB5.

3. Compress the folder YOUR ROLL NO LAB5 into YOUR ROLL NO LAB5.tar.gz and submit the compressed folder on Moodle.

4. NOTE: Make sure to run make clean, delete any additional manual and the .git folder from the xv6 folder before submitting.
