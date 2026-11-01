# Default target, and only one called with 'make' because of its
# default status by being in the beginning of the file
blah: blah.o
	# Linking step
	cc $^ -o $@

blah.o: blah.c
	# Compile only
	cc -c $^ -o $@

blah.c:
	# If 'blah.c' is not found, not usual! Just for learning
	echo "int main() { return 0; }" > $@

# Clean target
clean:
	rm -f blah*
