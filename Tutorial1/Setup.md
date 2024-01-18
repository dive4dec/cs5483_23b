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

# Setup

+++ {"tags": ["remove-cell"]}

**CS5483 Data Warehousing and Data Mining**
___

+++ {"slideshow": {"slide_type": "slide"}, "editable": true}

## Tutorial materials

+++

Tutorial materials are written in the form of Jupyter Notebooks. Jupyter Notebooks provide an interactive literate programming experience, which is a significant benefit for learners:

- Jupyter Notebooks allow programs to be mixed with other contents, including figures, videos, and formatted textual explanations.
- The notebooks can also run in a Jupyter server, which enables users to write and run their programs while adding formatted notes to it.
- The Jupyter server can access local and remote large language models, which enables an AI pair programming experience that speed up tedious coding tasks.

+++ {"editable": true, "slideshow": {"slide_type": "subslide"}}

### How to access the programming environment?

+++

The course's programming environment is conveniently accessible via a JupyterHub server, allowing remote access without the need to install any special software, thanks to <wiki:Project_Jupyter>. This means you can easily write and run programs on your mobile devices using just a web browser.

+++

You can access the JupyterHub server from the canvas course website or click this [LTI login link](https://www.cs.cityu.edu.hk/~ccha23/cs5483_23a/). The [LTI Authenticator](https://ltiauthenticator.readthedocs.io) provides a seamless login experience using your Canvas login credentials. After your initial LTI login, your account will be created in JupyterHub.

+++ {"slideshow": {"slide_type": "fragment"}, "editable": true}

::::{tip}

If you access JupyterHub from a bookmarked link, you may see a Login box as shown in [](#fig:login-box).

  1. Enter your [EID](https://www.cityu.edu.hk/esu/eid.htm) and Password in the fields `Username` and `Password` respectively.
  1. Click the `Sign in` button.

:::{figure} images/login.dio.svg
:name: fig:login-box
:alt: Login box
:align: left

Login box
:::

::::

+++ {"editable": true, "slideshow": {"slide_type": ""}}

To access the Jupyter environment, simply log into the JupyterHub server and select the `Default` option from the list of available Jupyter servers. Click `Start` to begin your session. If the server is spawned successfully, the JupyterLab interface should appear. Each student will have their own Jupyter server, providing individual computer resources such as CPU and memory.

+++ {"editable": true, "slideshow": {"slide_type": "subslide"}}

::::{note} Server options

- The `Default` option runs on the Ubuntu operating system with some data mining tools pre-installed.
  See the [dockerfile](https://github.com/dive4dec/jupyter/blob/main/cs5483nb/Dockerfile) for details.
- The `GPU` option offers some GPU resources if available.
- You can switch between the `Default` and other server options at any time by restarting your server and selecting the desired option. Restarting the server is simple and can be done through the hub control panel, as described in the note below.

:::{tip} Troubleshooting[^1]
:class: dropdown

In case the jupyterlab interface fails to show:

- Refresh the page or restart your browser.
- Restart your server using the `Hub Control Panel` under the `File` and click `Stop My Server` and then `Start My Server`.

:::

::::

[^1]:  click me to expand

+++ {"editable": true, "slideshow": {"slide_type": "slide"}}

### How to access the tutorial notebooks?

+++ {"slideshow": {"slide_type": ""}, "editable": true}

The recommended way is to access the tutorial notebooks is to follow the links on the course homepage. The notebooks actually reside in a [GitHub repository](https://github.com/dive4dec/cs1302_23a/blob/main/README.md). The first time you access the notebook link, the following steps occur:

- Your Jupyter server is opened.
- The repository is cloned to the server as a local repository.
- The desired notebook is opened in the JupyterLab interface.

+++

Afterwards, accessing a notebook link again will

- [git-pull](https://git-scm.com/docs/git-pull)s new or existing files in the repository and 
- merge them with the notebooks stored under the course folder `cs5483_23b` in your home directory without overwriting your changes.

+++ {"slideshow": {"slide_type": ""}, "editable": true}

::::{important}

Manually fetching the notebooks through other means may not create the local repository required for git version control. This can result in new notebooks or changes to existing notebooks not being pulled properly to your server. To ensure that you have the latest versions of the notebooks with proper version control, use the provided notebook links.

:::{seealso} How git-pull links work?
:class: dropdown

If you are interested in how the link works, see [`nbgitpuller`](https://jupyterhub.github.io/nbgitpuller/index.html). A git-pull link looks as follows:

```bash
https://{{server_url}}/git-pull        # send request to jupyter server
repo={{git_repo}}&                     # pull from the git repository
urlpath=lab/tree/{{path_to_notebook}}  # follow the path to open the notebook
```

:::

::::

+++

The released notebooks are also compiled into an ebook <https://www.cs.cityu.edu.hk/~ccha23/cs5483book>,
which allows you to preview the notebooks conveniently as webpages and download the notebooks in PDF or ipynb formats.

+++ {"slideshow": {"slide_type": "slide"}, "editable": true}

## Lab Assignments

+++ {"slideshow": {"slide_type": "subslide"}}

### How to complete a lab assignment?

+++

The notebooks can be edited in JupyterLab to include your notes and answers for submission. If this is your first time using JupyterLab, take a look at the official video tutorial:

+++

:::{iframe} https://www.youtube.com/embed/A5YyoCKxEOU
:width: 100%
:align: left

Official video tutorial on Jupyter
:::

+++ {"editable": true, "slideshow": {"slide_type": "fragment"}}

The `Help` menu gives more detailed references. For instance:

- Checkout the menu item `Show Keyboard Shortcuts` and try some of the shortcuts to see their effect. `Jupyter Reference` opens the [user guide](https://jupyterlab.readthedocs.io/en/latest/user/interface.html) in a new tab.
- Try the [MyST Markdown](https://mystmd.org/guide/typography) syntax to format your notes.

+++

In learning a new programming language, the first program to write is often the ["Hello, World!"](https://en.wikipedia.org/wiki/%22Hello,_World!%22_program) program, which says Hello to the world. As your first lab exercise, you will write such a program in python.

+++ {"editable": true, "slideshow": {"slide_type": "subslide"}, "nbgrader": {"grade_id": "qHelloWorld", "task": false, "schema_version": 3, "grade": false, "solution": false, "locked": true}}

:::::{exercise} Hello World
:label: ex:Hello-World

Complete the program in the solution cell to print the message `Hello, World!`. 

::::{hint}
:class: dropdown

One possible solution is:

:::{code-block} python
:name: code:Hello-World
:caption: Python, "Hello, World!"

def say_hello():
    print("Hello, World!")
    
say_hello()
:::

:::{caution}
You must use a tab or 4 spaces to indent the second line of code `print(...)`.
:::

::::

:::::

+++ {"editable": true, "slideshow": {"slide_type": ""}}

The following code cell is a solution cell. Since you are not expected to know python before, you can simply expand the hint above and copy the solution to the solution cell instead.

```{code-cell} ipython3
---
code_folding: []
editable: true
nbgrader:
  grade: false
  grade_id: helloworld
  locked: false
  schema_version: 3
  solution: true
  task: false
slideshow:
  slide_type: '-'
tags: [remove-output]
---
def say_hello():
    ### BEGIN SOLUTION
    print("Hello, World!")
    ### END SOLUTION
    
say_hello()
```

+++ {"slideshow": {"slide_type": "subslide"}, "editable": true}

:::{important}

It's important to follow certain guidelines when writing your answers or code in the notebooks:

- Only provide your answers in the cells that are designated for this purpose, which are usually labeled with `YOUR CODE HERE` or `YOUR ANSWER HERE`.
- For coding exercises, be sure to remove the line `raise NotImplementedError()` from the cell before submitting your work.
- Do not clone or duplicate the answer cells, as this can cause issues with version control and grading.

:::

+++

To test your program:

- Run your program by selecting the solution cell and press `Shift`+`Enter`.
- Then, run the following visible test to check whether your program prints the correct message.

```{code-cell} ipython3
---
editable: true
nbgrader:
  grade: true
  grade_id: test-helloworld
  locked: true
  points: 1
  schema_version: 3
  solution: false
  task: false
slideshow:
  slide_type: '-'
tags: [remove-output]
---
# Run this test cell right after running your "Hello, World!" program.
import io
import sys

old_stdout, sys.stdout = sys.stdout, io.StringIO()
say_hello()
printed = sys.stdout.getvalue()
sys.stdout = old_stdout
assert printed == "Hello, World!\n"
```

+++ {"editable": true, "slideshow": {"slide_type": ""}}

The test returns an assertion error if your program does not print the correct message.

+++ {"editable": true, "slideshow": {"slide_type": ""}}

::::{tip}

- You can repeatedly modify your solution and run the test cell until your solution passes the test. There is no mark penalty in failing the test before submission. 
- You should try to understand the error messages from a failed test.
- To assess your solution thoroughly, we will run new tests hidden from you after you have submitted your notebook. Therefore, *you should ensure your solution works in general rather than just the visible tests*.
- If you open the same notebook multiple times in different browser windows, be careful in making changes in different windows as you may overwrite your own changes.
- If your notebook fails to run any code, the kernel might have died. You can restart the kernel with `Kernel`$\to$ `Restart`. If restarting fails, check your code cells to see if there is anything that breaks the kernel.

::::

+++ {"slideshow": {"slide_type": "slide"}}

### How to submit a notebook

+++

Each lecture has a set of corresponding tutorial notebooks. They provide hands-on practice for the individual Project 1 and group Project 2. Although they don't typically count towards the final grade, if both submission rates of the first two tutorials are over 50%, the tutorial scores may count up to 5% bonus points towards the 30% project 1 and 2 grades.

+++ {"slideshow": {"slide_type": ""}, "editable": true}

:::{important} Grading policies

- The tutorial notebooks for each lecture are *due before the next lecture*.
- Late submissions will not be graded without valid justifications.
- You can submit your assignment repeatedly before the deadline without penalty, so it is recommended to submit your assignment in advance.
- It is also important to make a record or backup of your submission that includes the submission timestamp. Double check to ensure that you have submitted the correct lab assignment, since multiple lab assignments may be open for submission at the same time.

:::

+++

[Nbgrader](https://nbgrader.readthedocs.io/en/stable/index.html) is the tool used for grading notebook assignments. It is well-integrated into the JupyterLab interface, allowing students to submit their notebooks directly through the JupyterHub server. Submitted notebooks can be both auto-graded with pre-defined test cases and manually graded with custom feedback. After grading is complete, you can check your scores and access the feedback using the same interface.

+++ {"slideshow": {"slide_type": "fragment"}, "nbgrader": {"grade": false, "task": false, "locked": true, "solution": false, "schema_version": 3, "grade_id": "Check"}, "editable": true}

Before you submit, make sure everything runs as expected:

1. **Git-pull the notebooks** (optional): Follow any one of the link on the course homepage to a notebook, which will git-pull any updates/corrections to (all) your notebooks.
1. **Save the notebook**: Unsaved changes are not exported, even though they are in the memory.
1. **Restart the kernel**: `Kernel`$\to$ `Restart Kernel...` to have a clean state before running visible tests.
1. **run all cells**: `Run`$\to$ `Run All Cells` to double check the results of the visible tests are as expected.

+++ {"slideshow": {"slide_type": "subslide"}, "editable": true}

To submit your notebook:

1. Select the menu item `Nbgrader`$\to$`Assignment List`.
1. Expand the Lab folder and click the `validate` button next to the notebook(s) to check if all the visible tests pass.
1. Click `Submit` to submit your notebook.

+++ {"editable": true, "slideshow": {"slide_type": ""}}

::::{caution}

Your submission may not be graded under the following circumstances:

- If the notebook files have been renamed, for example, `Setup.ipynb` being changed or copied to `Setup (Copy).ipynb`.
- If an HTML file exists with the same name as a notebook, for example, `Setup.html`.
- If the file size exceeds `100MB`.
- If the code takes too long to run or requires an excessive amount of memory.

It is essential to ensure that your submission meets these guidelines to avoid any issues with grading.

:::{tip} Troubleshooting
:class: dropdown

If you believe your notebooks are corrupted, 
1. download/backup your existing notebooks,
1. remove them from the `Lab*/` folder,
1. click the git-pull links from the course homepage to re-pull the notebooks, and
1. copy your solutions to the new notebooks.

You may also run the course notebooks outside the jupyterhub server and locally on your computer. For more details, see the course homepage.

:::

::::

+++

## AI Tutor

+++ {"slideshow": {"slide_type": "slide"}}

### How to play with LLMs in notebooks?

+++

Large language models (LLMs) have been integrated into the Jupyter server using [`jupyter-ai`](https://github.com/jupyterlab/jupyter-ai/blob/main/README.md).

```{code-cell} ipython3
# load the cell magic to interact with a LLM in a cell
%reload_ext jupyter_ai
# list available providers/models
%ai list
```

While most of the providers require subscriptions, you can try a local model `diveai-chat:mistral` deployed locally.

```{code-cell} ipython3
%%ai diveai-chat:mistral
Write a python hello world program.
```

```{code-cell} ipython3
%%ai diveai-chat:mistral
Give a brief introduction to AI pair programming.
```

There is also a Jupyternaut chatbot:

1. Click the chat icon on the left menu bar. A chat panel will open.
1. Click the gear icon on the chat panel to set up the provider.
1. Select the first model `AI :: mistral` and click the `Save Changes` button.
1. Click the back arrow at the top to go back to the chat window.
1. Enter `/ask how are you today?` to see a response.

+++

::::{tip}
:class: dropdown

You can also use the vscode interace with the [`ai-genie` extension](https://github.com/ai-genie/chatgpt-vscode/blob/main/README.md):

1. Open [VSCode](https://dive.cs.cityu.edu.hk/cs5483_23b/user-redirect/vscode).
2. Click the genie icon of the left menu bar to open the chat panel.
3. Click the gear button to setup the provider.
4. Set `genieai.openai.model` to `gpt-3.5-turbo`, which will trigger a pop-up box asking for API key.
5. Enter any non-empty string as the key.
6. Change `genieai.openai.apiBaseUrl` from `https://api.openai.com` to `https://ai.local-ai` without trailing slash.
7. Reload the vscode window (`Shift-Cmd/Ctrl-P` and type reload).

::::

+++

### How to subscribe to Azure OpenAI?

+++

To play with other models such as `gpt-4`, registered students can subscribe to Azure OpenAI as follows:

1. Access <https://www.cs.cityu.edu.hk/~ccha23/cs5483_23b/apim> and click `Active Directory - Login` to login with your CityU active directory credentials.
2. From the top menu, navigate to the product page and click the [link to cs5483-2024-openai](https://www.cs.cityu.edu.hk/~ccha23/cs5483_23b/apim?next=product%23product=cs5483-2024-openai)
3. Enter any name such as cs5483 in the textbox and click subscribe. You will be brought to the profile page where you can show/regenerate your primary/secondary api keys.
4. Navigate to the apis page and click the [link to cs5483-2024](https://www.cs.cityu.edu.hk/~ccha23/cs5483_23b/apim?next=api-details%23api=659b53a77acc9f64d2862811&operation=echo-api).
5. On the left panel, click the available API to show the corresponding base url.
6. On the right panel, you may test access the chosen API chosen on the left panel:
   - Select the `echo` API on the left and the protocol `HTTP` on the right.
   - Click `Send` to send the request.
   - You should receive HTTP response `200 okay` if the connection is successful.
8. For APIs other than echo:
   - Click `+ Add parameter` and enter the parameter name `api-version` and value `2023-08-01-preview`.
   - In the textbox under `Body`, enter the message body in a format expected by the API. See [some examples here](https://learn.microsoft.com/en-us/azure/ai-services/openai/reference).

+++

Run the following cell to enter your API Key securely:

```{code-cell} ipython3
from ipywidgets import Password

api_key_widget = Password(description='API Key:')
api_key_widget
```

Create a client with the subscription information:

```{code-cell} ipython3
from openai import AzureOpenAI

# For Jupyternaut:
# Select Azure OpenAI::* provider
# to enter the following information
deployment_name = "cs-gpt-35-turbo-0301"
base_api_url = "https://apim-aoai-eas-dev02.azure-api.net/cs5483-2024"
api_version = "2023-08-01-preview"
api_key = api_key_widget.value # taken from the above widget

client = AzureOpenAI(
  azure_endpoint = base_api_url,
  api_version = api_version,
  api_key = api_key,
)
```

Create a chat completion:

```{code-cell} ipython3
stream = client.chat.completions.create(
  model = deployment_name,
  messages = [
    {"role": "user", "content": "What is data mining?"},
  ],
  temperature = 0,
  max_tokens = 75,
  stream = False
)

print(stream.choices[0].message.content)
```
