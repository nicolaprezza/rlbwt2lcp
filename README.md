# RLBWT2LCP

### Overview

Input: path of a file containing the (extended) BWT of a collection of strings. Alphabet: {A,C,G,T,N,#}. The default terminator is #, but it can be changed with option -t. If the file does not contain "N", the algorithm is faster and uses slightly less RAM.

Output: a file containing r pairs of 64-bits integers (i,LCP[i]), where r is the number of equal-letter runs in the input BWT and i is a position such that LCP[i] is a minimum in an interval [L,R+1] such that BWT[L,R] is an equal-letter run. If there are multiple minima in a run, we store only one (arbitrarily). Pairs (i,LCP[i]) are stored by increasing i. 

Based on an extension (to BWTs of collections) of the suffix-tree navigation algorithm described in  the paper "


*Nicola Prezza and Giovanna Rosone, 2019. Space-Efficient Computation of the LCP Array from the Burrows-Wheeler Transform. Proceedings of the 30th Annual Symposium on Combinatorial Pattern Matching (CPM).*

*Nicola Prezza and Giovanna Rosone, 2019. "Space-Efficient Construction of Compressed Suffix Trees." arXiv preprint arXiv:1908.04686*

*Djamal Belazzougui, 2014. Linear time construction of compressed text indices in compact space. STOC*

### RAM usage

Let r be the number of BWT runs. When "N"s are not present (alphabet = A,C,G,T,#) the tool uses **n"*"5.25 + r"*"128 bits** of RAM. If "N"s are present, the tool uses **n*5.65 + r*128 bits** of RAM.

### Running time

O(n), where n is the total collection(s) size. 

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







