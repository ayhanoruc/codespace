# compile python from scratch
codespace_test

 1. `sudo apt-get update`
 
 2. `wget https://www.python.org/ftp/python/3.11.5/Python-3.11.5.tgz` # download from python.org

 3. `tar zxvf Python-3.11.5.tgz` # unzip

 4. `rm Python-3.11.5.tgz` # we dont need this now.

 5. `./configure --enable-optimizations`

 6. `make -j 2` # use how many cores you want to use. i got 2

 7. `sudo make altinstall`  

    if you are compiling and installing a custom version of Python, running sudo make altinstall will install this version of Python without overwriting the system's default Python interpreter. This can be useful to avoid potential conflicts with system tools and applications that rely on the default version of Python.  


 8. `find /workspaces/codespace/Python-<version> -type f -executable` # to find the executable python path

    `/home/codespace/Python-<version>/<python_executable_location>` mine is: /workspaces/codespace/Python-3.11.5/python 

9. `vim ~/.bashrc` # to add a python alias

   `alias python="/workspaces/codespace/Python-3.11.5/python"` # add this to the bottom of the file.

   `source ~/.bashrc` # update current shell session 
   
   `python` #now this should execute the python version we want

10. `python -m venv ~/.venv` 

    `vim ~/.bashrc`

    `source ~/.venv/bin/activate` # add this to the bottom of the file.

    `source ~/.bashrc`

    `which python` #this should return the latest python in .venv, now all the shells can run the python version we want, by default.

    The series of commands provided above are used to create and activate a Python virtual environment (venv) and ensure that the selected Python version within the virtual environment becomes the default

11. Create template for projects
    `touch requirements.txt`

    `touch Makefile`

    **Makefile template:**

    print:

        echo "working"

    install:

        pip install --upgrade -r requirements.txt

    test: 

        python -m pytest -vv test_hello.py

    format:

        black *.py

    lint:

        pylint disable=R,C hello.py


    all: install lint format test 

13. add * Python * to .gitignore

    `git status`

    `git add .`

    `git commit -m "project template created"`

    `git push -u origin main`
