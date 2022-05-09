BUILDDIR = build
SRCDIR = src
ASSETSDIR = assets
SRCFILES = $(wildcard ${SRCDIR}/*.md) $(wildcard ${SRCDIR}/*.yaml)

download-cls:
	mkdir ${ASSETSDIR} -p
	wget -O "${ASSETSDIR}/citation-style.csl" \
		"https://raw.githubusercontent.com/citation-style-language/styles/master/harvard-anglia-ruskin-university.csl"

pdf:
	mkdir "${BUILDDIR}" -p
	@echo "Creating pdf output"
	pandoc ${SRCFILES} \
		--resource-path="${SRCDIR}" \
		--csl="${ASSETSDIR}/citation-style.csl" \
		--from="markdown+raw_tex+tex_math_single_backslash+tex_math_dollars" \
		--to="latex" \
		--toc \
		--output="${BUILDDIR}/output.pdf" \
		--pdf-engine="xelatex" \
		-F pandoc-acro \
		-F pandoc-crossref \
		--citeproc 

html:
	mkdir "${BUILDDIR}" -p
	echo "Creating html output"
	pandoc ${SRCFILES} \
		--resource-path="${SRCDIR}" \
		--csl="${ASSETSDIR}/citation-style.csl"\
		--from="markdown+raw_tex+tex_math_single_backslash+tex_math_dollars" \
		--to="html5" \
		--output="${BUILDDIR}/output.html" \
		--self-contained \
		-F pandoc-acro \
		-F pandoc-crossref \
		--citeproc 

all: pdf html
