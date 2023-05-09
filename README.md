# auto_diff
Automated Testing Script

the Script automates the testing by running the exe with each input file, 
comparing the program's output with the expected output.

Run the command:
	./auto_diff.sh.x -dvl <program_name>.exe <input_test_name> <expected_output_name>

How to use:
----------
1) Place your EXE file in the same directory as the "auto_diff.sh.x".
2) Make Sure that in the same directory you have the folders (if not create them):
		"in" -put your input files here.
		"cout"- put your expected output files here. 
		"out" - The output files of you program will go here
		"log" - The diff/valgrind log will go there
3) instal or make sure you have this tools (you can copy paste the command):
		gcc (probably already have):	sudo apt-get install build-essential
		diff (probably already have):	sudo apt-get install diffutils
		valgrind:			sudo apt-get install valgrind
    
How to run:
----------
Run the command:
		./auto_diff.sh.x -dvl <program_name>.exe <input_test_name> <expected_output_name>
FLAGS:
	-d : diff falg
	-v : valgrind flag
	-l : log_save

NOTE1: 
don't forget to do:
		 chmod +x auto_diff.sh.x
NOTE2: 
You can run several tests by passing multiple input and output in a chained sequence:
		./auto_diff.sh.x -dvl <program_name>.exe <input1> <exout1> <input2> <exout2> <input3> <exout3> ...

NOTE3: 
	test file (input&output) have sto start with "test" 
	(like "test1.in" "test_044101_out.txt")!!!!
NOTE4:
	the script should work on v-box: mamat_vm-1.16-linux
	
EXAMPLE:
--------
root@Sagi $ ./auto_diff.sh.x -dvl prog.exe test-2.txt test-2.out test-1.in test-1.out
----------------------------------------------------
OUTPUT PASS example:
----------------------------------------------------
program exe:            prog.exe
input file:             in/test-2.txt
program out:            out/test-2.out
expected:               cout/test-2.out

Diff test PASS: test-2 - outputs are identical
Valgrind test PASS: no memory leak found

log/LOG[05-08][20-41-07][test-2][PASS][PASS].txt

----------------------------------------------------
OUTPUT FAIL example:
----------------------------------------------------
program exe:            prog.exe
input file:             in/test-1.in
program out:            out/test-1.out
expected:               cout/test-1.out

Diff test FAIL: test-1 - outputs are differ
Valgrind test FAIL: memory leak found

log/LOG[05-08][20-55-55][test-1][FAIL][FAIL].txt

