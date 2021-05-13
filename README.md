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
I then needed to run 'pip install wagtail'  again.
[barry] - The next command will create the wagtail project nebula:
$ cd exampleproject
$ wagtail start app
[barry][wagtail] - Install projects dependencies
$ cd app
$ pip install -r requirements.txt
[DJ] - ERROR: Could not open requirements file: [Errno 2] No such file or directory: 'requirement.txt'
[barry][wagtail] - Create the project database
$ python3 manage.py migrate
[barry] - Create admin user:
$ python3 manage.py createsuperuser
[DJ] - admin - 'letmein1!'
[barry] - Start the server:
$ python3 manage.py runserver
You can now access you installation at:
http://127.0.0.1:8000
[DJ] - Saving progress to github


STEP 2 -

In the last project by Richard and Lorenzo https://github.com/flowmoco/vodafone-sales-wagtail.git we have the a Vue frontend, with Wagtail running headless.  So let's have a look at how to do that .

https://www.youtube.com/watch?v=xUWd3o6z2bk
and the instructions and code can be found here https://gist.github.com/tomdyson/abf1e973db4dcd50b388816f8c20adb0

[1] So that we can display this working they make a 'news' app.
$python3 manage.py startapp news
[2] In settings/base.py we need to add 'news' to  INSTALLED_APPS list
[3] in news/models.py add the fields and data we need.
[4]
$python3 manage.py makemigrations
$python3 manage.py migrate
$python3 manage.py runserver
[5] So we should now be able to goto our Admin page and a page with the Child template of 'news'

[6] Create a new folder called 'frontend' the sits outside of our 'exampleproject' folder
[DJ] Note: in this demonstration they use 'backend' as the Wagtail project folder, this seems to make sense to me and could be argued for best practice in our future projects.

[7] Add the file app/api.py
[8] Add the following to urls.py
{code}
path('api/v2/', api_router.urls),
...
    path('api/v2/', api_router.urls),
    {/code}
[9] Add "rest_framework" to the INSTALLED_APPS list in settings/base.py
http://127.0.0.1:8000/api/v2/pages/?type=news.NewsPage will now show your endpoints.


[DJ] - at this point I'm going to jump out of this and create an vue.js installation in Frontend.
In my opinion Vue.js should include the following
Axios
Vue-router
Vuetify
Vuex

DEV DEPS
cli-plugin-babel
cli-plugin-router
cli-plugin-vuex
vue/cli-service
Sass
Sass-loader
vue-cli-plugin-vuetify
vue-template-compiler
vuetify-loader

Lets start the Vue.js installation at . https://flowmoco.atlassian.net/wiki/spaces/TB/pages/1973846026/Firebase%2Band%2BVue%2B-

[1] $npm install -f @vue/cli
[2] $vue create frontend
[3] Template [Vue2] node-sass, babel, router, vuex, eslint, unit-mocha
[4] here we can cd into the folder and 'npm run serve.
[5] We can now see a vue site at

http://localhost:8081/

Next up lets go back to these instructions

https://www.youtube.com/watch?v=xUWd3o6z2bk
and the instructions and code can be found here https://gist.github.com/tomdyson/abf1e973db4dcd50b388816f8c20adb0

[DJ] In our installation we have the {{ msg }} being out put in src/components/HelloWorld.vue

And the wording in that message set in /src/views/Home.vue

[1] The HelloWorld.vue here is the child page.  So I've removed that and the call to HelloWorld.vue and replaced with code to pull from the backend API
[2] We'll need to import axios as well.
[3] At this stage we only get our header outputting and nothing from Django.
[error] XMLHttpRequest at XX has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource.
[4] Going back into the tutorial above we can use the project 'django-cors-headers' to sort this.
https://github.com/adamchainz/django-cors-headers
[5] cd back into the backend folder 'exampleproject/app' and
$pip install django-cors-headers

[error] this is as far as I got and had issue with installing this.