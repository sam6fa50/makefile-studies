# This lesson is particularly important as it shows the relation between shell
# envrionment, variables, child processes at large, and the general concept of a
# process environment.
# Firstly, let's look at processes and process environments:
# Processes are any instances of programs that are actively running on your 
# system and have a PID attached to them.
# All processes on UNIX, and by extension, most *NIX systems are programs that
# have been initialized and contain a 'process image', which is the actual
# chunk of memory a process takes that represents its state (as much possible
# in RAM). Note, this memory is in a virtual memory space allocated by the 
# kernel, so it goes much deeper. Process environments are key-value tables of
# essentially what can be seen as variables that the process can access 
# globally. 
# Shell environments are a specific instance of process environments. In a 
# shell, we can add shell environment variables by calling 'export', which adds
# a new key-value pair to the process environment table.
# These are NOT shell variables, which are declared using 'a=5;' for example, 
# as we are not exporting to the environment. Now, the thing about a process'
# environment is that all child processes inherit its parents' environment into
# a unique environment table that it can then modify for its own usage and
# further propagate to child processes. 
# So what happens when we run Make? each 'command' executes as its own shell,
# meaning Make creates a new shell from the shell it was initially called in,
# per 'command'. Which means all 'command's get access to the orignial shell
# environment. 
# Make itself is a process, meaning when called, it absorbs the calling shell's
# environment variables, which can be utilized across all recursive instances of
# Make. Equally importantly, the process can declare environment variables in
# itself, saturating its process environment with more key-value pairs that 
# will ALSO propagate down to child processes.
# Long story short, 'export'ed variables in Make will leave the parent shell's
# environment unimpacted, but will introduce process environment variables in
# the running Make process which will propagate to all children, allowing us to
# preserve data throughout all recursive Make calls

