.. _spinhx-conda:

==================================================
Conda ile Spinhx Kurulumu
==================================================

.. code-block:: bash

   bash Miniconda3-latest-Linux-x86_64.sh 

   Welcome to Miniconda3 py38_4.9.2

   In order to continue the installation process, please review the license agreement.
   Please, press ENTER to continue
   >>> 
   ===================================
   End User License Agreement - Anaconda Individual Edition
   ===================================

   Copyright 2015-2020, Anaconda, Inc.

   All rights reserved under the 3-clause BSD License:

   ....
   ....
   ....
   ....

   Last updated September 28, 2020

   Do you accept the license terms? [yes|no]
   [no] >>> yes

   Miniconda3 will now be installed into this location:
   /home/sevil/miniconda3

   - Press ENTER to confirm the location
   - Press CTRL-C to abort the installation
   - Or specify a different location below

   [/home/sevil/miniconda3] >>> /home/sevil/progs/miniconda3
   PREFIX=/home/sevil/progs/miniconda3
   Unpacking payload ...
   Collecting package metadata (current_repodata.json): done
   Solving environment: done

   ## Package Plan ##
   environment location: /home/sevil/progs/miniconda3

   added / updated specs:
    - _libgcc_mutex==0.1=main
    - brotlipy==0.7.0=py38h27cfd23_1003
    - ca-certificates==2020.10.14=0
    - certifi==2020.6.20=pyhd3eb1b0_3
    - cffi==1.14.3=py38h261ae71_2
    - chardet==3.0.4=py38h06a4308_1003
    - conda-package-handling==1.7.2=py38h03888b9_0
    - conda==4.9.2=py38h06a4308_0
    - cryptography==3.2.1=py38h3c74f83_1
    - idna==2.10=py_0
    - ld_impl_linux-64==2.33.1=h53a641e_7
    - libedit==3.1.20191231=h14c3975_1
    - libffi==3.3=he6710b0_2
    - libgcc-ng==9.1.0=hdf63c60_0
    - libstdcxx-ng==9.1.0=hdf63c60_0
    - ncurses==6.2=he6710b0_1
    - openssl==1.1.1h=h7b6447c_0
    - pip==20.2.4=py38h06a4308_0
    - pycosat==0.6.3=py38h7b6447c_1
    - pycparser==2.20=py_2
    - pyopenssl==19.1.0=pyhd3eb1b0_1
    - pysocks==1.7.1=py38h06a4308_0
    - python==3.8.5=h7579374_1
    - readline==8.0=h7b6447c_0
    - requests==2.24.0=py_0
    - ruamel_yaml==0.15.87=py38h7b6447c_1
    - setuptools==50.3.1=py38h06a4308_1
    - six==1.15.0=py38h06a4308_0
    - sqlite==3.33.0=h62c20be_0
    - tk==8.6.10=hbc83047_0
    - tqdm==4.51.0=pyhd3eb1b0_0
    - urllib3==1.25.11=py_0
    - wheel==0.35.1=pyhd3eb1b0_0
    - xz==5.2.5=h7b6447c_0
    - yaml==0.2.5=h7b6447c_0
    - zlib==1.2.11=h7b6447c_3


   The following NEW packages will be INSTALLED:

   _libgcc_mutex      pkgs/main/linux-64::_libgcc_mutex-0.1-main
   brotlipy           pkgs/main/linux-64::brotlipy-0.7.0-py38h27cfd23_1003
   ca-certificates    pkgs/main/linux-64::ca-certificates-2020.10.14-0
   certifi            pkgs/main/noarch::certifi-2020.6.20-pyhd3eb1b0_3
   cffi               pkgs/main/linux-64::cffi-1.14.3-py38h261ae71_2
   chardet            pkgs/main/linux-64::chardet-3.0.4-py38h06a4308_1003
   conda              pkgs/main/linux-64::conda-4.9.2-py38h06a4308_0
   conda-package-han~ pkgs/main/linux-64::conda-package-handling-1.7.2-py38h03888b9_0
   cryptography       pkgs/main/linux-64::cryptography-3.2.1-py38h3c74f83_1
   idna               pkgs/main/noarch::idna-2.10-py_0
   ld_impl_linux-64   pkgs/main/linux-64::ld_impl_linux-64-2.33.1-h53a641e_7
   libedit            pkgs/main/linux-64::libedit-3.1.20191231-h14c3975_1
   libffi             pkgs/main/linux-64::libffi-3.3-he6710b0_2
   libgcc-ng          pkgs/main/linux-64::libgcc-ng-9.1.0-hdf63c60_0
   libstdcxx-ng       pkgs/main/linux-64::libstdcxx-ng-9.1.0-hdf63c60_0
   ncurses            pkgs/main/linux-64::ncurses-6.2-he6710b0_1
   openssl            pkgs/main/linux-64::openssl-1.1.1h-h7b6447c_0
   pip                pkgs/main/linux-64::pip-20.2.4-py38h06a4308_0
   pycosat            pkgs/main/linux-64::pycosat-0.6.3-py38h7b6447c_1
   pycparser          pkgs/main/noarch::pycparser-2.20-py_2
   pyopenssl          pkgs/main/noarch::pyopenssl-19.1.0-pyhd3eb1b0_1
   pysocks            pkgs/main/linux-64::pysocks-1.7.1-py38h06a4308_0
   python             pkgs/main/linux-64::python-3.8.5-h7579374_1
   readline           pkgs/main/linux-64::readline-8.0-h7b6447c_0
   requests           pkgs/main/noarch::requests-2.24.0-py_0
   ruamel_yaml        pkgs/main/linux-64::ruamel_yaml-0.15.87-py38h7b6447c_1
   setuptools         pkgs/main/linux-64::setuptools-50.3.1-py38h06a4308_1
   six                pkgs/main/linux-64::six-1.15.0-py38h06a4308_0
   sqlite             pkgs/main/linux-64::sqlite-3.33.0-h62c20be_0
   tk                 pkgs/main/linux-64::tk-8.6.10-hbc83047_0
   tqdm               pkgs/main/noarch::tqdm-4.51.0-pyhd3eb1b0_0
   urllib3            pkgs/main/noarch::urllib3-1.25.11-py_0
   wheel              pkgs/main/noarch::wheel-0.35.1-pyhd3eb1b0_0
   xz                 pkgs/main/linux-64::xz-5.2.5-h7b6447c_0
   yaml               pkgs/main/linux-64::yaml-0.2.5-h7b6447c_0
   zlib               pkgs/main/linux-64::zlib-1.2.11-h7b6447c_3


   Preparing transaction: done
   Executing transaction: done
   installation finished.
   Do you wish the installer to initialize Miniconda3
   by running conda init? [yes|no]
   [no] >>> yes
   no change     /home/sevil/progs/miniconda3/condabin/conda
   no change     /home/sevil/progs/miniconda3/bin/conda
   no change     /home/sevil/progs/miniconda3/bin/conda-env
   no change     /home/sevil/progs/miniconda3/bin/activate
   no change     /home/sevil/progs/miniconda3/bin/deactivate
   no change     /home/sevil/progs/miniconda3/etc/profile.d/conda.sh
   no change     /home/sevil/progs/miniconda3/etc/fish/conf.d/conda.fish
   no change     /home/sevil/progs/miniconda3/shell/condabin/Conda.psm1
   no change     /home/sevil/progs/miniconda3/shell/condabin/conda-hook.ps1
   no change     /home/sevil/progs/miniconda3/lib/python3.8/site-packages/xontrib/conda.xsh
   no change     /home/sevil/progs/miniconda3/etc/profile.d/conda.csh
   modified      /home/sevil/.bashrc

   ==> For changes to take effect, close and re-open your current shell. <==

   If you'd prefer that conda's base environment not be activated on startup,
   set the auto_activate_base parameter to false:

   conda config --set auto_activate_base false

   Thank you for installing Miniconda3!

