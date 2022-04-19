# CoFI Test Suite


CoFi TestSuite is a collection of clearly defined, stand-alone forward and inversion problems that each can be solved using the same code structure. The aim is to create a minimalistic framework that is easily understandable while still being capable of hosting a wide range of inversion problems. Information will be conveyed via a sensible, consistent naming convention and informative output at the end consisting of text and visualisations. Extended documentation will be available on Github. 


# Installation

It is recommended to use a clean virtual environment for the install: 

```console
conda create -n cofi_testsuite_env python=3.8 scipy jupyterlab numpy
conda activate cofi_testsuite_env
```

CoFi Test Suite is available on the PyIP test server and can be installed using this command:

```console
python3 -m pip install --index-url https://test.pypi.org/simple/ cofitestsuite-h-hollmann
```

# Basic usage

Once installed, each CoFI test problem can be imported using the following command structure:

```console
from cofitestsuite.testproblem import testproblem as tp
```

Replace ``testproblem`` with one of the following currently available problems:

- ``gravityforward``: 
- ``xraytomorgraphy``: 
- ``earthquakebootstrap``: 
- ``earthquakeleastsquares``: 

Once a problem is imported, it's functions can be called using the same structure for each problem:

```console

from InversionTestProblems import testproblem as tp

model=tp.init_routine(problem_basics) 

synthetic, gradient = tp.forward(problem_basics, model)

result = tp.solver(problem_basics, model, synthetic, gradient)

tp.plot_model(problem_basics, result)

```

Problem-specific values, for example model resolution or noise level, can be specified after calling ``problem_basics=problem_fcn.basics()``:


```console

from InversionTestProblems import testproblem as tp

problem_basics = problem_fcn.basics()
problem_basics.variable=value
problem_basics.variable2=value2
...

```

# How to contribute to the repository:
 <em>This section needs to be include a text about merge before we see more traffic.</em>

Here we assume that the contributor already created a Github account and established a secure connection using https or SSH. If this is not the case please see the following tutorials: 
- [Add a tutorial for how to set up a secure connection.]

To contribute an existing test problem to the Github repository, first clone the Github repository: 

```console
git clone https://github.com/inlab-geo/inversion-test-problems.git
```

Create a new branch for the new test problem:

```console
git checkout -b new_branch
```

Then add the new test problem as a new folder to ``scr/cofitestsuite/newproblem`` (replacing ``newproblem`` with the new problem name) and add the Jupyter Notebook with the name ''newproblem.ipynb'' to the ``Jupyter Notebooks`` folder. 

Then use the following commands to upload the new test problem to the repository:

```console
git add .
git commit -m "A sentence that describes the new problem."
git push
```

The new test problem is now uploaded into the repository. As a last step, visit https://github.com/inlab-geo/inversion-test-problems/branches. Locate the new branch and click on "create pull request". If the changes are confined to the new folder and Jupyter Notebook, the new test problem will be quickly added to the repository and released to pip with the next update.

# How to create a sensible inversion test problem

The code can include files of all kinds of formats. But it needs to include a file called ``newproblem.py``. This file should include the following functions: 
- ``basic()``
- ``init_routine()``
- ``forward()``
- ``solver()``
- ``plot_model()``

Some notes on how to make a local problem work within the repository:
- If the code imports local functions, for example ``import auxillaryfunction'' where auxillaryfunction.py is in the same folder, it is necessary to change the line to ``from cofitestsuite.newproblem import auxillaryfunction``
- If data is included, then the correct path has to be given. 

Additionally, we encourage you to add a Jupyter Notebook with an identical name into the folder ''Jupyter Notebooks`` that contains the following:
- An extensive description of the new inversion test problem, containing information about (but not limited to)...
  - the forward calculation (ie. the underlying physics) and how it was implemented.
  - which inversion method is used (and regularisation) and how it was implemented.
  - the physical unit of relevant variables, but at least of ``model`` and ``data``.
  - all changeable parameters, possibly in a list.
- An example of the new problem being used, with a reasonable output.


description of 

Now, use the following commands to add the new folder into 

<!---  Binder does not work right now.   -->
<!---  [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/inlab-geo/inversion-test-problems/HEAD)   -->

