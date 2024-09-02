This repo is Randal Hyde's Assembler Developer Kit as it was last
published, before it was abandoned.
I have converted it into a HIDE project. I believe it
has some useful features and code that can be of benefit to some.
The source is presented "as is" in whatever state it happens to be in.

=======================================================================

The webster site contains the writeup documentation and concept for HLA3
The original sources may also be available. There is no guarantee that the
links still work.

https://www.plantation-productions.com/Webster/HighLevelAsm/hla3/0_hla2.html

==========================================
Assembler Developer's Kit (ADK) / HLA v2.0
==========================================

Many beginning assembly language programmers think that
programming tools such as compilers and assemblers are "magic"
systems. Somehow, these amazing programs convert ASCII-based
source files into executable code, using techniques
sufficiently advanced that they truly are "magic" to the
beginning programming.

Of course, as time passes and the beginning programmer gains
experience and knowledge, they learn the basic concepts of
opcode construction in memory and many such programmers decide
to create their own "assembler" to help them better understand
the process of code generation. Such assemblers generally
start off as "experiments" and rapidly become development
tools that the author (and, possibly, other programmers) use
for software development.

A big problem with such "hobby" assemblers is that they rarely
contain professional-quality features. Once the author gets
past the "interesting" parts of the project, specifically:
converting mnemonics to opcodes, they quickly discover that
the rest of the language system consists of a lot of "grunt"
work and their attention quickly turns elsewhere.  As a
result, most of these "hobby" projects wind up containing
minimalist features above and beyond the processing of basic
machine instructions.  A classic indication of this phenomenon
is the lack of a powerful macro processing system (or even a
lack of macro facilities altogether). Another indication of
this problem is the lack of decent data structure support in
the assembly language created by the author (e.g., no
"structs" or "records" in their language).  The problem is,
implementing these features requires considerable technical
knowledge and is, quite frankly, a lot of work.  Authors of
such products respond with comments like "such features are
not 'true' assembly language and don't belong in an
assembler."  Nonsense. Commercial quality assemblers have had
these features for at least two decades. They are an absolute
requirement in a modern, commercial-quality assembly language
product.

Another problem with many "hobby-level" assemblers is low
performance. Though some hobby assemblers are every bit as
fast as (or faster than) their commercial counterparts, it's
also the case that many such hobby endeavors are written by
programmers who don't have much experience writing
high-performance compilers and assemblers. As such, the
performance of such products tends to degenerate as you
attempt to process larger and larger projects with them.

The "Assembler Developer's Kit" (ADK) is a  language design
toolkit intended to help alleviate the problem of
low-performance, low-feature, assemblers (and other language
systems).  The ADK provides a huge amount of public-domain
(totally free) source code that you can use to create
assemblers, compilers, interpreters, and scripting languages.
It provides a high-performance solution with pre-written
source code that handles all the "hard" stuff found in a
commercial-quality, high-featured assembler:

1.	The ADK provides a very powerful macro and 
	"compile-time language" system. Far more 
	powerful than any existing assembler (even 
	more powerful than MASM, TASM, and HLA).

2.	The ADK provides a high-performance lexer/parser 
	that operates at between 100,000 and 1,000,000 
	lines per SECOND on a 3.00 GHz Pentium (actual 
	speed varies based on the size of the source file 
	and the complexity of the source code the ADK code
	is processing). For all intents and purposes,
	this is instantaneous for all but the very largest
	source files.

3.	The ADK supports a wide variety of data types
	and operations. Integers from 8 bits to 128 bits.
	32, 64, and 80 bit IEEE floating point formats.
	Character sets supported include 7-bit ASCII,
	8-bit extended ASCII, and 16-bit Unicode.
	Character sets, arrays, records, unions, and
	classes/objects. Plus many more advanced data
	structures.

4.	The ADK supports a wide range of compile-time
	operators and functions. Included with the
	ADK are hundreds of compile-time functions.
	Plus you have the ability to create your
	own compile-time functions using the ADK's
	macro facilities.

5.	The ADK fully supports namespaces, nested
	declarations (block structured languages),
	and other advanced symbol structures that
	you don't find in hobby, or even in many
	"professional quality" assemblers.

6.	The ADK supports the most poweful macro system
	found in any x86 assembler. It is so powerful,
	you can easily create just about any statement
	(e.g., HLL-like statements) using nothing more
	than the ADK macro facilities.  Combined with
	the ADK's "compile-time language" facilities,
	no other assembler (or other language processor)
	can touch the ADK's capabilities.

7.	The ADK's compile-time language fully supports
	facilities such as include files, conditional
	compilation/assembly, compile-time looping,
	and compile-time complex data types for constants
	(e.g., compile-time array, records/structs,
	unions, and character sets).

8.	The ADK provides an advanced, high-performance
	symbols management system (symbol table) using
	fast algorithms while providing considerable
	flexibility for nearly any symbol organization
	you can imagine.

9.	The ADK is well-tested. The package includes
	a regression test suite that tests every
	executable line of code in the program
	(i.e., a "code coverage" test). Furthermore,
	the test suite is automated, so an ADK
	developer can easily run the tests after
	making changes or extensions to the ADK.

