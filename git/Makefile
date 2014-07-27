OS = ubuntu\:12.04 ubuntu\:12.10 ubuntu\:13.04 ubuntu\:13.10 ubuntu\:14.04
Ubuntu-dir = .ubuntu-template

.PHONY: all clean

all: clean $(OS)

clean:
	rm -rf $(OS)

ubuntu%:
	./compile $@ $(@:ubuntu\:%=ubuntu-git\:%) $(Ubuntu-dir)
