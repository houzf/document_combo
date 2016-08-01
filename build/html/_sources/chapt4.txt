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


Classes and functions in COMBO
-------------------------------
variable object 
^^^^^^^^^^^^^^
COMBO defines a python class called :class:`variable` to setup and handle the dataset in the training and testing. From a python script, variable object can be created like this:
::

    >>>from combo.variable import variable
    >>>import numpy as np
    >>>X= np.array([[1,2,3,4], [5,6,7,8], [9,10,11,12]])
    >>>t=np.array([[1], [5], [9]])
    >>>Z=np.array([[2,6,3,4], [9,6,10,8], [22,10,11,12]])
    >>>vtest=variable(X,t,Z) 
    >>>print vtest.X

.. py:class:: combo.variable.variable

    .. py:attribute:: X
       array_like 
    .. py:attribute:: t
       array_like
    .. py:attribute:: Z
       array_like 
    .. py:method:: get_subset(index)
    .. py:method:: delete(num_row)
    .. py:method:: add(X,t,Z)
    .. py:method:: delete_X(num_row)
    .. py:method:: delete_t(num_row)
    .. py:method:: delete_Z(num_row)
    .. py:method:: add_X(X)
    .. py:method:: add_t(t)
    .. py:method:: add_Z(Z)
    .. py:method:: save(filename)
    .. py:method:: load(filename)


.. py:class:: combo.predictor.base_predictor

    .. py:attribute:: config
    .. py:attribute:: model
    .. py:method:: fit()
    .. py:method:: prepare()
    .. py:method:: delete_stats()
    .. py:method:: get_basis()
    .. py:method:: get_post_fmean()
    .. py:method:: get_post_fcov()
    .. py:method:: get_post_params()
    .. py:method:: get_post_samples()

.. py:function:: combo.misc.centering(X)

    standardize the data X and remove the columns with zero value

    .. math::
            X_{1,1\sigma}=\frac{X_{i}-\bar{X}_S}{\sigma_{X,S}}

    :param X: input data
    :rtype: return the standardized data for the columns with non-zero values

.. py:function:: combo.misc.gauss_elim(L, t)

    :param L:
    :param t:
    :rtype: return

.. py:class:: combo.misc.set_config.set_config

    .. py:method:: show()
    .. py:method:: load()

.. py:class:: combo.misc.set_config.search

    .. py:method:: show()
    .. py:method:: load()

.. py:class:: combo.misc.set_config.learning

    .. py:method:: show()
    .. py:method:: load()

.. py:class:: combo.misc.set_config.batch

    .. py:method:: show()
    .. py:method:: load()

.. py:class:: combo.misc.set_config.online

    .. py:method:: show()
    .. py:method:: load()

.. py:class:: combo.misc.set_config.adam

    .. py:method:: show()
    .. py:method:: load()

.. py:function:: combo.misc.set_config.boolean(str)

    :param str:
    :rtype: return a boolean value

.. py:function:: combo.search.utility.show_search_results(history, N)

    :param history:
    :param N:

.. py:function:: combo.search.utility.show_start_message_multi_search(N, score=None)

    :param N:
    :param score:

.. py:function:: combo.search.utility.show_interactive_mode(simulator, history)

    :param simulator:
    :param history:

.. py:function:: combo.search.utility.is_learning(n, interval)

    :param n:
    :param interval:

.. py:function:: combo.search.call_simulator(simu, action)

    :param simu:
    :param action:

.. py:function:: combo.search.score.EI(predictor, training, test, fmax=None)

    :param predictor:
    :param training:
    :param test:
    :param fmax:
    :rtype: return score

.. py:function:: combo.search.score.PI(predictor, training, test, fmax=None)

    :param predictor:
    :param training:
    :param test:
    :param fmax:
    :rtype: return score

.. py:function:: combo.search.score.TS(predictor, training, test, alpha=1)

    :param predictor:
    :param training:
    :param test:
    :param alpha:
    :rtype: return score

