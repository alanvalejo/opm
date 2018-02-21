## OPM (One-mode projection-based multilevel method for bipartite networks)

**About**

This is an Python implementation of a novel multilevel method based on one-mode projection that allows executing traditional multilevel methods in bipartite network models, published by Alan et. al. [1] and [2].  The aim to reduce the cost of an optimization process by applying it to a reduced or coarsened version of the original bipartite network.

**Usage**

    $ python coarsening.py [options]

| Option					| Domain					| Required	| Default 			| Description															|
|:------------------------- |:------------------------- | --------	| ----------------- | :-------------------------------------------------------------------- |
| -f, --filename			| string [FILE]				| yes		| - 				|  Dataset as input file												|
| -v, --vertices			| int						| yes		| -					|  Number of vertices for each layer									|
| -d, --directory			| string [DIR]				| no		| '.' 				|  Output directory														|
| -o, --output				| string [FILE]				| no		| filename 			|  Output file															|
| -r, --rf					| array in (0, 0.5]			| no		| [0.5] * n 		|  Reduction factor for each layer										|
| -m, --ml					| array in [0, n]			| no		| 1					|  Max levels for each layer											|
| -c, --matching			| string 					| no		| Hem				|  Matching method														|
| -s, --similarity			| string					| no		| Common Neighbors	|  Similarity measure													|
| -l, --layers				| {1,2}						| no		| all				|  Layers that will be processed										|
| -e, --extension			| string [ncol, gml, pajek]	| no		| .ncol 			|  Output extension														|
| --save_hierarchy			| store true				| no		| False 			|  Save all levels of hierarchy of coarsening							|
| --show_timing				| store true				| no		| False 			|  Show timing															|
| --save_timing_csv			| store true				| no		| False 			|  Show timing in csm													|
| --save_timing_json		| store true				| no		| False 			|  Save timing in json													|
| --unique_key				| store true				| no		| False 			|  Output date and time as unique_key									|

The matching strategy selects the best pairs of vertices for matching. Formally, a matching $M$ can be denoted by a set of pairwise non-adjacent edges, i.e., a set of edges with no common vertices. In this software it is possible use two matching methods:

> * Heavy Edge Matching (Hem)
> * Light Edge Matching (Lem)
> * Random Matching (Rm)

Bipartite networks can be transformed into unipartite networks through one-mode projections. Application of a one-mode projection to a bipartite network generates two unipartite networks, one for each layer, so that vertices with common neighbors are connected by edges in their respective projection. In this software it is possible use some similarity measures for generation of unipartite networks:

> * Common Neighbors
> * Weighted Common Neighbors
> * Preferential Attachment
> * Jaccard
> * Salton
> * Adamic Adar
> * Resource Allocation
> * Sorensen
> * Hub Promoted
> * Hub Depressed
> * Leicht Holme Newman

**Quick benchmark results**

We test a scientific collaboration network (Cond-Mat), available [here](https://toreopsahl.com/datasets/#newman2001), which is based on preprints posted in the Condensed Matter section (arXiv) between 1995 and 1999 and has 38.742 vertices (authors and papers) and 58.595 edges (authorship) among different types of vertices.

    $ python coarsening.py -f input/condmat9599R16726C22016.ncol -v 16726 22016 -m 1 1 -r 0.5 0.5 --show_timing

    	Snippet   Time [m]   Time [s]
          Load        0.0     0.4741
    Coarsening        0.0     1.7116
          Save        0.0     0.1087

	$ python coarsening.py -f input/condmat9599R16726C22016.ncol -v 16726 22016 -m 2 2 -r 0.5 0.5 --show_timing

    	Snippet   Time [m]   Time [s]
          Load        0.0     0.4807
    Coarsening        0.0     2.4015
          Save        0.0     0.0340

	$ python coarsening.py -f input/condmat9599R16726C22016.ncol -v 16726 22016 -m 3 3 -r 0.5 0.5 --show_timing

    	Snippet   Time [m]   Time [s]
          Load        0.0     0.4830
    Coarsening        0.0     2.8129
          Save        0.0     0.0467

**Dependencies**

* Python: tested with version 2.7.13.
* Packages needed: igraph and numpy.

**Known Bugs**

Please contact the author for problems and bug report.

**Contact**

* Alan Valejo.
* Ph.D. candidate at University of São Paolo (USP), Brazil.
* alanvalejo@gmail.com.


**License (For a complete version of the license, see the COPYING.md)**

* Can be used for creating unlimited applications
* Can be distributed in binary or object form only
* Non-commercial use only
* Can modify source-code and distribute modifications (derivative works)
* Giving credit to the author by citing the papers
* License will expire in 2018, July, and will be renewed

**Download**

* You can download the MkNN software in http://www.alanvalejo.com.br/software?id=1

**References**

> [1] Valejo, A.; Ferreira V.; Rocha Filho, G. P.; Oliveira, M. C. F.; and Lopes, A. A.: One-mode projection-based multilevel approach for community detection in bipartite networks. Proceedings of the International Symposium on Information Management and Big Data (SIMBig), Social Network and Media Analysis and Mining (SNMAM). 2018
>
> [2] Valejo, A.; Ferreira V.; Oliveira, M. C. F.; and Lopes, A. A.:  Community detection in bipartite network: a modified coarsening approach. Extended version and Revised Selected Papers. Proceedings of the International Symposium on Information Management and Big Data (SIMBig), Social Network and Media Analysis and Mining (SNMAM). 2018. (to publish)

~~~~~{.bib}
@proceedings{Alan_2014a,
    author={Valejo, A.; Ferreira V.; Rocha Filho, G. P.; Oliveira, M. C. F.; and Lopes, A. A.},
    title={One-mode projection-based multilevel approach for community detection in bipartite networks},
    booktitle={Proceedings of the International Symposium on Information Management and Big Data (SIMBig), Social Network and Media Analysis and Mining (SNMAM)},
    year={2018},
}
@proceedings{Alan_2014b,
    author={Valejo, A.; Ferreira V.; Oliveira, M. C. F.; and Lopes, A. A.},
    title={Community detection in bipartite network: a modified coarsening approach},
    booktitle={Proceedings of the International Symposium on Information Management and Big Data (SIMBig), Social Network and Media Analysis and Mining (SNMAM), Extended version and Revised Selected Papers.},
    year={2018},
	note={to publish}
}
~~~~~

<div class="footer"> &copy; Copyright (C) 2017 Alan Valejo &lt;alanvalejo@gmail.com&gt; All rights reserved.</div>
