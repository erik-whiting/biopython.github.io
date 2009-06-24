---
title: PhyloXML
permalink: wiki/PhyloXML
layout: wiki
---

This module handles the parsing and generation of files in the
[phyloXML](http://www.phyloxml.org/) format.

This code is not yet part of Biopython, and therefore the documentation
has not been integrated into the Biopython Tutorial yet either.

Usage
-----

(Coming soon: use cases)

Development
-----------

The source code for this module currently lives on the [phyloxml
branch](http://github.com/etal/biopython/tree/phyloxml) in GitHub.

### Parser

The XML parser used in this module is ElementTree, new to the Python
standard library in Python 2.5. To use this module in Python 2.4, you'll
need to install a separate package that provides the ElementTree
interface. Two exist:

-   [lxml](http://codespeak.net/lxml/)
-   [elementtree](http://effbot.org/zone/element-index.htm)
    (or cElementTree)

The module attempts to import each of these compatible ElementTree
implementations until it succeeds. The given XML file handle is then
parsed incrementally to instantiate an object hierarchy containing the
relevant phylogenetic information. Existing Biopython classes will be
reused for these objects wherever appropriate.

This parser is meant to be able to handle large files, meaning several
thousand external nodes. (Benchmarks of relevant XML parsers for Python
are [here](http://effbot.org/zone/celementtree.htm#benchmarks). To
support this, the parser takes an open file handle, and the API will
offer wrappers for loading compressed files, and perhaps pulling from a
database or web URL, too.

### Writer

The writer portion of this module hasn't been written yet, but
presumably it will be based on ElementTree as well.

### Integration

At some point this should be merged into the Biopython trunk, and it
would be nice to have a common interface with Bio.Nexus and Newick.
Should these three modules be reorganized to extract a common Bio.TreeIO
interface? Let's discuss it at some point.

Summer of Code project
----------------------

This module is being developed by [Eric](User%3AEricTalevich "wikilink")
as a project for Google Summer of Code 2009, with NESCent as the
mentoring organization and Brad as the primary mentor.

Main SoC project page: [PhyloSoC:Biopython support for parsing and
writing
phyloXML](https://www.nescent.org/wg_phyloinformatics/PhyloSoC:Biopython_support_for_parsing_and_writing_phyloXML)

Other software
--------------

[Christian Zmasek](http://monochrome-effect.net/), author of the
phyloXML specification, has released some software that uses this
format:

-   [Forester](http://www.phylosoft.org/forester/) -- a collection of
    Java and Ruby libraries for working with phylogenetic data
-   [Archaopteryx](http://www.phylosoft.org/archaeopteryx/) -- Java
    application for the visualization of annotated phylogenetic trees
    (also available in applet form)

Another list is maintained at
[phylosoft.org](http://www.phylosoft.org/).