# In this Makefile, we're exploring the ability to reuse the same exact rule 
# for multiple targets. The goal of this is, if a single rule captures what we
# need for multiple unique cases, we can generalize them using variables.
# This example takes from multiple-targets-one-rule
all: f1.o f2.o

# '$@' is an 'automatic variable' that gets set to the current target on the
# execution of said target's rule if it needs to be satisfied. Since the rule
# is the exact same for these two targets, we can share the rule between them
# by using this 'automatic variable' to cover working on each target
f1.o f2.o:
	@echo $@