10.	The ADK is robust. It includes lots of
	"defensive" code to check for unexpected
	conditions. It is also full of ASSERT
	statements that check for illegal values
	and unexpected results (the ASSERTs can
	be disarmed and eliminated from the code
	by changing *one* statement in the source
	files). It handles large and small projects
	with relative ease (e.g., one of the programs
	in the test suite is 4MB long, containing
	over 115,000 lines of code (packed, almost
	no blank lines and no comments, with roughly
	one symbol definition and two additional
	symbol references per line; on a 3GHz PIV,
	by the way, the ADK compiles this file in
	454 ms at a rate of 253,682 lines/second).

11.	The ADK will be portable across OSes (currently,
	only Win32 is supported, but there is only one
	module that contains OS-specific code and this
	will be modified to support Linux in the near
	future).

12.	The ADK source code is well-documented and
	well-commented. The lexical analyzer is easy
	to maintain. New reserved words can be added
	to the language by adding them to a text file
	and running a utility to generate the high-
	performance scanner for the lexical analyzer.
	Extending the lexer is a relatively straight-
	forward process.  The parser uses an easy-to-
	understand and maintain recursive-descent,
	predictive, parser. Though the ADK provides
	a large amount of source code, programmers
	with a minimum of language design/implementation
	theory behind them can easily extend the
	system according to their own desires. Though
	the current syntactical model of the ADK
	is that for HLA v2.0 (as the ADK is being
	used to develop HLA v2.0), it's easy enough
	to modify the syntax that the ADK accepts
	to support any syntax you choose.

13.	The ADK is written in HLA. As the ADK is
	being used to create HLA v2.0, this means
	that the ADK is written in the language that
	the ADK (natively) supports. Therefore, you
	don't have to learn a different language
	in order to work on the ADK source code
	(assuming you keep the existing ADK syntax).
	The syntax for the ADK source code is very
	similar to the language that the ADK is
	written in.

14.	The ADK provides a solution for most of the
	"grunt" work needed to create a high-performance
	fully-featured assembler.  As this is being
	written, the ADK contains just under 90,000
	lines of source code.

15.	As noted, the ADK is being used to develop
	the High Level Assembler (HLA) v2.0. Therefore,
	you can be assured of continuing development
	of the ADK system.


-------------
Using the ADK
-------------

The ADK is written in assembly language, using HLA v1.x.
Therefore, to use the ADK you will need to install HLA (if you
haven't done so already). You can obtain a copy of HLA
(the High Level Assembler) from http://webster.cs.ucr.edu.

The ADK uses a standard "make" file to control building the
final executable. You will need a "make.exe" program in
order to build the ADK.	You can use Microsoft's "nmake.exe"
program for this purpose (note, however, that if you want
to use the automated test suite that accompanies the ADK,
you'll need a make program that is actually named "make.exe";
if you're using Microsoft's nmake.exe program, just make a
copy and name the copy "make.exe").

Once you've installed the HLA v1.x system, you can build the
ADK system by CD'ing into the HLA2 subdirectory (which
contains the ADK) and type "make".  In a minute or so, you
should be greated by the completion of the ADK compilation.

NOTE TO "FHLA" USERS: if you want to compile the ADK using
HLA and FASM (rather than HLA and MASM), then use the
command line:

	make -f makefile.fhla

This will create the executable file (HLA2.EXE) using HLA and
FASM rather than HLA and MASM. Note that the test suite only
uses the HLA/MASM combination. If you want to use FASM in the
test suite, you'll have to go in an modify all the make files
in the test suite yourself.

Once the compilation of the ADK is complete, you'll wind up
with the executable file (assuming no compilation errors)
"HLA2.EXE".  As this is being written, the ADK executable
(HLA2.EXE) compiles declaration sections only. Support for
machine instructions (or other language statements) is left to
the assembler developer who is using the ADK as a development
aid.

--------------------------
Extending the ADK Language
--------------------------

The ADK, as it exists while this is being written, supports
declaration sections for an HLA-like language. If you don't
particularly like this syntax, that's okay. You can easily
change the parser to use any syntax you like. You can remove
features you don't want to support (much easier than adding
features).

The ADK is relatively "processor-neutral" at this time. Though
the lexer does recognize certain x86 reserved words (such as
mnemonics and register names), it's a simple matter to replace
those x86-specific names with others (for example, if you
wanted to develop a PowerPC assembler). The x86 reserved words
are only  referenced in a few limited places in the ADK source
code, so you can easily change them, if that's what you want
to do. Other than reserved words, the only place x86-isms
creep in are in the code that looks for memory expressions.
This code is easy to remove (and replace by something else) if
you decide to create an assembler for a different processor or
if you decide to create a high-level language rather than an
assembler.

Currently, there are a couple of documentation files in the
"Doc" subdirectory. However, these are starting to get out of
date and the information is eventually going to wind up in
comments in the source code. Nevertheless, you might want to
scan through these documents -- they'll give you a good idea
of how the ADK system operates (internally).