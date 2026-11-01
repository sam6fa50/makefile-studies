# We can define targets that do not need to be files, as files do not have
# to be targets (exist beforehand) and targets do not have to be files 
# (serve as broader scopes/commands rather than genuine files that are
# 'made').
# Prerequisites are best understood as targets that must be brought up to
# data before the commands defined for the target having these dependencies can
# exist, specifically brought up to date compared to the timestamp of the file
# that corresponds to the target name. In this instance, all targets need to
# brought up to date timestamp wise with the file called 'all'.
# Since the file 'all' doesn't exist, and won't exist, since it's not really a
# file that we're making but rather a phony for a build scope, no timestamp
# comparison for 'one', 'two', and 'three' can occur against 'all', but the 
# target still runs, in fact it always runs-- why?. This is because Make 
# considers a *target whose corresponding file doesn't exist as always out
# of date; i.e. it has not been created; potentially being a fresh run, for, 
# for example, an object file needed for linking, which won't exist first run*.
# Now in our case, actually defining a file called 'all' doesn't change this
# behavior because the prerequisites are checked each run to see if, so target 
# 'all' needs to be updated against the prerequisites.
# Normally, this is used to issue the creation of the file, but in our case, it
# is instead used to convey the target 'all' should and will ALWAYS run when
# called, and semantically in this Makefile, we are essentially saying 'all'
# will never be a file in our best interest.
# This example declares a target called 'all', with the prerequisites 'one',
# 'two', and 'three'. Resolving these prerequsites means Make searches for
# the files in order: 'one', 'two', and 'three', checking if the files are up to
# date against their dependencies. If the targets are out of data against their
# dependencies (which includes the case that they don't exist even for empty
# dependencies, because their nonexistence means they are so out of date they
# don't even exist yet, and may have a creation proceduer), their rules are 
# executed to bring them up to date with their prerequisites.
# When the targets are satisfied, this means that the file whose name matches
# the target exists and is up to date compared to its prerequisites, and in 
# this case, prerequisite targets 'one', 'two', and 'three' do not have any
# prerequisites to check timestamp aganist, so their own existence is enough to 
# validate that they are up to date, satisfying the rule, satisfying the
# prerequisite for all
all: one two three

one:
	touch one

two:
	touch two

three:
	touch three

# Again, we will never create a file called 'clean' or that will always be up
# to date
clean:
	rm -f one two three
