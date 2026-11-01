# 'filter' is a function that can be applied to a list to only select based on
# a matching qualifier. This makes it so that the right 'target's are selected
# given a rule. This example uses a list called 'obj_files' that is filtered 
# against '%.o' files and '%.raw' files, with '%.o' files depending on '%.c' 
# files and '%.result' files depending on '%.raw'
obj_files := foo.result bar.o lose.o
src_files := foo.raw bar.c lose.c

# Without specifying .PHONY, because Make auto attempts to compile C and C++ 
# source code, we'll end up with an attempt to compile 'all' because its 
# prerequisites are '*.o' files
.PHONY: all clean

all: $(obj_files)

$(filter %.o, $(obj_files)): %.o: %.c
	@echo "target: $@ prereq: $^"

$(filter %.result, $(obj_files)): %.result: %.raw
	@echo "target: $@ prereq: $^"

%.c %.raw:
	touch $@

clean:
	rm -f $(src_files)

