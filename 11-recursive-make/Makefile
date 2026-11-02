# We can recursively call Make using '$(MAKE)' which is a 'predefined variable'
# defined by Make itself that serves a dual purpose beyond being a variable: it
# also receives special interpretation by the Make process for the line it is
# in. Specifically, when $(MAKE) exists in a 'command' for a recipe, the Make
# interperter recognizes it and creates a new instance of Make in a shell that
# is not influenced by some potentially influential arguments passed into the 
# original Make process, eg. -n | --dry-run, -t | --touch, -q | --question, which
# print recipes without executing them, just marks targets as updated without 
# executing the recipes, and doesn't execute any recipes but reports whether 
# 'target's are out of date post execution through exit status, respectively.
# In these examples, no 'command's in the recipes are executed, and since a
# recursive call of Make is technically a command, a recursive call would not
# execute in these arguments passed into the original Make call. Thus, $(MAKE)
# comes to the rescue by being specially identified by the interpreter as a
# must execution regardless of any flags that may have inhibited execution at 
# all, which allows for recursive Make processes to actually take the same 
# flags and perform as expected by the original intent of making at the root 
# level with other Makefiles at the subdirectory level
main_folder_name := main_src
utils_folder_name := utils_src

main_directory := $(CURDIR)/$(main_folder_name)
utils_directory := $(CURDIR)/$(utils_folder_name)

.PHONY: all clean

all: main

main: $(main_directory)/main.o $(utils_directory)/utils.o
	$(CC) $? -o $@

# $(MAKE) -C is the idomatic means of creating a child Make process in a 
# different directory; a changed directory
$(main_directory)/main.o:
	$(MAKE) -C $(main_directory)

$(utils_directory)/utils.o:
	$(MAKE) -C $(utils_directory)

clean:
	$(MAKE) -C $(main_directory) clean
	$(MAKE) -C $(utils_directory) clean
	rm -f main
