# Pattern rules are the non-directly called variant of static pattern rules; 
# aka implicit pattern rules. We've already used them, but they were only 
# lightly covered. This is a more in depth example of them.
output_files := main
obj_files    := main.o utils.o
src_files    := main.c utils.c

.PHONY: all clean

all: $(output_files)

$(output_files): $(obj_files)
	$(CC) $^ -o $@

%.o: %.c
	$(CC) -c $^ -o $@

clean:
	rm -f $(obj_files) $(output_files)
