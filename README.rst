.. image:: https://img.shields.io/pypi/v/pyqubo.svg
    :target: https://pypi.python.org/pypi/pyqubo

.. image:: https://codecov.io/gh/recruit-communications/pyqubo/branch/master/graph/badge.svg
  :target: https://codecov.io/gh/recruit-communications/pyqubo

.. image:: https://readthedocs.org/projects/pyqubo/badge/?version=latest
    :target: http://pyqubo.readthedocs.io/en/latest/?badge=latest

.. image:: https://circleci.com/gh/recruit-communications/pyqubo.svg?style=svg
    :target: https://circleci.com/gh/recruit-communications/pyqubo


.. index-start-marker1

PyQUBO
======

(Notice)
(contents) (1. Integer_partition, 2.Graph-Coloring, 3.Graph-partition, 5.TSP (location), 6.TSP (Latitude and longitude))
(papaer) https://journals.jps.jp/doi/full/10.7566/JPSJ.88.061010 
(notebook or code) https://github.com/recruit-communications/pyqubo/tree/master/notebooks
(code) (cvrp) https://github.com/rickyHong/Dwave-cvrp-repl

(contents, code) (4.Multimodal Container Planning)
(paper) https://arxiv.org/abs/2007.01730 


PyQUBO allows you to create QUBOs or Ising models from flexible mathematical expressions easily.
Some of the features of PyQUBO are

* **Python-based**.
* **QUBO generation (compile) is fast.**
* **Automatic validation of constraints.** (`details <https://pyqubo.readthedocs.io/en/latest/getting_started.html#validation-of-constraints>`__)
* **Placeholder** for parameter tuning. (`details <https://pyqubo.readthedocs.io/en/latest/getting_started.html#placeholder>`__)

For more details, see `PyQUBO Documentation <https://pyqubo.readthedocs.io/>`_.

Example Usage
-------------

This example constructs a simple expression and compile it to ``model``.
By calling ``model.to_qubo()``, we get the resulting QUBO.
(This example solves `Number Partitioning Problem <https://en.wikipedia.org/wiki/Partition_problem>`_ with a set S = {4, 2, 7, 1})

>>> from pyqubo import Spin
>>> s1, s2, s3, s4 = Spin("s1"), Spin("s2"), Spin("s3"), Spin("s4")
>>> H = (4*s1 + 2*s2 + 7*s3 + s4)**2
>>> model = H.compile()
>>> qubo, offset = model.to_qubo()
>>> pprint(qubo)
{('s1', 's1'): -160.0,
 ('s1', 's2'): 64.0,
 ('s1', 's3'): 224.0,
 ('s1', 's4'): 32.0,
 ('s2', 's2'): -96.0,
 ('s2', 's3'): 112.0,
 ('s2', 's4'): 16.0,
 ('s3', 's3'): -196.0,
 ('s3', 's4'): 56.0,
 ('s4', 's4'): -52.0}

For more examples, see `example notebooks <https://github.com/recruit-communications/pyqubo/tree/master/notebooks>`_.

Installation
------------

.. code-block:: shell

    pip install pyqubo

or

.. code-block:: shell

    python setup.py install

Supported Python Versions
-------------------------

Python 2.7, 3.4, 3.5, 3.6 and 3.7 are supported.

.. index-end-marker1

Test
----

Run all tests.

.. code-block:: shell

    python -m unittest discover test

Show coverage report.

.. code-block:: shell

    coverage run -m unittest discover
    coverage html

Run test with circleci CLI.

.. code-block:: shell

    circleci build --job $JOBNAME

Run doctest.

.. code-block:: shell

    make doctest

Citation
--------

If you use PyQUBO in your research, please cite `this paper <https://journals.jps.jp/doi/full/10.7566/JPSJ.88.061010>`_.

::

    @article{tanahashi2019application,
      title={Application of Ising Machines and a Software Development for Ising Machines},
      author={Tanahashi, Kotaro and Takayanagi, Shinichi and Motohashi, Tomomitsu and Tanaka, Shu},
      journal={Journal of the Physical Society of Japan},
      volume={88},
      number={6},
      pages={061010},
      year={2019},
      publisher={The Physical Society of Japan}
    }


Organization
------------

Recruit Communications Co., Ltd.

Licence
-------

Released under the Apache License 2.0.

Contribution
------------

We welcome contributions to this project. See `CONTRIBUTING <./CONTRIBUTING.rst>`_.
