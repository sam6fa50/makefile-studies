# This is an exploratory for the common automatic variables
hey: one two
	@# Outputs target name
	@echo "Target name: $@"
	@# Outputs all prerequisites that are newer than the target
	@echo "ONLY the prerequisites that are newer than target: $?"
	@# Outputs all prerequisites
	@echo "ALL Prerequisites: $^" 
	@# Outputs the first prerequisite only
	@echo "First prerequisite only: $<" 
	touch hey

one:
	touch one

two:
	touch two

clean:
	rm -f hey one two
