.. _lammps:

==================================================================
LAMMPS (Large-scale Atomic/Molecular Massively Parallel Simulator)
==================================================================

Genel Bilgiler
==============

LAMMPS, açık kaynak kodlu moleküler dinamik simülasyon programıdır.

Çevrimiçi Bilgiler
-------------------

* Web Sayfası: https://lammps.sandia.gov/
* Program Kitapçığı :  https://lammps.sandia.gov/doc/Manual.html
* Örnek Eğitim Dosyaları:  https://lammps.sandia.gov/tutorials.html

Kendi Bilgisayarınıza LAMMPS Yükleme ve Çalıştırma
===================================================

Debian/Ubuntu Linux için:
----------------------------------------------------

1- Ön Hazırlık
^^^^^^^^^^^^^^

Sisteminizde bazı paketlerin kurulu olması gerekmektedir. Bunları

.. code-block:: bash
 
    $ sudo apt install <paket adları>

ile kurabilirsiniz. Gerekli paket listesi aşağıdaki gibidir:

.. code-block:: bash

    gcc gfortran cmake autoconf automake autotools-dev libopenmpi-dev libopenmpi3  mpi-default-bin openmpi-bin openmpi-common libopenblas-base libopenblas-dev

2- LAMMPS’ın indirilmesi
^^^^^^^^^^^^^^^^^^^^^^^^^

LAMMPS’ın kaynak kodunun indirilmesi için iki yöntem mevcuttur. Detaylara

- https://lammps.sandia.gov/doc/Install_tarball.html

- https://lammps.sandia.gov/doc/Install_git.html 

adreslerinden ulaşabilirsiniz.


* https://lammps.sandia.gov/download.html sayfasından LAMMPS Stable seçeneğini seçin, ve “Download now” tuşuna basın. Bilgisayarınıza indirdiğiniz dosyayı::

  $ tar zxvf lammps*.tar.gz 

komutu ile açabilirsiniz.

* veya  sisteminizde git yüklü ise::

  $ git clone -b stable https://github.com/lammps/lammps.git lammps-stable

ile lammps-stable klasörüne lammps’ı klonlayabilirsiniz.



