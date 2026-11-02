# Quick Makefile that will not be called on its own, but rather through a 
# recursive Make call
.PHONY: clean

utils.o: utils.c
	$(CC) -c $< -o $@

utils.c:
	@echo "int utils() { return 0; }" > $@

clean:
	rm -f utils.o
