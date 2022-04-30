=====
Usage
=====

.. _installation:

Installation
============

Development Environment
-----------------------

The development environment and setup for each component is described in reasonable
detail in the relevant repository’s README file.  The documentation is reproduced below:

**General: Cloning and Setting Up the Node.js Environment**

Both the Frontend and Backend utilize Node.js as a platform, the latter also using React
as its primary framework. The process for cloning the repository and installing Node
dependencies is the same between both components:

*Cloning the Project:*

To contribute to the project, it is expected that you first create a fork of the relevant
repository, clone that repository, perform your work, and use the Pull Request mechanism
to contribute to the main repository. Github has easy-to-follow documentation on this
process available `here: <https://docs.github.com/en/get-started/quickstart/contributing-to-projects>`_.

*Installing Node dependencies*

To run the project component(s) locally on your machine, you must first install the
NPM packages upon which the component(s) depend. This must be done for each component
which has its own repository.  First, ensure that Node and NPM are installed (it is
recommended using NVM, the Node Version Manager). Then, run npm install in the root
of the repository’s directory. This will install the packages recorded in
package.json as dependencies.

To run the project locally, enter ``npm start``.

Creating recipes
----------------

To retrieve a list of random ingredients,
you can use the ``lumache.get_random_ingredients()`` function:

.. autofunction:: lumache.get_random_ingredients

The ``kind`` parameter should be either ``"meat"``, ``"fish"``,
or ``"veggies"``. Otherwise, :py:func:`lumache.get_random_ingredients`
will raise an exception.

.. autoexception:: lumache.InvalidKindError

For example:

>>> import lumache
>>> lumache.get_random_ingredients()
['shells', 'gorgonzola', 'parsley']

