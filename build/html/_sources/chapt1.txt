Introduction
=====================
COMmon Bayesian Optimization Library (COMBO)

Bayesian optimization :cite:`Mockus1974pitc` has been proven as an effective tool in accelerating scientific discovery. A standard implementation (e.g., `scikit-learn <http://scikit-learn.org/>`_), however, can accommodate only small training data. COMBO :cite:`Ueno2016md` is highly scalable due to an efficient protocol that employs Thompson sampling :cite:`Chapelle2011nips`, random feature maps :cite:`Rahimi07randomfeatures`, one-rank Cholesky update :cite:`Gill1972mc` and automatic hyperparameter tuning :cite:`Rasmussen2006book`.


Getting Help
----------------------
The latest version of COMBO and documentation can always be found at https://github.com/tsudalab/combo.

Citation
----------------------
We ask that you acknowledge the use of COMBO in any publications arising from the use of this
code through the following reference

[ref] Tsuyoshi Ueno, Trevor David Rhone, Zhufeng Hou, Teruyasu Mizoguchi and Koji Tsuda,
COMBO: An Efficient Bayesian Optimization Library for Materials Science,
Materials Discovery, (2016), in press. Available from http://dx.doi.org/10.1016/j.md.2016.04.001

Bibtex file for citing COMBO  ::

    @article{Ueno2016,
    title = "COMBO: An Efficient Bayesian Optimization Library for Materials Science ",
    journal = "Materials Discovery",
    volume = "",
    number = "",
    pages = "-",
    year = "2016",
    note = "",
    doi = "http://dx.doi.org/10.1016/j.md.2016.04.001",
    url = "http://www.sciencedirect.com/science/article/pii/S2352924516300035",
    author = "Tsuyoshi Ueno and Trevor David Rhone and Zhufeng Hou and Teruyasu Mizoguchi and Koji Tsuda",
    }


Credits
----------------------

Licence
----------------------
This package is distributed under the `MIT License <https://en.wikipedia.org/wiki/MIT_License>`_.

`The MIT License (MIT) <https://opensource.org/licenses/MIT>`_.

Copyright (c) <2015-> <`Tsuda Laboratory <http://www.tsudalab.org/>`_>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

References
----------------------
.. bibliography:: references.bib

