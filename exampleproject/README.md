## Django Wagtail app

Current build:
```
Python: [3.9]
Wagtail: [2.13]
```

### Prereqs

- Python 3.9+
- [pipenv](https://pipenv.pypa.io/en/latest/) (`pip install --user pipenv` -OR- `curl https://raw.githubusercontent.com/pypa/pipenv/master/get-pipenv.py | python`)

### Setup

In root of the project (where `Pipfile` is) run:

```
pipenv install --dev
```
(Leave the `--dev` out for production)

Now, activate the virtual environment:

```
pipenv shell
```

Place yourself inside the `/app/` directory (where `manage.py` is):

```
cd app
```

Run migrations, which will initialise a SQLite3 database as well if not present, and create an admin user:

```
python manage.py migrate
python manage.py createsuperuser
```
