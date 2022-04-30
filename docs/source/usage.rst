=====
Usage
=====

.. _installation:

Installation: Development Environment
=====================================

The development environment and setup for each component is described in reasonable
detail in the relevant repository’s README file.  The documentation is reproduced below:

General: Cloning and Setting Up the Node.js Environment
-------------------------------------------------------

Both the Frontend and Backend utilize Node.js as a platform, the latter also using React
as its primary framework. The process for cloning the repository and installing Node
dependencies is the same between both components:

**Cloning the Project:**

To contribute to the project, it is expected that you first create a fork of the relevant
repository, clone that repository, perform your work, and use the Pull Request mechanism
to contribute to the main repository. Github has easy-to-follow documentation on this
process available `here: <https://docs.github.com/en/get-started/quickstart/contributing-to-projects>`_.

**Installing Node dependencies**

To run the project component(s) locally on your machine, you must first install the
NPM packages upon which the component(s) depend. This must be done for each component
which has its own repository.  First, ensure that Node and NPM are installed (it is
recommended using NVM, the Node Version Manager). Then, run npm install in the root
of the repository’s directory. This will install the packages recorded in
package.json as dependencies.

To run the project locally, enter ``npm start``.

.. _components:

Components
==========

Frontend
--------
The Frontend utilizes React as its main framework, and as such must be built before
deployment.  This build may be performed by running npm build in the project’s root
directory. This will produce a ``/build`` directory from which Netlify deploys. This
directory contains the transpiled JavaScript, HTML, and CSS which is created from
the main project code.

Backend
-------
The Backend uses Express.js as its main framework, and unlike the Frontend, does not
need to be “compiled” in the same sense before deployment.  However, the main “App”
component is written in TypeScript, which does need to be compiled before deployment.
This process is completed automatically when the npm start script is evoked,a process
which is also completed by Heroku when the project is deployed.

.. _testing:

Testing
=======

Frontend
--------
Once testing is implemented later in the semester, a script will be defined which
can then be invoked with ``npm test``.

Backend
-------
The testing script for the backend is defined in the package.json file as being invoked
by npm test. This runs the test file defined at ``/test/test.js``. This file uses the
`Mocha testing library <https://mochajs.org>`_ to test the backend's routes and return
values. This script is run each time a pull request is merged into the main repository.

The Backend's API is tested using a set of `Postman <https://www.postman.com/>`_ tests.
