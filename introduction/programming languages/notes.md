Modern computers are incredibly fast, and getting faster all the time. However, computers also have some significant constraints: they only natively understand a limited set of commands, and must be told exactly what to do.

A computer program (also commonly called an application) is a set of instructions that the computer can perform in order to perform some task. The process of creating a program is called programming. Programmers typically create programs by producing source code (commonly shortened to code), which is a list of commands typed into one or more text files.

The collection of physical computer parts that make up a computer and execute programs is called the hardware. When a computer program is loaded into memory and the hardware sequentially executes each instruction, this is called running or executing the program.

# Machine Language

A computer’s CPU is incapable of speaking C++. The limited set of instructions that a CPU can understand directly is called machine code (or machine language or an instruction set).

Here is a sample machine language instruction: 10110000 01100001

Back when computers were first invented, programmers had to write programs directly in machine language, which was a very difficult and time consuming thing to do.

How these instructions are organized is beyond the scope of this introduction, but it is interesting to note two things. First, each instruction is composed of a sequence of 1s and 0s. Each individual 0 or 1 is called a binary digit, or bit for short. The number of bits that make up a single command vary -- for example, some CPUs process instructions that are always 32 bits long, whereas some other CPUs (such as the x86 family, which you are likely using) have instructions that can be a variable length.

Second, each set of binary digits is interpreted by the CPU into a command to do a very specific job, such as compare these two numbers, or put this number in that memory location. However, because different CPUs have different instruction sets, instructions that were written for one CPU type could not be used on a CPU that didn’t share the same instruction set. This meant programs generally weren’t portable (usable without major rework) to different types of system, and had to be written all over again.

# Assembly Language

Because machine language is so hard for humans to read and understand, assembly language was invented. In an assembly language, each instruction is identified by a short abbreviation (rather than a set of bits), and names and other numbers can be used.

Here is the same instruction as above in assembly language: mov al, 061h

This makes assembly much easier to read and write than machine language. However, the CPU can not understand assembly language directly. Instead, the assembly program must be translated into machine language before it can be executed by the computer. This is done by using a program called an assembler. Programs written in assembly languages tend to be very fast, and assembly is still used today when speed is critical.

However, assembly still has some downsides. First, assembly languages still require a lot of instructions to do even simple tasks. While the individual instructions themselves are somewhat human readable, understanding what an entire program is doing can be challenging (it’s a bit like trying to understand a sentence by looking at each letter individually). Second, assembly language still isn’t very portable -- a program written in assembly for one CPU will likely not work on hardware that uses a different instruction set, and would have to be rewritten or extensively modified.

# High-level Languages

To address the readability and portability concerns, new programming languages such as C, C++, Pascal (and later, languages such as Java, Javascript, and Perl) were developed. These languages are called high level languages, as they are designed to allow the programmer to write programs without having to be as concerned about what kind of computer the program will be run on.

Here is the same instruction as above in C/C++: a = 97;

Much like assembly programs, programs written in high level languages must be translated into a format the computer can understand before they can be run. There are two primary ways this is done: compiling and interpreting.

A compiler is a program that reads source code and produces a stand-alone executable program that can then be run. Once your code has been turned into an executable, you do not need the compiler to run the program. In the beginning, compilers were primitive and produced slow, unoptimized code. However, over the years, compilers have become very good at producing fast, optimized code, and in some cases can do a better job than humans can in assembly language!

Here is a simplified representation of the compiling process:
![Alt text](image.png)

Since C++ programs are generally compiled, we’ll explore compilers in more detail shortly.

An interpreter is a program that directly executes the instructions in the source code without requiring them to be compiled into an executable first. Interpreters tend to be more flexible than compilers, but are less efficient when running programs because the interpreting process needs to be done every time the program is run. This means the interpreter is needed every time the program is run.

Here is a simplified representation of the interpretation process:
![Alt text](image-1.png)
Example of interpreting
Optional reading

A good comparison of the advantages of compilers vs interpreters can be found here.

Most languages can be compiled or interpreted, however, traditionally languages like C, C++, and Pascal are compiled, whereas “scripting” languages like Perl and Javascript tend to be interpreted. Some languages, like Java, use a mix of the two.

High level languages have many desirable properties.

