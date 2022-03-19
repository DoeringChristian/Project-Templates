BUILDDIR = build
SRCDIR = src
ASSETSDIR = assets
FILENAME = index

download-cls:
	mkdir "${ASSETSDIR}" -p
	wget -O "${ASSETSDIR}/citation-style.csl" \
		"https://raw.githubusercontent.com/citation-style-language/styles/master/harvard-anglia-ruskin-university.csl"

pdf:
	mkdir "${BUILDDIR}" -p
	@echo "Creating pdf output"
	pandoc "${SRCDIR}/${FILENAME}.md" \
		--resource-path="${SRCDIR}" \
		--citeproc \
		--csl="${ASSETSDIR}/citation-style.csl" \
		--from="markdown+tex_math_single_backslash+tex_math_dollars" \
		--to="latex" \
		--toc \
		--output="${BUILDDIR}/output.pdf" \
		--pdf-engine="xelatex"

html:
	mkdir "${BUILDDIR}" -p
	echo "Creating html output"
	pandoc "${SRCDIR}/${FILENAME}.md" \
		--resource-path="${SRCDIR}" \
		--citeproc \
		--csl="${ASSETSDIR}/citation-style.csl"\
		--from="markdown+tex_math_single_backslash+tex_math_dollars" \
		--to="html5" \
		--toc \
		--output="${BUILDDIR}/output.html" \
		--self-contained

all: pdf html
