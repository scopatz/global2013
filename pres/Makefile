notebook = scopatz_global2013
#nbcdir = ~/nbconvert

all:
	#cp -r $(nbcdir)/reveal . $<
	#rm -rf reveal/.git* $<
	#mkdir -p js $<
	#cp $(nbcdir)/js/mathjax-onload.js js
	ipython nbconvert --to slides $(notebook).ipynb $<
	cp classy.css reveal.js/css/theme/ $<
	sed -i 's:reveal.js/css/theme/simple.css:reveal.js/css/theme/classy.css:' $(notebook).slides.html $<
	sed -i 's:class="fragment" class="text_cell_render:class="fragment text_cell_render:' $(notebook).slides.html $<
	sed -i 's/.rendered_html ul{list-style:disc;margin:1em 2em;}/.rendered_html ul{list-style:disc;margin:0em 2em;}/' $(notebook).slides.html $<
	sed -i '/<\!-- Social buttons -->/,/<\!-- End of social buttons -->/d' $(notebook).slides.html $<
	#sed -i 's/background: #3F3F3F;/background: #4A363D;/' reveal.js/lib/css/zenburn.css $<

clean:
	rm -f *.pdf *.html *.zip

%.ps :%.eps
	convert $< $@

%.png :%.eps
	convert $< $@

zip:
	zip paper.zip *.html *.bib

.PHONY: all clean
