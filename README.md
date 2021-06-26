The following are the steps for installing Python and using the Python virtual environment *virtualenv*.

A Python virtual environment contains a version of Python and the packages that are required for the application being developed. Virtual environments make it easy to have the environment that is needed for each project. There is more than one option for virtual environments for Python.

## Install Python

There is more than one way to install Python on macOS. The method used here is to install Python using the installer provided at https://www.python.org/downloads/

1. Download the latest Python.
2. Launch the installer by double-clicking on the Python .pkg file.
3. Complete the installation using the installer.
4. Remember the version of the Python that was installed.

Notes: 

* pip3, the package installer for Python, is installed with Python.
* Enter "which python3" at the command line in the Terminal to determine where Python is installed.
* Enter "python3 --version" at the command line in the Terminal to display the version.

## virtualenv and Installing virtualenv

Using *virtualenv* allows each project to have the version of Python and the required packages that are needed. You activate an environment, work on it, then deactivate it when you are done. The command prompt changes to let you know you are working on a virtual environment.

To install *virtualenv* enter the following at the command prompt in the Terminal:

> python3 -m pip install virtualenv

To test that *virtualenv* is installed and working, follow the steps to create a new project and make it a virtual environment.

### Creating a virtual environment using ```virtualenv```

A directory is the container for a project. To create a new virtual environment, create a directory for the project and execute the command for making it a virtual environment. If that works, it is installed.

I put my projects in ```~/Documents/spot```, so I create a directory inside the ```spot``` directory for the project.

Change to the directory where you want to create the new directory.

>cd ~/Documents/spot

Then, make the new directory.

>mkdir spotproject1

Make the new directory a virtual environment.

>python3 -m virtualenv spotproject1

When I do the above, I get the following.

>dale@p1:~/Documents/spot$ python3 -m virtualenv spotproject1

>dale@breeze spot % python3 -m virtualenv spotproject1
created virtual environment CPython3.9.5.final.0-64 in 685ms
  creator CPython3Posix(dest=/Users/dale/Documents/spot/spotproject1, clear=False, no_vcs_ignore=False, global=False)
  seeder FromAppData(download=False, pip=bundle, setuptools=bundle, wheel=bundle, via=copy, app_data_dir=/Users/dale/Library/Application Support/virtualenv)
    added seed packages: pip==21.1.2, setuptools==57.0.0, wheel==0.36.2
  activators BashActivator,CShellActivator,FishActivator,PowerShellActivator,PythonActivator,XonshActivator

We can now take a look at what was created in the directory. Change to the directory and then use ```ls``` to display its contents.

>dale@breeze spotproject1 % ls

```bin  lib  pyvenv.cfg```

The directories ```bin``` and ```lib``` were created along with the ```pyvenv.cfg``` file. 

To list the contents of ```bin``` do the following. It contains the programs that are needed including ```python3.9```, ```pip``` and ```wheel```. The ```activate``` program is used to activate the virtual environment.

>dale@breeze spotproject1 % cd bin
>dale@breeze bin % ls -al

```
total 112
drwxr-xr-x  19 dale  staff   608 Jun 25 20:06 .
drwxr-xr-x   6 dale  staff   192 Jun 25 20:06 ..
-rw-r--r--   1 dale  staff  2155 Jun 25 20:06 activate
-rw-r--r--   1 dale  staff  1447 Jun 25 20:06 activate.csh
-rw-r--r--   1 dale  staff  3078 Jun 25 20:06 activate.fish
-rw-r--r--   1 dale  staff  1751 Jun 25 20:06 activate.ps1
-rw-r--r--   1 dale  staff  1169 Jun 25 20:06 activate.xsh
-rw-r--r--   1 dale  staff  1199 Jun 25 20:06 activate_this.py
-rwxr-xr-x   1 dale  staff   255 Jun 25 20:06 pip
-rwxr-xr-x   1 dale  staff   255 Jun 25 20:06 pip-3.9
-rwxr-xr-x   1 dale  staff   255 Jun 25 20:06 pip3
-rwxr-xr-x   1 dale  staff   255 Jun 25 20:06 pip3.9
lrwxr-xr-x   1 dale  staff    61 Jun 25 20:06 python -> /Library/Frameworks/Python.framework/Versions/3.9/bin/python3
lrwxr-xr-x   1 dale  staff     6 Jun 25 20:06 python3 -> python
lrwxr-xr-x   1 dale  staff     6 Jun 25 20:06 python3.9 -> python
-rwxr-xr-x   1 dale  staff   242 Jun 25 20:06 wheel
-rwxr-xr-x   1 dale  staff   242 Jun 25 20:06 wheel-3.9
-rwxr-xr-x   1 dale  staff   242 Jun 25 20:06 wheel3
-rwxr-xr-x   1 dale  staff   242 Jun 25 20:06 wheel3.9
```

