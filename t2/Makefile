# http://stackoverflow.com/questions/15348497/gnu-make-generate-rules-for-extracting-tarballs

ZIPFILES = $(wildcard *.zip)

EXTRACT_TARGETS := $(addprefix .extract_,$(ZIPFILES))
CLEAN_TARGETS := $(addprefix .clean_,$(ZIPFILES))

default: $(EXTRACT_TARGETS)

clean: $(CLEAN_TARGETS)

$(CLEAN_TARGETS): .clean_%: .extract_%
	rm -rf "$(shell 7z x $(patsubst .extract_%,%,$<) | head -1)"
	rm -f $<

$(EXTRACT_TARGETS): .extract_%: %
	7z x $< >/dev/null

.PHONY: default clean $(CLEAN_TARGETS)
