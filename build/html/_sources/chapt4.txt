Code Overview
=====================

Modules in COMBO
----------------------
Instruction to import the modules in COMBO: 
::
        Relative import 'gp', should be 'combo.gp' (relative-import)
        Relative import 'opt', should be 'combo.opt' (relative-import)
        Relative import 'blm', should be 'combo.blm' (relative-import)
        Relative import 'misc', should be 'combo.misc' (relative-import)
        Relative import 'search', should be 'combo.search' (relative-import)
        Relative import 'predictor', should be 'combo.predictor' (relative-import)
        Relative import 'variable', should be 'combo.variable' (relative-import)

Structure of COMBO
----------------------
The files in each directory: 
::
        |-- blm
        |   |-- basis
        |   |   |-- fourier.py
        |   |   `-- __init__.py
        |   |-- core
        |   |   |-- __init__.py
        |   |   `-- model.py
        |   |-- inf
        |   |   |-- exact.py
        |   |   `-- __init__.py
        |   |-- __init__.py
        |   |-- lik
        |   |   |-- gauss.py
        |   |   |-- __init__.py
        |   |   |-- linear.py
        |   |   `-- _src
        |   |       |-- cov.py
        |   |       `-- __init__.py
        |   |-- predictor.py
        |   `-- prior
        |       |-- gauss.py
        |       `-- __init__.py
        |-- gp
        |   |-- core
        |   |   |-- __init__.py
        |   |   |-- learning.py
        |   |   |-- model.py
        |   |   `-- prior.py
        |   |-- cov
        |   |   |-- gauss.py
        |   |   |-- gauss.pyc
        |   |   |-- __init__.py
        |   |   `-- _src
        |   |       |-- enhance_gauss.c
        |   |       |-- enhance_gauss.pyx
        |   |       |-- __init__.py
        |   |       `-- __init__.pyc
        |   |-- inf
        |   |   |-- exact.py
        |   |   `-- __init__.py
        |   |-- __init__.py
        |   |-- lik
        |   |   |-- gauss.py
        |   |   `-- __init__.py
        |   |-- mean
        |   |   |-- const.py
        |   |   |-- __init__.py
        |   |   `-- zero.py
        |   `-- predictor.py
        |-- __init__.py
        |-- misc
        |   |-- centering.py
        |   |-- gauss_elim.py
        |   |-- __init__.py
        |   |-- set_config.py
        |   `-- _src
        |       |-- cholupdate.c
        |       |-- cholupdate.pyx
        |       |-- diagAB.c
        |       |-- diagAB.pyx
        |       |-- __init__.py
        |       |-- logsumexp.c
        |       |-- logsumexp.pyx
        |       |-- traceAB.c
        |       `-- traceAB.pyx
        |-- opt
        |   |-- adam.py
        |   `-- __init__.py
        |-- predictor.py
        |-- search
        |   |-- call_simulator.py
        |   |-- discrete
        |   |   |-- __init__.py
        |   |   |-- policy.py
        |   |   `-- results.py
        |   |-- __init__.py
        |   |-- score.py
        |   `-- utility.py
        `-- variable.py


