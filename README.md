This repository holds my reference file for generating Microsoft Word `.docx` files from [pandoc markdown](http://johnmacfarlane.net/pandoc/demo/example9/pandocs-markdown.html). 
This repo currently contains the plain text version of John MacFarlane's pandoc README as well as a `.docx` version created using my reference file.
It also contains a `.md` file with some sample text from an academic paper of mine along with its converted `.docx` file. 
Finally, it contains the actual `reference.docx` file used by pandoc in the conversion from markdown. 

If I were in this directory, I would use this pandoc command to convert the pandoc README into a `.docx` file using my template:

`pandoc -S -s --reference-docx=reference.docx pandoc_readme.txt -o pandoc_readme.docx`

The `.docx` template uses [Hoefler Text](http://www.typography.com/fonts/hoefler-text/overview/) as its font. It is double spaced, with small caps headers and 1" indented, single-line block quotes. It works well for academic papers.
