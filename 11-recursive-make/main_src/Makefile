# Quick Makefile that will not be called on its own, but rather through a 
# recursive Make call
.PHONY: clean

main.o: main.c
	$(CC) -c $< -o $@

main.c:
	@echo "int main() { return 0; }" > $@

clean: 
	rm -f main.o
	
