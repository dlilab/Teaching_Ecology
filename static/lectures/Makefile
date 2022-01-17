ALL: 01_whatIsEcology/notes.pdf 01_whatIsEcology/notes.html 01_whatIsEcology/presentation.html \
		 01_whatIsEcology/Rcode.pdf 01_whatIsEcology/Rcode.html 02_lifeEnviron/presentation.html

OStype := $(shell uname -s)

ifeq ($(OStype), Linux)
	   view = evince
endif

ifeq ($(OStype), Darwin)
	   view = open
endif

%.pdf: %.Rmd
	Rscript -e 'rmarkdown::render("$<", output_format = "bookdown::pdf_document2")'
	$(view) $@

%.html: %.Rmd
	Rscript -e 'rmarkdown::render("$<")'
	$(view) $@
			
clean:
	rm -fv */*.aux */*.log */*.toc */*.blg */*.bbl */*.synctex.gz
	rm -fv */*.nav */*.aux */*.snm 
	rm -fv */*.out */*.bcf */*blx.bib */*.run.xml
	rm -fv */*.fdb_latexmk */*.fls
