# Rendering .qmd to pdf
## Why quarto?
Quarto is a markdown extension based on - and retrocompatible with - RMarkdown and Pandoc.
With Quarto we can format our documents with the following languages:
- Markdown
- RMarkdown
- LaTex
- Quarto
- Pandoc
- HTML

This means we can switch between any of those - preferably in the order described above - when writing our documents. As such we'll be able to benefit from the conciseness of Markdown and, when necessary, use LaTex or HTML for more complex stuff (without bothering with wysiswg text editors => easier pull requests!).
Since the majority of our documents will be written in Markdown, It will also be directly rendered by GitHub, which is a nice feature.

## Installation
### Debian
```bash
sudo apt update
sudo apt install texlive-latex-full
sudo apt install texlive-xetex
sudo apt install pandoc
wget https://github.com/quarto-dev/quarto-cli/releases/download/v1.1.251/quarto-1.1.251-linux-amd64.deb
sudo dpkg -i quarto-1.1.251-linux-amd64.deb
quarto install tool chromium
```

### Windows
[MikTex Installer](https://miktex.org/download)  
[Pandoc Installer](https://pandoc.org/installing.html)  
[Quarto Installer](https://quarto.org/docs/get-started/)  
On Windows you must add `tex`, `pandoc`, `quarto` to the environment path  

### Suggested VSCode extensions
- https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one
- https://marketplace.visualstudio.com/items?itemName=quarto.quarto
- https://marketplace.visualstudio.com/items?itemName=tomoki1207.pdf
- https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop

## Quick Cheatsheet

```bash
quarto render my-pretty-file.qmd
```
[MarkDown](https://www.markdownguide.org/basic-syntax)  
[Quarto](https://quarto.org/docs/authoring/figures.html)

#### Underlined text
```rmd
Cannot find a way
```
#### Unnumbered Sections
```rmd
{-}
{.unnumbered}
{.unlisted}
{.unlisted .unnumbered}
```
#### Wrapped Figures
```latex
\begin{wrapfigure}{r}{2cm}
\includegraphics{./my-image.jpeg}
\end{wrapfigure}
```
#### Figures' Attributes
```rmd
fig-pos=(!, H, h, t, b, p)
fig-env=(figure, mdframed, wrapfigure, ...)
width=(%, cm, ...)
height=(%, cm, ...)
scale=(%)
fig-cap-location=(top, bottom, margin)
```

#### Footnotes
```rmd
poorly explained phrase[^1]

[^1]: some footnote

```

#### Layout
```rmd
:::{layout-ncol=1}

This goes in the first column

And this goes in the second column

:::
```

## Custom Scripts Usage

### Grammar checking (alias checkdoc)
```bash
split -b 20000 documento*.qmd &&\
for f in xa*; do gramma check -m true "$f" && rm "$f"; done;
```

### exporting
There is a custom exporting script for each deliverable; to call them all use:
```bash
chmod 777 export_all.bash;
./export_all.bash;
```

### rendering
This script simply calls `quarto render` on each deliverable and then opens them.
```bash
chmod 777 render_all.bash;
./render_all.bash;
```

### opening
This script simply opens all deliverables (pdfs).
```bash
chmod 777 open_alll.bash;
./open_all.bash
```