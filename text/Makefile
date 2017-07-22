# Configuration ###########################################
# FILE = file name without tex
# PDBFR = pdf browser
# BIBTEX = bibtex command
# LATEX = latex command to run
FILE=PhDThesis
PDFBR=qpdfview
BIBTEX=bibtex
LATEX=pdflatex -interaction=errorstopmode -shell-escape
EDITOR=texstudio

# Helping variables #######################################
# Find all SVG figures
DIA_TO_EPS := $(shell find ./chapters -name "*.dia" | sed 's/\.dia/\.eps/g' | xargs)
SVG_TO_EPS := $(shell find ./chapters -name "*.svg" | sed 's/\.svg/\.eps/g'| xargs)
PDF_FILES_TO_DELETE := $(shell find ./chapters -name "*-converted-to.pdf" | xargs)

# Makefile targets ########################################
all: pdf 
	make pdf

open: all
	$(PDFBR) $(FILE).pdf 1>/dev/null 2>/dev/null&

pdf: figures
	$(LATEX)  $(FILE).tex
	if [ -f $(FILE).aux ]; then \
		$(BIBTEX) $(FILE); \
		$(LATEX)  $(FILE).tex; \
		$(LATEX)  $(FILE).tex; \
	fi

texstudio:
	$(EDITOR) PhDThesis.txss 1>/dev/null 2>/dev/null&

clean:	
	#Clean main directory
	rm -rf *.lot *.ps *.log *.aux *.dvi *.nav *.out *.snm *.toc *.bbl *.blg *.lof *.acn *.ist *.loa
	#Remove all *.aux,log,dvi files
	find ./chapters/ -name '*.aux' -exec rm -f {} \;
	find ./chapters/ -name '*.dvi' -exec rm -f {} \;
	find ./chapters/ -name '*.log' -exec rm -f {} \;
	
mrproper: clean	
ifneq ($(strip $(PDF_FILES_TO_DELETE)),)
	rm $(PDF_FILES_TO_DELETE)
endif
ifneq ($(strip $(SVG_TO_EPS)),)
	rm $(SVG_TO_EPS)
endif
ifneq ($(strip $(DIA_TO_EPS)),)
	rm $(DIA_TO_EPS)
endif
	rm $(FILE).pdf

figures: $(SVG_TO_EPS) $(DIA_TO_EPS) 
	@echo "All figures are converted"

chapters/pic/%.eps: chapters/pic/%.dia
	dia -t eps -e $@ $< 	

chapters/pic/%.eps: chapters/pic/%.svg
	inkscape -D -E $@ $<