The directory ```lib``` is where the Python packages are held. When pip is used to install a package in an activated virtual environment, the files are placed in a directrory in ```lib```.

### Using a Virtual Environment

To use a virtual environment:

1. Activate the virtual environment.
2. Do work in the activated virtual environment.
3. Deactivate the virtual environment.

To activate a virtual environment, do the following. The path to ```activate``` needs to be based on the current working directory, the name of your project/virtual environment directory, and the path to the ```activate``` program inside the project directory. The following assumes I am currently in the ```~/Documents/spot``` folder that holds ```spotproject1``` and ```activate``` is inside ```bin```.

>source spotproject1/bin/activate

When the virtual environment is activated, the command prompt changes to the name of the directory for the environment. The following shows what happens when I run the command to activate.

>dale@breeze spot % source spotproject1/bin/activate

```(spotproject1) dale@breeze spot % ```

The above indicates that the ```spotproject1``` virtual environment has been activated.

While in the activated state, work on the project including installing packages that are placed in ```lib``` in the directory for the virtual environment.

To deactivate the virtual environment, do the following.

>deactivate

When I run deactivate, I get the following.

>(spotproject1) dale@breeze spot % deactivate

>dale@breeze spot % 

Notice that ```(spotproject1)``` is removed from the prompt after deactivating.

### Installing the Spot and other packages int the virtual environment

```pip``` is used to install packages in the virtual environment. Activate the virtual environment (see above) before doing any package management.

First make sure your virtual environment is activated. It is activated if the project directory is displayed in the prompt.

Use pip to install Python packages using:

>python3 -m pip install --upgrade <package_name>

For example, to install the matplotlib package use:

>python3 -m pip install --upgrade matplotlib

The following is what I get when I perform the installation.

>(spotproject1) dale@breeze spotproject1 % python3 -m pip install --upgrade matplotlib

```
Collecting matplotlib
  Using cached matplotlib-3.4.2-cp39-cp39-macosx_10_9_x86_64.whl (7.2 MB)
Collecting kiwisolver>=1.0.1
  Using cached kiwisolver-1.3.1-cp39-cp39-macosx_10_9_x86_64.whl (61 kB)
Collecting numpy>=1.16
  Downloading numpy-1.21.0-cp39-cp39-macosx_10_9_x86_64.whl (16.9 MB)
     |████████████████████████████████| 16.9 MB 4.2 MB/s 
Collecting python-dateutil>=2.7
  Using cached python_dateutil-2.8.1-py2.py3-none-any.whl (227 kB)
Collecting cycler>=0.10
  Using cached cycler-0.10.0-py2.py3-none-any.whl (6.5 kB)
Collecting pillow>=6.2.0
  Downloading Pillow-8.2.0-cp39-cp39-macosx_10_10_x86_64.whl (2.8 MB)
     |████████████████████████████████| 2.8 MB 107.5 MB/s 
Collecting pyparsing>=2.2.1
  Using cached pyparsing-2.4.7-py2.py3-none-any.whl (67 kB)
Collecting six
  Using cached six-1.16.0-py2.py3-none-any.whl (11 kB)
Installing collected packages: six, python-dateutil, pyparsing, pillow, numpy, kiwisolver, cycler, matplotlib
Successfully installed cycler-0.10.0 kiwisolver-1.3.1 matplotlib-3.4.2 numpy-1.21.0 pillow-8.2.0 pyparsing-2.4.7 python-dateutil-2.8.1 six-1.16.0
```

The list of packages that are installed can be displayed using:

>pip list

From the ```spotproject1``` directory, use the following to run ```pip``` located in the ```bin``` directory and have it list the installed packages.

>(spotproject1) dale@breeze spotproject1 % ./bin/pip list

```
Package         Version
--------------- -------
cycler          0.10.0
kiwisolver      1.3.1
matplotlib      3.4.2
numpy           1.21.0
Pillow          8.2.0
pip             21.1.2
pyparsing       2.4.7
python-dateutil 2.8.1
setuptools      57.0.0
six             1.16.0
wheel           0.36.2
```

### Writing and running Python programs in the virtual environment

To write and run Python program in the virtual environment do the following.

1. Activate the virtual environment.
2. Write/place your Python code in the directory for the virtual environment.
3. Run using: ```python3 <program_file.py>```
   
When you are done, deactivate the virtual environment.









