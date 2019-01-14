# List any generated files here
TARGETS = swagger_gen.go
# List any source files used to generate the targets here
SOURCES = swagger.json
# List any directories that have their own Makefile here
SUBDIRS =

# Default target
all: generate $(SUBDIRS) $(TARGETS)

# Recurse into subdirs for same make goal
$(SUBDIRS):
	$(MAKE) -C $@ $(MAKECMDGOALS)

# Clean all targets recursively
clean: $(SUBDIRS)
	$(RM) $(TARGETS)

# Define go generate if not already defined
GO_GENERATE := go generate
# Define ui generation command if not already defined
GO_BINDATA := go run github.com/kevinburke/go-bindata/go-bindata

generate:
	$(GO_BINDATA) -o swagger_gen.go -tags assets -ignore go -nocompress -pkg server .

# Run go generate for the targets
$(TARGETS): $(SOURCES)
	$(GO_GENERATE) -x

.PHONY: all clean $(SUBDIRS)
