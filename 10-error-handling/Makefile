# This is a sample Makefile that shows how error suppression looks like in make
# using the '-k' and '-i' arguments as well as the '-' 'command' prefix
# First is the '-' 'command' prefix because we are going to delibrately ignore
# all errors in the process of making 'dashprefix'. This ignores the error and 
# continues the dependency tree traversal upwards back rather than stopping at
# the first failing step
.PHONY: all
all: dashprefix kiprefix

dashprefix: dashprefix.o
	-$(CC) $^ -o $@

dashprefix.o: dashprefix.c
	-$(CC) -c $< -o $@

# The next thing we're covering is supplying '-k' and '-i' as arguments into
# Make when running it to see how the following behaves. '-k' attempts to keep
# going in the face of errors, BUT this attempt expects that 'prerequisite's 
# are satisfied in the intermediary. If that does not happen, we end up failing
# because we can't go on with a failed 'prerequisite'. However, '-i' just keeps
# going even when the 'prerequisite's are failed. So for retaining the build
# failure propagation, '-k' really helps as it will consume all 'target's called
# by the main target, so it will take all dependency paths and fail the paths
# at their first 'prerequisite' failure, but it won't terminate the process, so
# it will keep going across all the different dependency chains whilst 
# preserving their exact failure by dropping out of the dependency chain on 
# first 'prerequsite' failure, meaning you can end up with one path that fully
# works alongside several paths that fail somewhere, really good for debugging
# complex systems. For simply observing the entire Makefile, '-i' can be used,
# but it doesn't carry build propagation errors so it will have output that is
# more cumbersome to sift through than actually usable/needed
kiprefix: kiprefix.o
	$(CC) $^ -o $@

kiprefix.o: kiprefix.c
	$(CC) -c $< -o $@

# We don't have a target that makes 'dashprefix.c', so we're going to end up 
# with a build error because we are not manually creating 'dashprefix.c'. Same
# with our 'kiprefix.c'
%.c:
	@echo "Nothing here!"
