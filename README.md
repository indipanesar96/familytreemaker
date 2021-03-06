familytreemaker
===============

This program creates family tree graphs from simple text files.

The input file format is very simple, you describe persons of your family line
by line, children just have to follow parents in the file. Persons can be
repeated as long as they keep the same name or id. An example is given in the
file `LouisXIVfamily.txt`.

Note: This branch version is optimized for chinese. If other language for 
      input text file is used, command option gender (-g) has to be used to
      specify words of male and female, since their default values are set
      as "男" and "女" instead of origin "M" and "F".  


Installation
------------

Simply clone the repo or install package familytree by pip as shown below:
```bash
pip install familytree
```

This script outputs a graph descriptor in DOT format. To make the image
containing the graph, you will need a graph drawer such as [GraphViz] [1].

[1]: http://www.graphviz.org/  "GraphViz"

Usage
-----
```
usage: familytreemaker.py [-h] [-a ANCESTOR] [-g GENDER] [-v INFOLEVEL]
                          [-o OUTFILE]
                          INPUTFILE

Generates a family tree graph from a simple text file

positional arguments:
  INPUTFILE     the formatted text file representing the family

optional arguments:
  -h, --help    show this help message and exit
  -a ANCESTOR   make the family tree from an ancestor (if omitted, the program
                will try to find an ancestor)
  -g GENDER     customized gender string, for example: "男,女" or "M,F"
  -v INFOLEVEL  Information level (0/1/2) to output. (0 - only name and
                surfname will be output; 1 - time of birthday and deathday
                will be invisable; 2 - all information will be output)
  -o OUTFILE    file name for output
```

The sample family descriptor `LouisXIVfamily.txt` is here to show you the
usage. Simply run:
```
python familytreemaker.py -a "王灿文" -v2 -o LouisXIVfamily.dot LouisXIVfamily.txt && \
    dot -Tsvg -o LouisXIVfamily.svg LouisXIVfamily.dot
```

If package familytree has been installed by pip, commands below can be performed to populate:
```bash
python -m familytree.familytreemaker -a "王灿文" -v2 -o LouisXIVfamily.dot LouisXIVfamily1.txt && \
    dot -Tsvg -o LouisXIVfamily.svg LouisXIVfamily.dot
``` 

It will generate the tree from the infos in `LouisXIVfamily.txt`, starting from
*王灿文* and saving the image in `LouisXIVfamily.svg`.

![result: LouisXIVfamily.svg](./LouisXIVfamily.svg)