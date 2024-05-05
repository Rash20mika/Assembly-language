COMPUTER ORGANIZATION

ASSEMBLY LANGUAGE

      
At first let us discuss about the programming language and where we are using those languages.

A programming language is a formal language comprising a set of instructions used to produce various kinds of output. It allows humans to communicate instructions to computers in a manner that they can understand and execute. Programming languages consist of syntax rules and semantics that determine how instructions are structured and interpreted. These instructions can be used to create software applications, websites, algorithms, and more. Programming languages vary widely in their complexity, purpose and application domain and new languages contribute to emerge as technology evolves.
And now let us discuss the assembly language.

Assembly language is a low-level programming language that provides a way to communicate directly with a computer's hardware. It uses mnemonic codes and symbols that represent specific machine instructions. It has direct interaction with the hardware of the system. Unlike high-level programming languages, assembly language offers minimal abstraction from the underlying hardware. Programmers must have a deep understanding of the system architecture and the behavior of individual instructions. It has many types of assembly languages,

Some other examples of assembly languages include:

x86 Assembly Language: Used for Intel and AMD x86 architecture processors, commonly found in PCs and servers.

ARM Assembly Language: Used for ARM architecture processors, commonly found in mobile devices, embedded systems, and IoT devices.

PowerPC Assembly Language: Used for PowerPC architecture processors, formerly used in Macintosh computers and gaming consoles like the PlayStation 3.

SPARC Assembly Language: Used for SPARC architecture processors, commonly found in Sun Microsystems and Oracle servers.

68k Assembly Language: Used for Motorola 68000 series processors, popular in older personal computers and gaming consoles.

MIPS Assembly language

In this we are mainly focusing about the mips code

What is MIPS assembly language?

Some other examples of assembly languages include:

RISC Architecture:

MIPS is a Reduced Instruction Set Computing (RISC) architecture. It emphasizes a small, simple set of instructions that execute in a single clock cycle, which makes it relatively straightforward to learn and understand.

Instruction Types:
MIPS instructions can be classified into several types:

R-type instructions: Arithmetic and logical operations between registers.
I-type instructions: Operations with immediate values (constants).
J-type instructions: Jump instructions for control flow.

It uses branching and jumping by the instruction beq, bge, blt,bneq and j for jump statements.

Let us see how we can write the code in assembly language,
At first we should know about the mnemonic in assembly language. Then what is mnemonics? Let us see now,
A mnemonic is a symbolic representation of an instruction or operation. Mnemonics are designed to be more human-readable and easier to remember than the binary machine code instructions they represent. Each mnemonic corresponds to a specific machine instruction or operation that the processor can execute.

Example:
Let us consider the instruction,
      ADD R3,R2,R1
Here ADD is the mnemonic which is used to add two registers and store in the third register.
R1,R2,R3 are registers. 
Now let us see few more mnemonics,



