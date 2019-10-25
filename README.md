familytreemaker
===============

This program creates family tree graphs from simple text files.

The input file format is very simple, you describe persons of your family line
by line, children just have to follow parents in the file. Persons can be
repeated as long as they keep the same name or id. An example is given in the
file `LouisXIVfamily.txt`.


Installation
------------

Simply clone the repo.

This script outputs a graph descriptor in DOT format. To make the image
containing the graph, you will need a graph drawer such as [GraphViz] [1].

[1]: http://www.graphviz.org/  "GraphViz"

Usage
-----
usage: familytreemaker.py [-h] [-a ANCESTOR] [-v INFOLEVEL] [-o OUTFILE]
                          INPUTFILE

Generates a family tree graph from a simple text file

positional arguments:
  INPUTFILE     the formatted text file representing the family

optional arguments:
  -h, --help    show this help message and exit
  -a ANCESTOR   make the family tree from an ancestor (if omitted, the program
                will try to find an ancestor)
  -v INFOLEVEL  Information level (0/1/2) to output. 
                0 - only name and surfname will be output; 
                1 - time of birthday and deathday will be invisable; 
                2 - all information will be output
  -o OUTFILE    file name for output


The sample family descriptor `LouisXIVfamily.txt` is here to show you the
usage. Simply run:
```
$ ./familytreemaker.py -a '王灿文' -v0 LouisXIVfamily.txt | dot -Tsvg -o LouisXIVfamily.svg
```
or
```
python familytreemaker.py -a "王灿文" -v2 -o LouisXIVfamily.dot LouisXIVfamily.txt && \
    dot -Tsvg -o LouisXIVfamily.svg LouisXIVfamily.dot
```

It will generate the tree from the infos in `LouisXIVfamily.txt`, starting from
*Louis XIV* and saving the image in `LouisXIVfamily.svg`.


You can see the result:

![result: LouisXIVfamily.svg](/LouisXIVfamily.svg)

