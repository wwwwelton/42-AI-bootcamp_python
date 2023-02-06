## PISCINE PYTHON DJANGO
### D03 - PIP AND VIRTUALENV

##### PACKAGE MANAGER
```bash
# manual
pip3 help

# install package
pip3 install package-name

# remove package
pip3 uninstall package-name

# freeze / lock packages versions
pip freeze
pip freeze > requirements.txt

# install all packages from a requirements.txt
pip install -r requirements.txt

# remove all packages from a requirements.txt
pip uninstall -r requirements.txt -y

# remove all packages installed by pip
pip freeze | xargs pip uninstall -y
```

##### VIRTUAL ENVIRONMENT
Virtual environments in python can isolate packages and python version
```bash
# install virtualenv package
pip install virtualenv

# create new virtual env
virtualenv my_virtual_env

# activate virtual env
source my_virtual_env/bin/activate

# list installed packages to check if is correct
pip list

# install a package isolated
pip install package-name

# deactivate exit from virutal env
deactivate

# change virtual env python version
virtualenv -p path_to_python my_virtual_env

# install virtualenvwrapper
# virtualenvwrapper is a tool to easy manage virtual env in python
# docs https://virtualenvwrapper.readthedocs.io/en/latest/
pip install virtualenvwrapper

# create a new virtual env named pouet
mkvirtualenv pouet

# activate virtual env pouet
workon pouet
```

##### API
An API, or application programming interface, is a set of defined rules that enable different applications to communicate with each other.

```bash
# install requests package to make HTTP requests
pip install requests
```

Example of github API call using requests
```python
import requests

# Create an API request
url = 'https://api.github.com/search/repositories?q=language:python&sort=stars'
response = requests.get(url)
print("Status code: ", response.status_code)
# In a variable, save the API response.
response_dict = response.json()
# Evaluate the results.
print(response_dict.keys())
```
