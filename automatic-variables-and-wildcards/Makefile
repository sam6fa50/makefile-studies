# A deeper exploratory on 'automatic variables' and 'wildcards', which are used
# to match in different ways
# '*' wildcard searches the filesystem for matching filenames, should wrap in
# 'wildcard' function to prevent two situations:
# 1.) '*' does not work with variable names, i.e.
x_wrong := *.o # not valid
x_right := $(wildcard *.o) # is valid

# 2.) '*' does not sustain the wildcard status if it does not match anything,
# and instead gets demoted to a strict string to compare against, i.e.
# Fails because $(x_wrong) is "*.o", which means it 
# matches against that string; same as 'two' but behavior more 
# explicitly explained below
one: $(x_wrong) 

# Fails because "*.o" starts off as a wildcard, but gets
# demoted if nothing matches to it, e.g. if there's "blah.o", it sets
# that as the prerequisite, but if there isn't any files ending in ".o"
# it just searches for filenames literally called "*.o", which is 
# extermely undeterministic
two: *.o 

# Works as expected! Always matches because x_right
# used the 'wildcard' function meaning it will ALWAYS attempt to match,
# and will never demote to a plain string
three: $(x_right) 

# Works, same as above
four: $(wildcard *.o)


