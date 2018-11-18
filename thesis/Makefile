TARGET = thesis

all: ${TARGET}.pdf

${TARGET}.pdf2: ${SOURCES}
	( \
	pdflatex $(TARGET).tex; \
	while grep -q "Rerun to get cross-references right." $(<:.tex=.log); \
	do \
		pdflatex $(TARGET).tex; \
	done \
	)

${TARGET}.pdf: ${SOURCES} ${TARGET}.bbl
	( \
	latex $(TARGET).tex; \
	while grep -q "Rerun to get cross-references right." $(<:.tex=.log); \
	do \
		latex $(TARGET).tex; \
	done \
	)
	dvipdf ${TARGET}.dvi;


${TARGET}.bbl: references.bib bibliography.bib
	latex ${TARGET}.tex; \
	bibtex ${TARGET}; \
	latex ${TARGET}.tex; \
	latex ${TARGET}.tex;

.PHONY: clean
clean:
	rm -f \
	*.aux \
	${TARGET}.log \
	${TARGET}.out \
	${TARGET}.dvi \
	${TARGET}.pdf \
	${TARGET}.thm \
	${TARGET}.bbl \
	${TARGET}.blg \
	${TARGET}.lof \
	${TARGET}.lot \
	${TARGET}.toc \
	${TARGET}.ps