.. code-block:: bash

   conda create -n sphinx python=3

   Collecting package metadata (current_repodata.json): done
   Solving environment: done


   ==> WARNING: A newer version of conda exists. <==
   current version: 4.9.2
   latest version: 4.10.0

   Please update conda by running

    $ conda update -n base -c defaults conda

   ## Package Plan ##

   environment location: /home/sevil/progs/miniconda3/envs/sphinx

   added / updated specs:
    - python=3


   The following packages will be downloaded:

    package                    |            build
    ---------------------------|-----------------
    ca-certificates-2021.1.19  |       h06a4308_1         118 KB
    certifi-2020.12.5          |   py39h06a4308_0         140 KB
    openssl-1.1.1k             |       h27cfd23_0         2.5 MB
    pip-21.0.1                 |   py39h06a4308_0         1.8 MB
    python-3.9.2               |       hdb3f193_0        18.2 MB
    readline-8.1               |       h27cfd23_0         362 KB
    setuptools-52.0.0          |   py39h06a4308_0         724 KB
    sqlite-3.35.4              |       hdfb4753_0         981 KB
    tzdata-2020f               |       h52ac0ba_0         113 KB
    wheel-0.36.2               |     pyhd3eb1b0_0          33 KB
    ------------------------------------------------------------
                                           Total:        24.9 MB

   The following NEW packages will be INSTALLED:

   _libgcc_mutex      pkgs/main/linux-64::_libgcc_mutex-0.1-main
   ca-certificates    pkgs/main/linux-64::ca-certificates-2021.1.19-h06a4308_1
   certifi            pkgs/main/linux-64::certifi-2020.12.5-py39h06a4308_0
   ld_impl_linux-64   pkgs/main/linux-64::ld_impl_linux-64-2.33.1-h53a641e_7
   libffi             pkgs/main/linux-64::libffi-3.3-he6710b0_2
   libgcc-ng          pkgs/main/linux-64::libgcc-ng-9.1.0-hdf63c60_0
   libstdcxx-ng       pkgs/main/linux-64::libstdcxx-ng-9.1.0-hdf63c60_0
   ncurses            pkgs/main/linux-64::ncurses-6.2-he6710b0_1
   openssl            pkgs/main/linux-64::openssl-1.1.1k-h27cfd23_0
   pip                pkgs/main/linux-64::pip-21.0.1-py39h06a4308_0
   python             pkgs/main/linux-64::python-3.9.2-hdb3f193_0
   readline           pkgs/main/linux-64::readline-8.1-h27cfd23_0
   setuptools         pkgs/main/linux-64::setuptools-52.0.0-py39h06a4308_0
   sqlite             pkgs/main/linux-64::sqlite-3.35.4-hdfb4753_0
   tk                 pkgs/main/linux-64::tk-8.6.10-hbc83047_0
   tzdata             pkgs/main/noarch::tzdata-2020f-h52ac0ba_0
   wheel              pkgs/main/noarch::wheel-0.36.2-pyhd3eb1b0_0
   xz                 pkgs/main/linux-64::xz-5.2.5-h7b6447c_0
   zlib               pkgs/main/linux-64::zlib-1.2.11-h7b6447c_3


   Proceed ([y]/n)? y


   Downloading and Extracting Packages
   wheel-0.36.2         | 33 KB     | ######################################################################################## | 100%
   ca-certificates-2021 | 118 KB    | ######################################################################################## | 100%
   openssl-1.1.1k       | 2.5 MB    | ######################################################################################## | 100%
   sqlite-3.35.4        | 981 KB    | ######################################################################################## | 100%
   readline-8.1         | 362 KB    | ######################################################################################## | 100%
   setuptools-52.0.0    | 724 KB    | ######################################################################################## | 100%
   pip-21.0.1           | 1.8 MB    | ######################################################################################## | 100%
   python-3.9.2         | 18.2 MB   | ######################################################################################## | 100%
   tzdata-2020f         | 113 KB    | ######################################################################################## | 100%
   certifi-2020.12.5    | 140 KB    | ######################################################################################## | 100%
   Preparing transaction: done
   Verifying transaction: done
   Executing transaction: done
   #
   # To activate this environment, use
   #
   #     $ conda activate sphinx
   #
   # To deactivate an active environment, use
   #
   #     $ conda deactivate

