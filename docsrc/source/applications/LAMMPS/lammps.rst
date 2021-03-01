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

1- Kendi Bilgisayarınıza LAMMPS kurmak
=======================================

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

2- LAMMPS’ın İndirilmesi
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

3- LAMMPS'in Derlenmesi
^^^^^^^^^^^^^^^^^^^^^^^^
LAMMPS’ın derlenmesi için iki yöntem mevcuttur. Burada CMAKE yöntemini kullanacağız. Detaylara ``https://lammps.sandia.gov/doc/Build_cmake.html`` adresinden ulaşabilirsiniz.

* LAMMPS kodunu açtığınız klasörün içine gidin (örneğin ``cd lammps-stable``), burada build klasörü oluşturun, ve içine gidin::

  $ mkdir build 

  $ cd build

* Bulunduğunuz yer lammps_stable/build olmalı.

* Aşağıdaki komut ile cmake’i çalıştırın. Cmake sisteminizi tarayarak gerekli ayarları yapacaktır. Ekteki komutla ReaxFF dahil birkaç yaygın paket kurulmaktadır::

  $ cmake ../cmake -D PKG_BODY=yes -D PKG_CLASS2=yes -D PKG_DIPOLE=yes -D PKG_MANYBODY=yes -D PKG_USER-REAXC=yes -D PKG_USER-MEAMC=yes

* cmake size sisteminizde bulduğu özellikleri, ve LAMMPS’a dahil olacak paketleri özet geçecektir. Lütfen USER-REAXC paketinin açık olduğundan emin olun::

  -- Enabled packages: BODY;CLASS2;DIPOLE;MANYBODY;USER-MEAMC;USER-REAXC

* Aşağıdaki komut ile LAMMPS’ı derleyebilirsiniz (sondaki noktaya dikkat ediniz,  ve build klasörünün içinde olduğunuzdan emin olunuz)::

  $ cmake --build . 

Windows 10 için:
----------------------------------------------------

Window subsystem for Linux (WSL)’yi etkinleştiriniz ve Ubuntu kurunuz. Daha sonra yukarıdaki Ubuntu talimatlarını uygulayınız. 

* WSL kurulumu için  ``https://docs.microsoft.com/tr-tr/windows/wsl/install-win10`` adresinden yardım alabilirsiniz. 

2- Docker ile Hazır LAMMPS Kurulumu
====================================


