some_file: other_file
	@# @<command> suppresses the printing of the command without suppressing
	@# the output of the command, i.e. the command still runs and outputs
	@# what it is supposed to, but the printing of the command with its 
	@# arguments just never happens
	@echo "This will always run because we will never create other_file"
	touch some_file

other_file:
	@echo "Will never make other_file!!"

