# wagtail-base-May-2021
This is an initial set to list the current best procedures for a new Wagtail site.


Let's start by following the instructions for installation from https://docs.wagtail.io/en/stable/getting_started/tutorial.html
As well as comparing the installation instructions we have ( written by Barry Poore )

Barrys Wagtail installation https://flowmoco.atlassian.net/wiki/spaces/FLOW/pages/901742621/Wagtail+CMS+for+Django

[wagtail] - Check you have an appropriate version of Python
$ python3 --version
[barry] - Open a terminal and cd to where you want your installation.
[barry][wagtail] - Create a Virtual environment for your project.
python3 -m venv mysite/env
$ source mysite/env/bin/activate
[Dj] in this example I've used 'exampleproject' for the project name.
[Barry] The above will create the environment including a directory called nebula, cd into exampleproject
[barry][wagtail] -Use pip, which is packaged with Python, to install Wagtail and its dependencies:
$ pip install wagtail
[DJ] -  Running setup.py install for Pillow ... error
It was also recommended that I'd upgrade my Pip
$ pip install --upgrade pip
That part ran without errors.
[barry] - The next command will create the wagtail project nebula:
$ wagtail start app
[barry][wagtail] - Install projects dependencies
$ cd app
$ pip install -r requirements.txt
[DJ] - ERROR: Could not open requirements file: [Errno 2] No such file or directory: 'requirement.txt'
[barry][wagtail] - Create the project database
$ python manage.py migrate
[DJ] - ModuleNotFoundError: No module named 'wagtail'
