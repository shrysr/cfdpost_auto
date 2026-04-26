#  CFD Post processing with ANSYS 

This program is written in Python 2.7, using Notepad ++ and Sublime Text 3, on a Windows 7 X64 OS. The documentation was written using nvALT, iAWriter and on Github directly. It was used on a daily basis around 2012-2014. The portable version of Spyder was used as an IDE as well, initially, though all development was done with Sublime Text 3. This is among the first programs I ever wrote as I learned Python, and I was proud to use it at work where it saved a boatload of time. 

As you can see - no best practices of ANY kind were followed or known by me at the time. I'm sure there are better ways to interface with ANSYS and CFX nowadays. This repo is being archived and retained more for nostalgia than anything else. 

# Introduction 

- The program was designed to apply ANSYS CFD Post macros (.cse/cst) on several result files in a single specified location, one after the other.

- The user can change the scan locations and paths to ANSYS executables. The requirements to function are the path to the:-
		a. CFX result files, 
		b. post macro (.cst/.cse)
		c. ANSYS CFD Post executable 

- The code is split up into useful functions that can (hopefully) also be used as standalone programs, as per the need. This modularity and reusability should increase in the future.

