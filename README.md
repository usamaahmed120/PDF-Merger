# PDF-Merger
## Merging PDFs based on a key with PyPDF2
### This Python script uses the PyPDF2 library to merge multiple PDF files into one PDF based on a key that is extracted from their filename. For example, if you have several PDF files named 001-report.pdf, 001-summary.pdf, 002-report.pdf, 002-summary.pdf, etc., you can use the first three characters as the key (001, 002, etc.) and merge all files with the same key into a single PDF file.

Requirements
Python 3.x
PyPDF2 library (can be installed with pip install PyPDF2)
Usage
Download the script and save it as merge_pdfs.py.
Edit the pdf_input and pdf_output variables at the top of the script to match your input and output directories.
Run the script with python merge_pdfs.py.
Check the output directory for the merged PDF files.
