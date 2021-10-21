Installation
==============
If you are having trouble installing SimBA, please reach out to us on `gitter <https://gitter.im/SimBA-Resource/community>`_.

Requirements
^^^^^^^^^^^^^^

1. Python 3.6.8
2. Git
3. `FFmpeg <https://www.wikihow.com/Install-FFmpeg-on-Windows>`_
4. Windows OS

Installing on windows machine
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
1. Open up command prompt and type, ``pip install simba-uw-tf-dev``

Install SimBA using anaconda (does not support dlc)
^^^^^^^^^^^^^^^^^^^^^^^^
This will install the latest development version of SimBA.

1. Open up command prompt.
2. Make a new environment with python 3.6, ``conda create -n simbaenv python=3.6.10`` 
3. Make sure you activate your environment, ``conda activate simbaenv``
4. In the terminal type ``pip install simba-uw-tf-dev``
5. It will error out because of shapely. Uninstall shapely by ``pip uninstall shapely``
6. Then reinstall shapely with conda command: ``conda install -c conda-forge shapely``

Install SimBA with built in DeepLabCut (anaconda)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
This will install SimBA with built in deeplabcut. 

.. warning::
    We are are no longer supporting the legacy SimBAxTF branch, which required TensorFlow. To receive support, you must download the most up-to-date SimBA version (pip install simba-uw-tf-dev). If you are using the legacy SimBAxTF branch, please transition to the currently supported branch. If you require access to download the legacy branch, please contact us on Gitter for access. 

1. Open up command prompt.
2. Make a new environment with python 3.6, ``conda create -n simbaenv python=3.6.10`` 
3. Make sure you activate your environment, ``conda activate simbaenv``
4. Downgrade pip to version 19.0.1 by ``pip install pip==19.0.1``.
5. Install simba tensorflow version, ``pip install simba-uw-tf``
6. It will error out because of shapely. Uninstall shapely by ``pip uninstall shapely``
7. Then reinstall shapely with conda command: ``conda install -c conda-forge shapely``


Installing on MacOS
^^^^^^^^^^^^^^^^^^^^
Not recommended but it is possible.

Requirements
**************

- XCode installed
- Homebrew
- ffmpeg
- Python 3.6.10
- Anaconda

Installation process
********************

1. Create an environment for simba using anaconda terminal.

2. In the terminal type, ``pip install simba-uw-tf-dev``

3. Then, ``conda install -c anaconda python.app``

4. Then, ``conda install matplotlib``

5. Then, ``conda uninstall shapely``

6. Then, ``conda install -c conda-forge shapely``

7. Then, ``pip install shap``

8. Lastly, ``pip install h5py``

9. In the terminal, type in ``simba`` to test if it works.

