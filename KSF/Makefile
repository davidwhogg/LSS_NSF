LATEX       = pdflatex
BASH        = bash -c
ECHO        = echo
RM          = rm -rf
TMP_SUFFS   = pdf aux bbl blg log dvi ps eps out
CHECK_RERUN = grep Rerun $*.log

all: summary.pdf description.pdf data.pdf facilities.pdf biosketch_hogg.pdf

description.bbl: description.bib description.tex
	${LATEX} description
	bibtex description

description.pdf: description.tex hogg_nsf.tex description.bbl

%.pdf: %.tex hogg_nsf.tex
	${LATEX} $<
	( ${CHECK_RERUN} && ${LATEX} $< ) || echo "Done."
	( ${CHECK_RERUN} && ${LATEX} $< ) || echo "Done."

clean:
	${RM} $(foreach suff, ${TMP_SUFFS}, ${NAME}.${suff})
