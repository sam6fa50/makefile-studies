# This is a bad example of the good version, in which our Makefile actually
# doesn't utilize the 'filter' function in order to filter through our supplied
# list. In this case, the Make doesn't even successfully run, because what 
# happens instead is that our two and only rules that deals with all 'obj_files'
# are actually not syntactically correct; we can't do this. We can't have 
# multiple rules with the same 'target' unless we use double colon '::' in order
# to specify that the 'target' has multiple rules associated with it as the
# 'target'. So, we end up with all of our list going into one static pattern
# match, which doesn't support all the input files. Thus, we end up with an
# incorrect Makefile that doesn't even run. The 'filter' function explicitly
# produces unique 'target' lists that match a particular 'stem', which lets us
# have unique rules scoped using the 'filter' function. So it is not redundant,
# it is needed to split a large collection of files grouped under the same list
# into homogenous groups that can be statically matched against what makes them
# homogenous; their common 'stem'; homogenous 'target's.
obj_files := foo.result bar.o lose.o
src_files := foo.raw bar.c lose.c

.PHONY: all clean

all: $(obj_files)

$(obj_files): %.o: %.c
	echo "target: $@ prereq: $^"

$(obj_files): %.result: %.raw
	echo "target: $@ prereq: $^"

%.c %.raw:
	touch $@

clean:
	rm -f $(src_files)
