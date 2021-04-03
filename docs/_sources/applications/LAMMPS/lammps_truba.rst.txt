.. _lammps_truba:

==========================
TRUBA'da LAMMPS Kurulumu
==========================
TRUBA sisteminde kurulu olan programlar hakkındaki bilgiye

.. code-block:: bash

   module available

komutu ile ulaşabilirsiniz.

.. code-block:: bash

   module list

komutu ile kullanıcınızda yüklenmiş programları listeleyebilirsiniz. Herhangi bir çakışma olmaması açısından öncelikle:

.. code-block:: bash

   module purge

komutu ile  yüklü olan tüm modül dosyalarını kaldırmanız önerilmektedir.

Aşağıdaki komutları kullanarak Intel Parallel Studio'nun güncel versiyonunu load ediniz:

.. code-block:: bash

   module load centos7.3/comp/intel/PS2018-update2
   module load centos7.3/lib/openmpi/4.0.1-intel-PS2018

LAMMPS modulü, LAMMPS kullanım kitapçığındaki standart `CMake prosedürünü <https://lammps.sandia.gov/doc/Build_cmake.html>`_ izler. Kurulumu CMake ile yapmak için ilgili modülü load ediniz:

.. code-block:: bash

   module load centos7.3/comp/cmake/3.18.0

LAMMPS için derleme ortamını hazırlayınız:

.. code-block:: bash

   git clone  -b stable https://github.com/lammps/lammps.git lammps-stable
   cd lammps-stable
   mkdir build-intel18-openmpi4
   cd build-intel18-openmpi4

C/C++ ve Fortran90 derleyicilerin tanımlamalarını yapınız:

.. code-block:: bash

   export CC=mpicc CXX=mpic++ FC=mpif90

``-D PKG_NAME=yes`` komutu ile kurulmasını istediğiniz paketleri belirtebilirsiniz. Paket ayrıntıları için LAMMPS kullanma kitapçığını inceleyebilirsiniz (https://lammps.sandia.gov/doc/Packages.html).

Örnek olarak aşağıdaki kurulum komutuna bazı kullanıcı paketleri eklenmiştir:

   .. code-block:: bash

    cmake ../cmake -D BUILD_MPI=on -D BLAS_LIBRARIES="-L${MKLROOT}/lib/intel64 -lmkl_intel_lp64 -lmkl_sequential -lmkl_core -lpthread -lm -ldl" -D LAPACK_LIBRARIES="-L${MKLROOT}/lib/intel64 -lmkl_intel_lp64 -lmkl_sequential -lmkl_core -lpthread -lm -ldl" -D PKG_BODY=yes -D PKG_CLASS2=yes -D PKG_DIPOLE=yes -D PKG_MANYBODY=yes -D PKG_MC=yes -D PKG_LATTE=yes -D PKG_MLIAP=yes -D PKG_SNAP=yes -D PKG_SPIN=yes -D PKG_PYTHON=yes -D PKG_USER-MOLFILE=yes -D PKG_MOLECULE=yes -D PKG_USER-PHONON=yes -D PKG_USER-REAXC=yes  -D PKG_KSPACE=yes -D PKG_USER-MEAMC=yes -D PKG_USER-PLUMED=yes -D PKG_USER-SMTBQ=yes -D PKG_USER-DIFFRACTION=yes -D FFT=MKL

.. note::

   Özellikle PLUMED ve MSCCG paketlerine hesaplamalarınız için ihtiyanız yoksa eğer cmake komutundan çıkartabilirsiniz. Eğer bu paketlere ihtiyacınız varsa Conda ile GSL paketini kurmanız gerekmektedir. Conda kurulumu için aşağıdaki linki ziyaret edebilirsiniz.
   https://docs.truba.gov.tr/GPU/deep-learning/virtual-env.html#ev-dizininize-anaconda-kurun

   Conda ile GSL paketini de aşağıdaki komut ile kurabilirsiniz:

   .. code-block:: bash

      conda install -c conda-forge gsl 

Daha sonrasında CMake ile build komutunu çalışarak LAMMPS’i derleyiniz:

.. code-block:: bash

   cmake --build .

Yukarıdaki kurulum adımları tamamlandığında bulunduğunuz ``build-intel18-openmpi4`` dizininde ``bin`` klasörü altında çalıştırılabilir ``lmp`` dosyası yer alacaktır.

==========================
TRUBA'da LAMMPS Kullanımı:
==========================

Kendi kullanıcınıza kurduğunuz LAMMPS programını TRUBA sisteminde çalıştırmak için örnek iş betiği dosyası aşağıdaki gibidir:

lammps_run.slurm
^^^^^^^^^^^^^^^^^^

.. code-block:: bash

  #!/bin/bash
  #SBATCH -p mid1
  #SBATCH -C barbun
  #SBATCH -A accountname
  #SBATCH -J lammps-test
  #SBATCH -N 1
  #SBATCH -n 20
  #SBATCH --time=03:00:00
  #SBATCH --output=slurm-%j.out
  #SBATCH --error=slurm-%j.err


  echo "SLURM_NODELIST $SLURM_NODELIST"
  echo "NUMBER OF CORES $SLURM_NTASKS"

  export OMP_NUM_THREADS=1
  
  module load centos7.3/comp/intel/PS2018-update2
  module load centos7.3/lib/openmpi/4.0.1-intel-PS2018

  LAMMPS_DIR=/truba/home/username/lammps-stable/build-intel18-openmpi4/bin

  mpirun  $LAMMPS_DIR/lmp  < in.lammpsinputfile > lammps-outputfile.out

  exit

Güncel LAMMPS versiyonu için benzer betik dosyasını ``/truba/sw/scripts`` klasörü altında bulabilirsiniz (lammps-4Feb21-openmpi-1.8.8-gcc.slurm). Çalıştığınız klasör içerisinde yukarıdaki betik dosyasını düzenleyip oluşturduktan sonra ::
  
   sbatch lammps_run.slurm

komutu ile TRUBA sistemine işinizi gönderebilirsiniz.

