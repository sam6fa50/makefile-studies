# This is how we can push a shell variable in our rules, by simply specifying a
# variable in the 'command' portion of a rule, which naturally executes in a 
# shell environment (one shell per line, so you can't share data across 
# different lines without using '\' to make it appear like the same command is
# on two lines, or ';' to separate shell commands directly
make_var = I am a make variable

all:
	@sh_var='I am a shell variable'; echo $$sh_var
	@echo $(make_var)