![WhatsApp Image 2024-04-29 at 10 25 58 PM](https://github.com/Rash20mika/Assembly-language/assets/168262492/920ce9bc-aa0b-49b1-b812-ffe5d07faead)


Let us see few examples using these mnemonics in the instruction.

         ADD R2,R3,#10
         
In this instruction adds the number 5 to the contents of register R3 and puts the result into register R2. The number sign is not the only way to denote the Immediate addressing mode. In some assembly languages, the Immediate addressing mode is indicated in the OP code mnemonic. For example, the previous Add instruction may be written as,

         ADDI R2,R3,10
         
The suffix I in the mnemonic ADDI states that the second source operand is given in the Immediate addressing mode.

        and $rd, $rs, $rt
        
Performs a bitwise AND operation on the values in registers $rs and $rt, storing the result in register $rd.

       or $rd, $rs, $rt
       
Performs a bitwise OR operation on the values in registers $rs and $rt, storing the result in register $rd.

       sw R1,R2
       
Stores the value R1 into R2

       lw R1,R2
       
Load the word R2 in R1
 

Let us see the simple mips program to sum the first 10 natural numbers.
        li $t0, 0
        li $t1, 1

    loop:
        add $t0, $t0, $t1
        addi $t1,$t1,1
        bgt $t1, 10, exit
        j loop
    exit: 
        sw $t0, sum

Here’s Explanation for the above code

li $t0, 0: Initializes register $t0 to 0, which will hold the sum.

li $t1, 1: Initializes register $t1 to 1, which will be the loop counter.

loop label: Marks the beginning of the loop.

add $t0, $t0, $t1: Adds the loop counter to the sum.

addi $t1, $t1, 1: Increments the loop counter.

bgt $t1, 10, exit: Branches to exit if the loop counter is greater than 10.

j loop: Jumps back to the loop label to repeat the loop.

exit label: Marks the end of the program.

sw $t0, sum: Stores the final sum in the sum variable.

Let us consider the code for odd or even

        lw $t0, number        
        andi $t1, $t0, 1     
        beq $t1, $zero, even  
        li $v0, 1             
        move $a0, $t0         
        syscall               
        even:
          li $v0, 4            
          la $a0, even_msg     
          syscall               
          j end
       end:
         li $v0, 10           
         syscall

Explanation for above code

lw $t0, number: This instruction loads the value stored at the memory address labeled number into register $t0.

andi $t1, $t0, 1: This instruction performs a bitwise AND operation between the value in register $t0 and the immediate value 1, storing the result in register $t1.

beq $t1, $zero, even: This instruction branches to the even label if the value in register $t1 is equal to zero (i.e., the number is even).

li $v0, 1: This instruction loads the system call code 1 into register $v0, which is the code for printing an integer.

move $a0, $t0: This instruction moves the value from register $t0 (which holds the number) into register $a0, which is the argument register for system calls.

syscall: This instruction invokes the system call specified by the value in register $v0 (printing the number in this case).

j end: This unconditional jump instruction jumps to the end label, skipping the even section of the code.

even:: This line defines the even label.

li $v0, 4: This instruction loads the system call code 4 into register $v0, which is the code for printing a string.

la $a0, even_msg: This instruction loads the address of the null-terminated string even_msg into register $a0.

syscall: This instruction invokes the system call specified by the value in register $v0 (printing the even message).

j end: This unconditional jump instruction jumps to the end label to exit the program after printing the message.

end:: This line defines the end label.

li $v0, 10: This instruction loads the system call code 10 into register $v0, which is the code for exiting the program.

syscall: This instruction invokes the system call specified by the value in register $v0 to exit the program.


Real world Applications using Assembly language

Operating Systems

Assembly language is often used in the development of operating systems, as it provides low-level access to the system's hardware and is capable of executing critical operations that are not possible with higher-level languages.

Device Drivers

Assembly language is used to develop device drivers, which are software components that allow a computer to interact with specific hardware devices.

Embedded Systems

Assembly language is widely used in the development of embedded systems, such as microcontrollers and other specialized devices that have limited processing power and memory.

Performance-critical applications

Assembly language can be used to optimize performance-critical sections of code in high-performance applications, such as video games, simulations, and scientific computing.

Reverse Engineering

Assembly language is often used in reverse engineering, as it provides a detailed understanding of the underlying machine code and can be used to analyze malware, debug software, and study the internal workings of operating systems and other software.


Current Trends in the Assembly Language Industry
     
With cybersecurity threats increasing, there's an increased emphasis on using assembly language for security assessment and developing more secure firmware and low-level software components.
The Internet of Things (IoT) sector drives demand for assembly language expertise to develop highly efficient and optimized firmware for microcontrollers and embedded devices.
A specialized but growing interest in retro computing and game development for vintage systems is leading to renewed interest in assembly language programming for these platforms.
There's a trend towards integrating assembly language blocks within high-level language code (e.g., C or C++) for crucial performance sections, merging efficiency with developer productivity.
