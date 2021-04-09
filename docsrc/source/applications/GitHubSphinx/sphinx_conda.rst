.. _spinhx_conda:


1) İzole edilmiş yerel kurulum (xConda ile)
============================================

Conda ile sanal ortam yaratarak, bilgisayarınızdaki mevcut çevre değişkenlerine dokunmadan, kurulum gerçekleştirebilirsiniz. *İzole edilmemiş* yerel kurulum sırasında farklı uygulamalarınız için çakışma problemleri ortaya çıkabilir. **İzole edilmiş** yerel kurulum sayesinde ortaya çıkabilecek çakışma problemlerinden de kurtulmuş olursunuz.

Öncelikle, eğer kurulu değilse, ev dizininize Conda kurmanız gerekmektedir. Conda kurulumu için aşağıdaki linkleri de inceleyebilirsiniz:

`TRUBA Conda Kurulum Dökümantasyonu <https://docs.truba.gov.tr/how-to-guides/GPU/deep-learning/virtual-env.html#ev-dizininize-anaconda-kurun>`_

`Conda Web Sayfası <https://docs.conda.io/projects/continuumio-conda/en/latest/user-guide/install/index.html>`_

Aşağıda örnek olarak Linux/Ubuntu işletim sistemi üzerinde ``miniconda`` kurulumu anlatılmıştır. Terminalden Miniconda'nın mevcut güncel sürümünü indirip çalıştırınız.

.. code-block::

   wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh 
   bash Miniconda3-latest-Linux-x86_64.sh

.. note::

   Kurulum işlemi tamamlandıktan sonra çalıştırılabilir ``Miniconda3-latest-Linux-x86_64.sh`` dosyasını silebilirsiniz. Kurulumdan sonra Conda'nın aktif olabilmesi için terminalinizi kapatıp yeniden açmanız gerekmektedir.

Conda'nın nasıl kulanılacağı ile ilgili `ayrıntılı bilgiye web sayfasından ulaşabilirsiniz <https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#activating-an-environment>`_.

.. code-block::

   conda create -n sphinx python=3

Komutu ile ``spinhx`` isimli (veya farklı bir isimde) çevre değişkeni oluşturunuz.

.. code-block::

   conda activate sphinx

Komutu ile ``sphinx`` adını verdiğiniz çevre değişkenini aktif hale getiriniz. Çevre değişkenini aktif hale getirdikten sonra terminalinizde parantez içerisinde çevre değişkeninizin ismi yer alacaktır:

.. code-block::

   (sphinx) $

.. note::

   İlgili çevre değişkenini aktif durumdan çekmek için ``conda deactive`` komutunu kullanmanız yeterli olacaktır.
   