First, high level languages are much easier to read and write because the commands are closer to natural language that we use every day. Second, high level languages require fewer instructions to perform the same task as lower level languages, making programs more concise and easier to understand. In C++ you can do something like a = b * 2 + 5; in one line. In assembly language, this would take 5 or 6 different instructions.

Third, programs can be compiled (or interpreted) for many different systems, and you don’t have to change the program to run on different CPUs (you just recompile for that CPU). As an example:

![Alt text](image-2.png)
There are two general exceptions to portability.

The first is that many operating systems, such as Microsoft Windows, contain platform-specific capabilities that you can use in your code. These can make it much easier to write a program for a specific operating system, but at the expense of portability. In these tutorials, we will avoid any platform specific code.

The second is that some compilers also support compiler-specific extensions -- if you use these, your programs won’t be able to be compiled by other compilers that don’t support the same extensions without modification. We’ll talk more about these later, once you’ve installed a compiler.


# Before C++, there was C

The C language was developed in 1972 by Dennis Ritchie at Bell Telephone laboratories, primarily as a systems programming language (a language to write operating systems with). Ritchie’s primary goals were to produce a minimalistic language that was easy to compile, allowed efficient access to memory, produced efficient code, and was self-contained (not reliant on other programs). For a high-level language, it was designed to give the programmer a lot of control, while still encouraging platform (hardware and operating system) independence (that is, the code didn’t have to be rewritten for each platform).

C ended up being so efficient and flexible that in 1973, Ritchie and Ken Thompson rewrote most of the Unix operating system using C. Many previous operating systems had been written in assembly. Unlike assembly, which produces programs that can only run on specific CPUs, C has excellent portability, allowing Unix to be easily recompiled on many different types of computers and speeding its adoption. C and Unix had their fortunes tied together, and C’s popularity was in part tied to the success of Unix as an operating system.

In 1978, Brian Kernighan and Dennis Ritchie published a book called “The C Programming Language”. This book, which was commonly known as K&R (after the authors’ last names), provided an informal specification for the language and became a de facto standard. When maximum portability was needed, programmers would stick to the recommendations in K&R, because most compilers at the time were implemented to K&R standards.

In 1983, the American National Standards Institute (ANSI) formed a committee to establish a formal standard for C. In 1989 (committees take forever to do anything), they finished, and released the C89 standard, more commonly known as ANSI C. In 1990 the International Organization for Standardization (ISO) adopted ANSI C (with a few minor modifications). This version of C became known as C90. Compilers eventually became ANSI C/C90 compliant, and programs desiring maximum portability were coded to this standard.

In 1999, the ISO committee released a new version of C called C99. C99 adopted many features which had already made their way into compilers as extensions, or had been implemented in C++.

# C++

C++ (pronounced “see plus plus”) was developed by Bjarne Stroustrup at Bell Labs as an extension to C, starting in 1979. C++ adds many new features to the C language, and is perhaps best thought of as a superset of C, though this is not strictly true (as C99 introduced a few features that do not exist in C++). C++’s claim to fame results primarily from the fact that it is an object-oriented language. As for what an “object” is and how it differs from traditional programming methods, well, we’ll cover that in later chapters.

C++ was standardized in 1998 by the ISO committee (this means the ISO standards committee approved a document describing the C++ language, to help ensure all compilers adhere to the same set of standards). A minor update to the language was released in 2003 (called C++03).

Five major updates to the C++ language (C++11, C++14, C++17, C++20, and C++23) have been made since then, each adding additional functionality. C++11 in particular added a huge number of new capabilities, and is widely considered to be the new baseline version of the language. Future upgrades to the language are expected every three or so years.

Each new formal release of the language is called a language standard (or language specification). Standards are named after the year they are released in. For example, there is no C++15, because there was no new standard in 2015.

# C and C++’s philosophy

The underlying design philosophy of C and C++ can be summed up as “trust the programmer” -- which is both wonderful and dangerous. C++ is designed to allow the programmer a high degree of freedom to do what they want. However, this also means the language often won’t stop you from doing things that don’t make sense, because it will assume you’re doing so for some reason it doesn’t understand. There are quite a few pitfalls that new programmers are likely to fall into if caught unaware. This is one of the primary reasons why knowing what you shouldn’t do in C/C++ is almost as important as knowing what you should do.