.. py:class:: combo.search.discrete.policy.policy

    .. py:method:: set_seed()
    .. py:method:: delete_actions()
    .. py:method:: write()
    .. py:method:: random_search()
    .. py:method:: bayes_search()
    .. py:method:: get_score()
    .. py:method:: get_marginal_score()
    .. py:method:: get_actions()
    .. py:method:: get_random_action()
    .. py:method:: load()
    .. py:method:: export_predictor()
    .. py:method:: export_training()
    .. py:method:: export_history()
    .. py:method:: _set_predictor()
    .. py:method:: _init_predictor()
    .. py:method:: _set_training()
    .. py:method:: _set_unchosed_actions()
    .. py:method:: _set_test()
    .. py:method:: _set_config()

.. py:class:: combo.search.discrete.results.history

    .. py:method:: write()
    .. py:method:: export_sequence_best_fx()
    .. py:method:: export_all_sequence_best_fx()
    .. py:method:: save()
    .. py:method:: load()

.. py:class:: combo.opt.adam

    .. py:method:: set_params()
    .. py:method:: update()
    .. py:method:: run()
    .. py:method:: _set_options()


.. py:class:: combo.gp.predictor.predictor

    .. py:method:: fit()
    .. py:method:: get_basis()
    .. py:method:: get_post_params()
    .. py:method:: prepare()
    .. py:method:: delete_stats()
    .. py:method:: get_post_fmean()
    .. py:method:: get_post_fcov()
    .. py:method:: get_post_samples()
    .. py:method:: get_predict_samples()


.. py:class:: combo.gp.core.learning.batch

    .. py:method:: run()
    .. py:method:: one_run()
    .. py:method:: init_params_search()

.. py:class:: combo.gp.core.learning.online

    .. py:method:: run()
    .. py:method:: one_run()
    .. py:method:: disp_marlik()
    .. py:method:: init_params_search()
    .. py:method:: get_one_update()

.. py:class:: combo.gp.core.learning.adam

    .. py:method:: rest()
    .. py:method:: get_one_update()

.. py:class:: combo.gp.core.model.model

    .. py:method:: cat_params()
    .. py:method:: decomp_params()
    .. py:method:: set_params()
    .. py:method:: sub_sampling()
    .. py:method:: export_blm()
    .. py:method:: eval_marlik()
    .. py:method:: get_grad_marlik()
    .. py:method:: get_params_bound()
    .. py:method:: prepare()
    .. py:method:: get_post_fmean()
    .. py:method:: get_post_fcov()
    .. py:method:: post_sampling()
    .. py:method:: predict_sampling()
    .. py:method:: print_params()
    .. py:method:: get_cand_params()
    .. py:method:: fit()

.. py:class:: combo.gp.core.prior

    .. py:method:: cat_params()
    .. py:method:: decomp_params()
    .. py:method:: get_mean()
    .. py:method:: get_cov()
    .. py:method:: get_grad_mean()
    .. py:method:: get_grad_cov()
    .. py:method:: set_params()
    .. py:method:: set_mean_params()
    .. py:method:: set_cov_params()
    .. py:method:: sampling()

.. py:class:: combo.gp.cov.gauss.gauss

    .. py:method:: cat_params()
    .. py:method:: print_params()
    .. py:method:: prepare()
    .. py:method:: get_grad()
    .. py:method:: get_cov()
    .. py:method:: set_params()
    .. py:method:: supp_params()
    .. py:method:: decomp_params()
    .. py:method:: save()
    .. py:method:: load()
    .. py:method:: get_params_bound()
    .. py:method:: cat_params()
    .. py:method:: rand_expans()
    .. py:method:: get_cand_params()


.. py:function:: combo.gp.inf.exact.eval_marlik( gp, X, t, params = None )

    :param gp:
    :param X:
    :param t:
    :param params:
    :rtype: return  marlik

.. py:function:: combo.gp.inf.exact.get_grad_marlik( gp, X, t, params = None )

    :param gp:
    :param X:
    :param t:
    :param params:
    :rtype: return grad_marlik

.. py:function:: combo.gp.inf.exact.prepare( gp, X, t, params = None )

    :param gp:
    :param X:
    :param t:
    :param params:
    :rtype: return stats

.. py:function:: combo.gp.inf.get_post_fmean( gp, X, t, params = None )

    :param gp:
    :param X:
    :param t:
    :param params:
    :rtype: return G.dot(alpha) + fmu

