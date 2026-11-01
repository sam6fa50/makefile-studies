# Make actually defines for you, implicitly, some rules when it comes to 
# compiling C or C++ code. The following are examples of this behavior, but
# first, to actually invoke these we must define CC and CXX (C and CXX compilers
# respctively):
CC := gcc # (default cc)
CFLAGS := -g # Debug info

# Can also set:
# CXX: C++ Compiler (default g++)
# CXXFLAGS: Extra flags to give to the C++ compiler
# CPPFLAGS: Extra flags to give to the C preprocessor (!! IMPORTANT CPP = C
# PRE PROCESSOR)
# LDFLAGS: Extra flags to give compilers when they're supposed to invoke the
# linker

# We don't have to make the rule for target 'blah.o', or the command body for 
# target 'blah'
# This target just exists to clarify that we want to produce 'blah' from 
# linking 'blah.o', but we don't explicitly define the rule to link 'blah' as
# that is implicitly defined by Make itself
blah: 

# This target just exists to clarify that we want to compile a 'blah.o' from 
# 'blah.c', but we don't explicitly define the rule to compile 'blah.o' as that
# is implicitly defined by Make itself

# Implicit rule #1: target 'blah.o' produced from prerequisite 'blah.c': 
	# $(CC) -c $(CPPFLAGS) $(CFLAGS) $^ -o $@

# Implicit rule #2: target 'blah' produced from prerequisite 'blah.o':
	# $(CC) $(LDFLAGS) $^ $(LOADLIBES) $(LDLIBS) -o $@

blah.c:
	echo "int main() { return 0; }" > $@

clean:
	rm -rf blah*
