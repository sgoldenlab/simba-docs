Installation
==============

Requirements
^^^^^^^^^^^^^^

1. Python 3.6.8
2. Git
3. FFmpeg
4. Windows OS

Installing on windows machine
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
1. Open up command prompt and type, ``pip install simba-uw-tf-dev``

Install using anaconda
^^^^^^^^^^^^^^^^^^^^^^^^
1. Open up command prompt.
2. Make a new environment with python 3.6, ``conda create -n simbaenv python=3.6.10`` 
3. Make sure you activate your environment, ``conda activate simbaenv``
4. In the terminal type ``pip install simba-uw-tf-dev``
5. It will error out because of shapely. Uninstall shapely by ``pip uninstall shapely``
6. Then reinstall shapely with conda command: ``conda install -c conda-forge shapely``


Installing on MacOS
^^^^^^^^^^^^^^^^^^^^
Not recommended but it is possible.

Requirements
**************

- XCode installed
- Homebrew
- ffmpeg
- Python 3.6
- Anaconda

Installation process
********************

1. Create an environment for simba using anaconda terminal.

2. In the terminal type, ``pip install simba-uw-tf``

3. Then, ``conda install -c anaconda python.app``

4. Then, ``conda install matplotlib``

5. Then, ``conda uninstall shapely``

6. Then, ``conda install -c conda-forge shapely``

7. Then, ``pip install shap``

8. Lastly, ``pip install h5py``

9. In the terminal, type in ``simba`` to test if it works.

