if FVWM_BUILD_GOLANG
GOCMD=go
GOBUILD=$(GOCMD) build
GOCLEAN=$(GOCMD) clean
BINARY_NAME=FvwmPrompt

moduledir=@FVWM_MODULEDIR@

bin_SCRIPTS=FvwmCommand

FvwmCommand: ../../config.h Makefile
	echo "#!/bin/sh" > $@
	echo exec ${bindir}'/FvwmPrompt $$@' >> $@

CLEANFILES=$(bin_SCRIPTS)

all: build
build:
	$(GOBUILD) -o $(BINARY_NAME) -v
clean:
	$(GOCLEAN)
	rm -f $(BINARY_NAME)
	rm -f $(BINARY_UNIX)
	rm -f $(bin_SCRIPTS)

run:
	$(GOBUILD) -o $(BINARY_NAME) -v ./...
	./$(BINARY_NAME)

# If a previuos installation was made with !FVWM_BUILD_GOLANG,
# we don't want FvwmConsole, so remove it.
install:
	rm -f $(DESTDIR)$(moduledir)/FvwmConsole
	rm -f $(DESTDIR)$(moduledir)/FvwmConsoleC
	rm -f $(DESTDIR)$(moduledir)/FvwmConsoleC.pl
	rm -f $(DESTDIR)$(bindir)/$(BINARY_NAME)
	rm -f $(DESTDIR)$(bindir)/$(bin_SCRIPTS)
	install $(BINARY_NAME) $(DESTDIR)$(bindir)
	install $(bin_SCRIPTS) $(DESTDIR)$(bindir)

uninstall:
	rm -f $(DESTDIR)$(bindir)/$(BINARY_NAME)
	rm -f $(DESTDIR)$(bindir)/$(bin_SCRIPTS)
endif
