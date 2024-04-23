all: uprolog

export PATH := /usr/local/pub/mtf/plc/bin:$(PATH)

#
# Choose SML compiler
#
SMLC			:=
ifeq ($(SMLC),)
ifeq (mosmlc, $(shell PATH=$(PATH) command -v mosmlc > /dev/null 2>&1 && echo mosmlc))
SMLC := mosmlc
else ifeq (mlton, $(shell PATH=$(PATH) command -v mlton > /dev/null 2>&1 && echo mlton))
SMLC := mlton
else
$(error "No SML compiler found.")
endif
endif

ifeq ($(SMLC),mosmlc)
SMLCFLAGS := -o
endif
ifeq ($(SMLC),mlton)
SMLCFLAGS := -output
endif

uprolog: uprolog.sml
	$(SMLC) $(SMLCFLAGS) uprolog uprolog.sml

.PHONY: clean
clean:
	rm -rf *.ui *.uo uprolog
