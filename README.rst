.. image:: https://img.shields.io/badge/rtn--015-lsst.io-brightgreen.svg
   :target: https://rtn-015.lsst.io
.. image:: https://github.com/lsst/rtn-015/workflows/CI/badge.svg
   :target: https://github.com/lsst/rtn-015/actions/

############################################################
Brighter-Fatter Correction GPU Optimization Using CUDA C/C++
############################################################

RTN-015
=======

Leveraging the GPU with CUDA C/C++, the brighter-fatter effect (BFE) correction algorithm from the Large Synoptic Survey Telescope (LSST) Science Pipelines can be significantly optimized. BFE correction is among several other instrument signature removal (ISR) algorithms that are applied to astronomical images. BFE correction was a particularly good candidate for GPU optimization since it took up a majority of the ISR time (78.15% of the total ISR time). The BFE correction algorithm itself is highly parallelizable, particularly due to its use of convolutions and NumPy functions such as numpy.diff and numpy.gradient. Additionally, the algorithm is an iterative process, which offsets the time to perform memory transfers between the CPU (host) and GPU (device). The GPU implementation of the BFE correction algorithm achieved an average speed up of 10.95x over a CPU implementation using OpenCV C++.

Links
=====

- Live drafts: https://rtn-015.lsst.io
- GitHub: https://github.com/lsst/rtn-015

Build
=====

This repository includes lsst-texmf_ as a Git submodule.
Clone this repository::

    git clone --recurse-submodules https://github.com/lsst/rtn-015

Compile the PDF::

    make

Clean built files::

    make clean

Updating acronyms
-----------------

A table of the technote's acronyms and their definitions are maintained in the ``acronyms.tex`` file, which is committed as part of this repository.
To update the acronyms table in ``acronyms.tex``::

    make acronyms.tex

*Note: this command requires that this repository was cloned as a submodule.*

The acronyms discovery code scans the LaTeX source for probable acronyms.
You can ensure that certain strings aren't treated as acronyms by adding them to the `skipacronyms.txt <./skipacronyms.txt>`_ file.

The lsst-texmf_ repository centrally maintains definitions for LSST acronyms.
You can also add new acronym definitions, or override the definitions of acronyms, by editing the `myacronyms.txt <./myacronyms.txt>`_ file.

Updating lsst-texmf
-------------------

`lsst-texmf`_ includes BibTeX files, the ``lsstdoc`` class file, and acronym definitions, among other essential tooling for LSST's LaTeX documentation projects.
To update to a newer version of `lsst-texmf`_, you can update the submodule in this repository::

   git submodule update --init --recursive

Commit, then push, the updated submodule.

.. _lsst-texmf: https://github.com/lsst/lsst-texmf
