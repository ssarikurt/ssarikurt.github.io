.. _lammps_truba:

==========================
TRUBA'da LAMMPS Kullanımı:
==========================

TRUBA sisteminde kurulu olan programlar hakkındaki bilgiye::

   module available

komutu ile ulaşabilirsiniz. 
  

TRUBA sisteminde LAMMPS çalıştırmak için örnek ıs betiği dosyası aşağıdaki gibidir:

lammps_run.slurm
^^^^^^^^^^^^^^^^^^

.. code-block:: bash

  #!/bin/bash
  #SBATCH -p barbun
  #SBATCH -A accountname
  #SBATCH -J lammps-test
  #SBATCH -N 1
  #SBATCH -n 20

  echo "SLURM_NODELIST $SLURM_NODELIST"
  echo "NUMBER OF CORES $SLURM_NTASKS"

  export OMP_NUM_THREADS=1
  
  module load centos7.3/lib/openmpi/1.8.8-gcc-4.8.5
  module load centos7.3/comp/gcc/9.2

  export OMP_NUM_THREADS=1

  LAMMPS_DIR=/truba/sw/centos7.3/app/lammps/4Feb21-openmpi-1.8.8-gcc-4.8.5/bin

  mpirun  $LAMMPS_DIR/lmp_mpi  < in.lammpsinputfile

  exit


Çalıştığınız klasör içerisinde yukarıdaki betik dosyasını oluşturduktan sonra ::
  
   sbatch lammps_run.slurm

komutu ile TRUBA sistemine işinizi gönderebilirsiniz.

