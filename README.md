[![Build Status](https://travis-ci.org/k-dominik/ilastik-install.svg?branch=master)](https://travis-ci.org/k-dominik/ilastik-install)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/ambv/black)

# ilastik-install

## Motivation

[ilastik](https://ilastik.org) is distributed by copying the ilastik conda environment on the respective build machines.
In principle, conda environments are not simply transferrable, but for our dependencies it always worked (phew) but by getting more and more dependencies from conda, we run into limitations.
Expecially since we source `X11` from conda, error-messages started popping up because hard-coded, absolute paths (are hard-coded during install time of the conda-packages).

For distribution of our binaries we follow a similar approach as the conda-folks:
* install the release environment to a very long `placeholder...` path
* when ilastik is first started
 * could be problematic on windows, osx. But the problems mainly popped up on linux (because of `X11`)

Took the code for binary/text replacement of the placeholder from [conda/constructor](https://github.com/conda/constructor).
