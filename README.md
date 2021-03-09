# Evolution of urban patterns: urban morphology as an open reproducible data science

Martin Fleischmann<sup>1</sup>, Alessandra Feliciotti<sup>2</sup>, William Kerr<sup>3</sup>

1 Research Associate,  Department of Geography and Planning, University of Liverpool, m.fleischmann@liverpool.ac.uk.

2 Lecturer, Urban Design Studies Unit, Department of Architecture, University of Strathclyde, a.feliciotti@strath.ac.uk

3 Urban Designer, Gillespies, will.kerr@gillespies.co.uk 

## Code and data

This repository contains complete reproducible workflow for a research paper "*Evolution of urban patterns: urban morphology as an open reproducible data science*".

The research has been executed within a Docker container `martinfleis/momepy:0.4.2`. Alternatively, the environment can be built using a `Dockerfile` or as a conda environment using `environment.yml`.

You can start the container as 
```
docker run --rm -ti -p 8888:8888 -v ${PWD}:/home/jovyan/work martinfleis/momepy:0.4.2
```
which will start Jupyter Lab session on `localhost:8888` and mount current working directory to `work` folder within the container. 

Docker container is based on `jupyter/minimal-notebook`. Please see its [documentation](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html#jupyter-minimal-notebook) for details. 

## Abstract

The recent growth of geographic data science (GDS) fuelled by increasingly available open data and open source tools have influenced urban sciences across a multitude of fields. Yet, there is limited application in urban morphology - a science developed around the analysis of urban form. While quantitative approaches to morphological research are finding momentum, existing tools for such analyses have limited scope and are predominantly implemented as plugins for standalone GIS software This inherently restricts transparency and reproducibility of research. Simultaneously, the Python ecosystem for GDS built around GeoPandas and PySAL is maturing to the point of fully supporting highly specialised morphological analysis. In this paper, we implement OSMnx and momepy into a seamless workflow to illustrate their capabilities on a case study, where we assess the evolution of urban form patterns over six historical periods on a sample of 42 locations worldwide. Results show a trajectory of gradual change in the scale and structure of urban form from pre-industrial development to contemporary neighbourhoods, with a peak of highest deviation during the post-WW2 era of Modernism, confirming previous research findings. The wholly reproducible method is encapsulated in Jupyter notebooks, illustrating how modern GDS models can be applied to urban morphology research to promote open, collaborative and transparent science, independent of proprietary or otherwise limited GUI-based software. 