.. py:function:: combo.gp.inf.get_post_fcov( gp, X, t, params = None, diag = True )

    :param gp:
    :param X:
    :param t:
    :param params:
    :param diag:
    :rtype: post_cov

.. py:class:: combo.gp.lik.gauss.gauss

    .. py:method:: supp_params()
    .. py:method:: trans_params()
    .. py:method:: get_params_bound()
    .. py:method:: get_cov()
    .. py:method:: get_grad()
    .. py:method:: set_params()
    .. py:method:: get_cand_params()
    .. py:method:: sampling()

.. py:class:: combo.gp.mean.const.const

    .. py:method:: supp_params()
    .. py:method:: get_params_bound()
    .. py:method:: get_mean()
    .. py:method:: get_grad()
    .. py:method:: set_params()
    .. py:method:: init_params()
    .. py:method:: get_cand_params()

.. py:class:: combo.blm.predictor.predictor

    .. py:method:: fit()
    .. py:method:: prepare()
    .. py:method:: delete_stats()
    .. py:method:: get_basis()
    .. py:method:: get_post_fmean()
    .. py:method:: get_post_fcov()
    .. py:method:: get_post_params()
    .. py:method:: get_post_samples()
    .. py:method:: get_predict_samples()
    .. py:method:: update()

.. py:class:: combo.blm.basis.fourier

    .. py:method:: get_basis()
    .. py:method:: set_params()
    .. py:method:: show()
    .. py:method:: _check_params()
    .. py:method:: _check_len_params()

.. py:class:: combo.blm.core.model.model

    .. py:method:: prepare()
    .. py:method:: update_stats()
    .. py:method:: get_post_params_mean()
    .. py:method:: get_post_fmean()
    .. py:method:: sampling()
    .. py:method:: post_sampling()
    .. py:method:: predict_sampling()
    .. py:method:: get_post_fcov()
    .. py:method:: _set_options()
    .. py:method:: _init_prior()

.. py:function:: combo.blm.inf.exact.prepare( blm, X, t, Psi = None )

    :param blm:
    :param X:
    :param t:
    :param Psi:

.. py:function:: combo.blm.inf.exact.update_stats( blm, x, t, Psi = None )

    :param blm:
    :param x:
    :param t:
    :param Psi:
    :rtype: return ( L, b, alpha )

.. py:function:: combo.blm.inf.exact.sampling( blm, w_mu = None, N=1, alpha = 1.0 )

    :param blm:
    :param w_mu:
    :param N:
    :param alpha:
    :rtype: return (invLz.transpose() + w_mu).transpose()

.. py:function:: combo.blm.inf.exact.get_post_params_mean( blm )

    :param blm:
    :rtype: return blm.stats[2] * blm.lik.cov.prec 


.. py:function:: combo.blm.inf.exact.get_post_fmean( blm, X, Psi = None, w = None )

    :param blm:
    :param X:
    :param Psi:
    :param w:
    :rtype: return Psi.dot(w) + blm.lik.linear.bias 

.. py:function:: combo.blm.inf.exact.get_post_fcov( blm, X, Psi = None, diag = True )

    :param blm:
    :param X:
    :param Psi:
    :param diag:
    :rtype: return fcov 

.. py:class:: combo.blm.lik.gauss.gauss

    .. py:method:: get_cov()
    .. py:method:: get_prec()
    .. py:method:: get_basis()
    .. py:method:: get_mean()
    .. py:method:: set_params()
    .. py:method:: set_bias()
    .. py:method:: sampling()

.. py:class:: combo.blm.lik.linear.linear

    .. py:method:: get_mean()
    .. py:method:: set_params()
    .. py:method:: set_bias()
    .. py:method:: _init_params()
    .. py:method:: _init_bias()

.. py:class:: combo.blm.prior.gauss.cov_const

    .. py:method:: get_cov()
    .. py:method:: get_prec()
    .. py:method:: set_params()
    .. py:method:: _trans_params()

.. py:class:: combo.blm.prior.gauss.gauss

    .. py:method:: get_mean()
    .. py:method:: get_cov()
    .. py:method:: get_prec()
    .. py:method:: set_params()
    .. py:method:: _init_cov()
