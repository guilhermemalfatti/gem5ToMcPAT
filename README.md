# gem5ToMcPAT v0.1
An attempt to adapt [gem5](http://gem5.org/Main_Page) output to [McPAT](http://www.hpl.hp.com/research/mcpat/) input. This version is implemented in Bison, Flex and C/C++. It also uses the library [RapidXML](http://rapidxml.sourceforge.net/) for C++. Based on Fernando Endo's notes *[1]*, this parser extracts the parameters and statistics from the output of gem5, 'config.ini' and 'stats.txt', and fills the equivalent fields in a XML based on 'template.xml'.

## Compilation
To compile this version:

    make

## Running the parser
To run the parser and generate 'output.xml':

    make run

It is also possible to run as (all these options are mandatory):

    ./gem5ToMcPAT -x <template_file> -c <config_file> -s <stats_file> -o <output_file>
    ./gem5ToMcPAT --xmltempalte <template_file> --config <config_file> --stats <stats_file> --output <output_file>

In order to get help from the program:

    ./gem5ToMcPAT -h

## Software needed
It has been tested in a Linux distribution with `gcc version 5.2.1`, `bison version 3.0.2`, `flex 2.5.39` and `make 4.0`

The template has been adapted for the [last version](https://code.google.com/archive/p/mcpat/downloads) of [McPAT 1.0]. The gem5 version tested is from [03/2015](https://github.com/gem5/gem5/commit/8909843a76c723cb9d8a0b1394eeeba4d7abadb1), but it should work for a more recent version.

# TODO list

What can be done or improved:

* Parse `system.mc` params and statistics
* Check why dcache `block_size` must be 32 in order to work
* Code clarity
* Portability [?]

# Bugs

This tool is currently in development, so if you find a bug, you can open an issue. If you do not agree with the translation of a parameter or value, please do the same in order to discuss it!

# Limitations
This first version is focused on the compatibility of the output of memory system and core in gem5 with the input of McPAT. Thus, other components such as PCIe will be ignored by the moment.

# References
*[1]*: [Fernando Akira Endo. Génération dynamique de code pour l’optimisation énergétique. Architectures Matérielles [cs.AR]. Université Grenoble Alpes, 2015. Français. <NNT : 2015GREAM044>. <tel-01285964> (Appendix A)](https://tel.archives-ouvertes.fr/tel-01285964/document)