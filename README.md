
# Merging PDFs based on a key with PyPDF2

This Python script uses the PyPDF2 library to merge multiple PDF files into one PDF based on a key that is extracted from their filename. For example, if you have several PDF files named 001-report.pdf, 001-summary.pdf, 002-report.pdf, 002-summary.pdf, etc., you can use the first three characters as the key (001, 002, etc.) and merge all files with the same key into a single PDF file.
## Requirements

- Python 3.x
- PyPDF2 library (can be installed with pip install PyPDF2)


## Usage

- Download the script and save it as merge_pdfs.py.
- Edit the pdf_input and pdf_output variables at the top of the script to match your input and output directories.
- Run the script with python merge_pdfs.py.
- Check the output directory for the merged PDF files.



## Code

Import necessary libraries
```
from PyPDF2 import PdfMerger
from pathlib import Path
from glob import glob
```
Define input and output directories:
```
pdf_input = ""
pdf_output = ""
```

List all pdf files in the input directory

```
pdf_files = glob(f"{pdf_input}*.pdf")
```

Use the first 3 characters as the 'key'
```
keys = []
for pdf in pdf_files:
    keys.append(pdf[0:3])
```
Note: set() is used to remove any duplicates in the 'key' list.
```
keys = set(key)
```
Loop through the unique keys and merge all PDF files with that key:
```
for key in keys: 
    merger = PdfMerger()
    for pdf in pdf_files:
        if pdf.startswith(key):
            merger.append(pdf)
    merger.write(f"{pdf_output}/{key}.pdf")
    merger.close()
```

## Explanation
The script starts by importing the necessary libraries: PdfMerger from PyPDF2, Path from pathlib, and glob from glob. PdfMerger is used to merge PDF files, Path is used to manipulate file paths, and glob is used to find PDF files in a directory.

Next, the input and output directories are defined as empty strings. You should replace these with the actual directories you want to use.

Then, all PDF files in the input directory are listed using glob and stored in the pdf_files variable.

After that, the script extracts the keys from the filenames by taking the first three characters of each filename and storing them in a list called keys. The set() function is used to remove any duplicates in the keys list.

Finally, the script loops through the unique keys and merges all PDF files with the same key using PdfMerger. The merged PDF file is saved in the output directory with the key as the filename.

## Limitations
This script assumes that all PDF files in the input directory have filenames that start with the same three characters for each key. If your filenames have a different format, you will need to modify the script accordingly.

## Conclusion
This Python script provides a simple way to merge multiple PDF files into one PDF based on a key. You can use it to merge reports, summaries, invoices, or any other PDF files that have a common identifier in their filenames.
