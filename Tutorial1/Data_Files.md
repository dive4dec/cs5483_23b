---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.16.1
kernelspec:
  display_name: Python 3 (ipykernel)
  language: python
  name: python3
---

+++ {"slideshow": {"slide_type": "slide"}}

# Data Files

+++ {"slideshow": {"slide_type": "-"}, "tags": ["remove-cell"]}

**CS5483 Data Warehousing and Data Mining**
___

+++ {"slideshow": {"slide_type": "slide"}}

## Load data into Weka Explorer Interface

+++

**How to start Weka in JupyterHub?**

- Open the Launcher (`File->New Launcher`)
- Start a `Desktop` from the Launcher.
- Start a `Terminal` from the menu on the top left.
- Run the command `weka` and click the `Explorer` button.
- Load data from the folder `/data/`.

+++ {"slideshow": {"slide_type": "subslide"}}

::::{tip} Other methods to run Weka
:class: dropdown

- To run Weka locally on your computer:
  1. Download and install Weka from [here][Weka], and
  1. obtain the data files from  
     1. the subfolder `data` of your Weka installation path, or
     1. download from [here][WekaData].  
- For the computers in CSC teaching studios, you can start Weka as follows: 
  1. Click the shortcut `Work Desk` from desktop.
  1. Click the link `Weka 3.8.x` for CS Department.
  1. Load the dataset from  
  `C:\Program Files\Weka-3-8\data\`.
- For the computers in CS labs, you can start Weka as follows: 
  1. Execute `G:\weka\3.8\run.bat`,
  1. Click the `Explorer` button, and
  1. Load the dataset from  
  `C:\temp\Weka-3.8\data` or `G:\weka\3.8\files\data`.

[WekaData]: https://github.com/Waikato/weka-3.8/tree/master/wekadocs/data
[Weka]: https://waikato.github.io/weka-wiki/downloading_weka/

::::

+++ {"slideshow": {"slide_type": "fragment"}}

Use Weka to do [\[Witten11\] Exercises 17.1.1 and 17.1.2.][Witten11].

[Witten11]: https://ebookcentral.proquest.com/lib/cityuhk/reader.action?docID=634862&ppg=595

+++ {"slideshow": {"slide_type": "subslide"}}

::::{exercise} Ex 17.1.1
:label: ex:17.1.1

::::

+++ {"nbgrader": {"grade": true, "grade_id": "Witten11-17-1-1", "locked": false, "points": 1, "schema_version": 3, "solution": true, "task": false}, "slideshow": {"slide_type": "-"}}

hot, mild, cool.

+++ {"slideshow": {"slide_type": "subslide"}}

::::{exercise} Ex 17.1.2
:label: ex:17.1.2

::::

+++ {"nbgrader": {"grade": true, "grade_id": "Witten11-17-1-4", "locked": false, "points": 1, "schema_version": 3, "solution": true, "task": false}, "slideshow": {"slide_type": "-"}}

1. 150 instances.
1. 5 attributes.
1. 1 to 6.9.

+++ {"slideshow": {"slide_type": "slide"}}

## Create an ARFF file

+++ {"slideshow": {"slide_type": "fragment"}}

Create an ARFF file named `AND.arff` in the current directory for the AND gate $Y=X_1\cdot X_2$. Use `0` and `1` to represent `False` and `True` respectively.

+++

::::{important}

See the [documentation](https://waikato.github.io/weka-wiki/formats_and_processing/arff_stable/) for the ARFF file format, or take a look at some of the ARFF files in the WEKA data folder as examples.

::::

+++ {"slideshow": {"slide_type": "fragment"}}

::::{tip}

To generate the file from this notebook directly:
1. Copy the solution template below to the following solution cell.
1. Replace each underscore `_` by an appropriate value.
1. Execute the code cell.

```python
content = '''
@RELATION AND
@ATTRIBUTE X1 {0, 1}
@ATTRIBUTE X2 {_, _}
@ATTRIBUTE Y {_, _}
@DATA
_, _, _
_, _, _
_, _, _
_, _, _
'''
```

Alternatively, you may use other editors in JupyterHub to create `AND.arff` in the current folder.

::::

```{code-cell} ipython3
---
nbgrader:
  grade: false
  grade_id: AND
  locked: false
  schema_version: 3
  solution: true
  task: false
slideshow:
  slide_type: '-'
tags: [remove-output]
---
### BEGIN SOLUTION
content = '''
@RELATION AND
@ATTRIBUTE X1 {0, 1}
@ATTRIBUTE X2 {0, 1}
@ATTRIBUTE Y {0, 1}
@DATA
0, 0, 0
0, 1, 0
1, 0, 0
1, 1, 1
'''
### END SOLUTION

# write the content of text to the file
try: content
except NameError: 
    print("AND.arff not generated because `content` is undefined.")
else:
    filename = 'AND.arff'
    with open(filename,'w') as f:
        f.write(content)
    print("AND.arff generated.")
```

+++ {"slideshow": {"slide_type": "subslide"}}

Run the following test cell to see if your file is a valid ARFF file. You may also download and load the ARFF file into WEKA to see if there is any syntax error.

```{code-cell} ipython3
---
nbgrader:
  grade: true
  grade_id: test-AND
  locked: true
  points: 1
  schema_version: 3
  solution: false
  task: false
slideshow:
  slide_type: '-'
tags: [remove-output]
---
# test
print('Content of AND.arff:')
with open(filename) as f:
    print(f.read())

from scipy.io import arff
import pandas as pd

d = arff.loadarff(filename)
df = pd.DataFrame(d[0]).astype(int)
df.head()
```

```{code-cell} ipython3
---
nbgrader:
  grade: true
  grade_id: htest-AND
  locked: true
  points: 1
  schema_version: 3
  solution: false
  task: false
tags: [remove-cell]
---
# hidden tests
### BEGIN HIDDEN TESTS
ds = [[0, 0, 0],
      [0, 1, 0],
      [1, 0, 0],
      [1, 1, 1]]
assert all((df.loc[(df.X1==eg[0]) & (df.X2==eg[1]),'Y'] == eg[2]).all() for eg in ds)

import os
os.remove(filename)
### END HIDDEN TESTS
```
