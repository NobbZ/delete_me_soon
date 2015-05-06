SASSFOLDER = sass
CSSFOLDER  = stylesheets
DISTFOLDER = distribute

SCSSFILES  = $(wildcard $(SASSFOLDER)/*.scss)
CSSFILES   = $(SCSSFILES:$(SASSFOLDER)/%.scss=$(CSSFOLDER)/%.css)
HTMLFILES  = $(wildcard *.html)
DISTFILES  = $(CSSFILES:%=$(DISTFOLDER)/%) $(HTMLFILES:%=$(DISTFOLDER)/%)

all: $(CSSFILES)

clean:
	compass clean
.PHONY: clean

rebuild: clean all
.PHONY: rebuild

dist: $(DISTFOLDER) $(DISTFILES)

dist-clean: clean
	rm -rf $(DISTFOLDER)
.PHONY: dist-clean

dist-rebuild: dist-clean dist
.PHONY: dist-rebuild

$(CSSFOLDER)/%.css: $(SASSFOLDER)/%.scss
	compass compile

$(DISTFOLDER):
	mkdir -p $(DISTFOLDER)/$(CSSFOLDER)

$(DISTFOLDER)/%: %
	cp $< $@