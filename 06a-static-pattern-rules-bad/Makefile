# There's another way to reduce how much we write in a Makefile, called static
# pattern rules. They take the following shape:
# targets...: target-pattern: prereq-patterns ...
# 	commands
#
# We match the selected 'target' with 'target-pattern' using the '%' wildcard,
# which we are delibrately covering now because it was a bit more complex than
# the '*' wildcard. 
# Whatever we matched using '%' is called the 'stem'.
# The 'stem' is substituted into the 'prereq-pattern' to generate the 
# 'targets'' 'prerequsities' dynamically. 
# This allows us to generate 'prerequisites' dynamically based on what we 
# found relevant to match across the selected 'target' in 'targets'.
# Once again, having multiple 'target's in one line just means that we are 
# applying the same rule to each 'target' in the list of 'targets'
# This file contains a POOR example that can be simplified.
CC = gcc
objects = foo.o bar.o all.o

all: $(objects)
	$(CC) $^ -o all

foo.o: foo.c
	$(CC) -c $^ -o $@

bar.o: bar.c
	$(CC) -c $^ -o $@

all.o: all.c
	$(CC) -c $^ -o $@

all.c: 
	echo "int main() { return 0; }" > $@

# First % use EVER, this match does not cover all.c because Make always
# prioritizes the concretely defined rule, i.e. the rule right above this 
# comment
%.c:
	touch $@

clean:
	rm -f $(wildcard *.c) $(wildcard *.o) all
