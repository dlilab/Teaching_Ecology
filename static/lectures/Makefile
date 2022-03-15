ALL: 01_whatIsEcology/notes.pdf 01_whatIsEcology/notes.html 01_whatIsEcology/presentation.html \
		 01_whatIsEcology/Rcode.pdf 01_whatIsEcology/Rcode.html 02_lifeEnviron/presentation.html \
		 03_popDynamics/notes.pdf 03_popDynamics/notes.html 03_popDynamics/Rcode.html 03_popDynamics/presentation.html \
		 04_behavior/notes.pdf 04_behavior/notes.html 04_behavior/Rcode.html 04_behavior/presentation.html \
		 05_metapopulation/notes.pdf 05_metapopulation/notes.html 05_metapopulation/presentation.html \
		 06_niche/notes.pdf 06_niche/notes.html 06_niche/presentation.html \
		 07_trophicInteractions/notes.pdf 07_trophicInteractions/notes.html 07_trophicInteractions/presentation.html \
		 08_diseaseEcology/notes.pdf 08_diseaseEcology/notes.html 08_diseaseEcology/presentation.html \
		 09_communityEcology/notes.pdf 09_communityEcology/notes.html 09_communityEcology/presentation.html \
		 10_networks/notes.pdf 10_networks/notes.html 10_networks/presentation.html \
		 11_landscapeEcology/notes.pdf 11_landscapeEcology/notes.html 11_landscapeEcology/presentation.html \
		 12_envChange/notes.pdf 12_envChange/notes.html 12_envChange/presentation.html \
		 13_macroecology/notes.pdf 13_macroecology/notes.html 13_macroecology/presentation.html

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
	if [[ $< == *notes* ]]; then Rscript -e 'rmarkdown::render("$<", output_format = "tufte::tufte_html")'; fi
	if [[ $< == *Rcode* || $< == *presentation* ]]; then Rscript -e 'rmarkdown::render("$<")'; fi
	$(view) $@
			
clean:
	rm -fv */*.aux */*.log */*.toc */*.blg */*.bbl */*.synctex.gz
	rm -fv */*.nav */*.aux */*.snm 
	rm -fv */*.out */*.bcf */*blx.bib */*.run.xml
	rm -fv */*.fdb_latexmk */*.fls
