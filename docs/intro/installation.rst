Installation
==============

Requirements
^^^^^^^^^^^^^^

1. Python 3.6
2. Git
3. FFmpeg
4. Windows OS

Install using anaconda
^^^^^^^^^^^^^^^^^^^^^^^^
1. Make a new environment with python 3.6
2. In the terminal type ``pip install simba-uw-tf``
3. It will error out because of shapely. Uninstall shapely by ``pip uninstall shapely``
4. Then reinstall shapely with conda command: ``conda install -c conda-forge shapely``


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

2. In the terminal type, ``pip install simba-uw-no-tf``

3. Then, ``conda install -c anaconda python.app``

4. Then, ``conda install matplotlib``

5. Then, ``conda uninstall shapely``

6. Then, ``conda install -c conda-forge shapely``

7. Then, ``pip install shap``

8. Lastly, ``pip install h5py``

9. In the terminal, type in ``simba`` to test if it works.

