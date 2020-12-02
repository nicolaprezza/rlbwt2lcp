# RLBWT2LCP

### Overview

Input: path of a file containing the (extended) BWT of a collection of strings, in plain text. Be careful to not include a newline at the end of the file. Alphabet: {A,C,G,T,N,#}. The default terminator is #, but it can be changed with option -t. If the file does not contain "N" characters, the algorithm is faster and uses slightly less RAM.

Output: a file containing r pairs of integers (i,LCP[i]), where r is the number of equal-letter runs in the input BWT and i is a position such that LCP[i] is a minimum in an interval [L,R+1] such that BWT[L,R] is an equal-letter run.  If there are multiple minima in [L,R+1], we store only one (arbitrarily). Pairs (i,LCP[i]) are stored by increasing run number. Integer i is stored using 64 bits. Integer LCP[i] is stored using B*8 bits (B Bytes), where B = 8 by default and can be changed using option -l.

Based on the publications:

*Nicola Prezza and Giovanna Rosone, 2019. Space-Efficient Computation of the LCP Array from the Burrows-Wheeler Transform. Proceedings of the 30th Annual Symposium on Combinatorial Pattern Matching (CPM).*

*Nicola Prezza and Giovanna Rosone, Space-efficient construction of compressed suffix trees. Theoretical Computer Science. Available online 19 November 2020. In Press, Journal Pre-proof, ISSN 0304-3975, https://doi.org/10.1016/j.tcs.2020.11.024. 
ArXiv preprint arXiv:1908.04686*

*Djamal Belazzougui, 2014. Linear time construction of compressed text indices in compact space. STOC*

### RAM usage

Let r be the number of BWT runs and B the number of bytes used to represent LCP values (option -l). When "N"s are not present (alphabet = A,C,G,T,#) the tool uses **5.25 n + (64+8B) r bits** of RAM. If "N"s are present, the tool uses **5.65 n + (64+8B) r bits** of RAM.

### Running time

O(n), where n is the total collection size. 

### Funding

Supported by the project Italian MIUR-SIR CMACBioSeq ("Combinatorial methods for analysis and compression of biological sequences") grant n.~RBSI146R5L, PI: Giovanna Rosone. Link: http://pages.di.unipi.it/rosone/CMACBioSeq.html

### Install

First, install SDSL on your system (https://github.com/simongog/sdsl-lite). Then:

~~~~
git clone https://github.com/nicolaprezza/rlbwt2lcp
cd rlbwt2lcp
mkdir build
cd build
cmake ..
make
~~~~







