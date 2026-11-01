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
# This file contains the GOOD implementation
CC = gcc
objects = foo.o bar.o all.o

all: $(objects)
	$(CC) $^ -o all

# Syntax: targets...: target-pattern: prereq_patterns...
# The '%' captures the 'stem', which can be reused then as a variable. In the
# case of static pattern rules, we clarify the set of targets whom we want to
# operate the matching on.
$(objects): %.o: %.c
	$(CC) -c $^ -o $@

all.c: 
	echo "int main() { return 0; }" > $@

# This is an example of the implicit pattern rule, in which it serves as an 
# intermediary rule that simplifies / serves as a bucket rule for all inputs 
# that match against it, but it is never a rule that runs line by line on its 
# own because the 'target' name is needed to match. It is called, however, by
# the static pattern rule usage in this example when, in objects, 'foo.o' gets 
# matched with 'foo.c' from the stem 'foo', and Make searches for a rule for
# 'prerequisite' 'foo.c'. In searching for it, it finds this implicit pattern
# rule that can match against it with the stem once more becoming 'foo'. The 
# stem is discarded in this case, however, because we do not actually need it,
# instead we just take the full 'target' name 'foo.c' and touch the filesystem
# if that file is out of date compared its 'prerequisites', which are none, so
# DNE.
# This match does not cover all.c because Make always prioritizes the concretely
# defined rule, i.e. the rule right above this 
# comment
%.c:
	touch $@

clean:
	rm -f $(wildcard *.c) $(wildcard *.o) all
