
Partial derivative:
\newcommand{\pd}[2]{\frac{\partial{#1}}{\partial{#2}}}


To convert from ipynb to pdf:
```bash
jupyter nbconvert --execute --to pdf Sp24-ECE146-HW2.ipynb
```
To merge:
```bash
gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -sOutputFile=merged.pdf source1.pdf
```
HTML to pdf:
pandoc input.html -o output.pdf