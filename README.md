## A workaround for using the latex xr package on arXiv.

Based on the answer from this post: https://tex.stackexchange.com/questions/399065/arxiv-post-supplementary-files-using-external-document-and-xr

### Problem:  
When file SI.tex refers equations/pictures from file MAIN.tex.  
Get this message "Warning: No file MAIN.aux LABELS NOT IMPORTED" when processing files on arXiv.   
The compile will succeed, but the references in the other file are missing.


### Solution:

[1] Follow the set-up on Overleaf: https://www.overleaf.com/learn/how-to/Cross_referencing_with_the_xr_package_in_Overleaf. 

[2] Exporting files from Overleaf in arXiv format.

[3] Compile MAIN.tex on local computer, generating MAIN.aux.

[3] Create a new file xr.tex with the following content:  
\begin{filecontents}{MAIN.aux}  
The content of MAIN.aux  
\end{filecontents}

[4] In MAIN.tex  
Add on top: \usepackage{filecontents}  
Add before the end: \makeatletter\@input{xr.tex}\makeatother

[5] Zip and submit the whole folder to arXiv. 

Then, MAIN.aux will be generated during processing, and it should work now!
