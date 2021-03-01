.. _lammps_personal:

===================================================
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

Sizler için Linux tabanlı bir “Docker Container” oluşturduk. Bu container eğitim için gerekli paketleri ile LAMMPS’ı ve bazı yardımcı grafik arayüzleri içermektedir.  Bu container’i çalıştırınca, internet tarayıcınız (örn. Firefox) ile linux sisteme erişebilir, ve LAMMPS’ı kullanabilirsiniz. Windows, Linux, ve macOS işletim sistemleri ile uyumludur.   


* Linux işletim sistemi için Docker kurulumu ile ilgili yönergeler için lütfen linkteki web sayfasını ziyaret ediniz:

  `Linux’a Docker nasıl kurulur? <https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04>`_

* Windows işletim sistemi için Docker kurulumu ile ilgili yönergeler için lütfen linkteki web sayfasını ziyaret ediniz:

  `Windows’a Docker nasıl kurulur? <https://hub.docker.com/editions/community/docker-ce-desktop-windows>`_

* MacOS işletim sistemi için Docker kurulumu ile ilgili yönergeler için lütfen linkteki web sayfasını ziyaret ediniz:

 `MacOS’a Docker nasıl kurulur? <https://hub.docker.com/editions/community/docker-ce-desktop-mac>`_

* `Diğer işletim sistemlerine Docker kurulumu ile ilgili bilgilere ulaşmak için tıklayınız <https://hub.docker.com/search?q=&type=edition&offering=community>`_

Docker programı düzgün bir şekilde kurulduktan sonra Docker’ı kullanmaya başlayabilirsiniz. Daha fazlasını öğrenmek isterseniz bazı yararlı öğretici yönergelere bakabilirsiniz. Bu uygulama kapsamında Docker’ı çalıştırmanız için sadece çok temel komutlara ihtiyacınız olacak.

* Docker’ı Windows işletim sistemine kurmak, Ubuntu veya MacOS işletim sistemine kıyasla biraz daha karmaşıktır.

  Windows işletim sistemini kullanıyorsanız, docker ile bir terminalin nasıl kullanılacağına dair bir eğitim videosu izlemek için aşağıdaki linki takip edebilirsiniz:

  https://www.youtube.com/watch?v=_9AWYlt86B8

  Docker'ı Windows üzerinde çalıştırmak, kendi makinenizin BIOS'unda sanallaştırmayı açmayı zorunlu kılar. Bunu nasıl yapacağınızı aşağıdaki linkten okuyabilirsiniz:

  https://bce.berkeley.edu/enabling-virtualization-in-your-pc-bios.html

  Ücretsiz olarak dağıtımı olan “Linux için Windows Subsytem (WSL2)”, Windows Home sürümünde mutlaka gereklidir ve Windows Pro sürümünde kesinlikle önerilmektedir. Windows Pro'da WSL2 olmadan da ilerleyebiliriniz, ancak bu önerilen bir çözüm değildir. Docker, neredeyse her şeyi sizin için yükler, ancak gerekli Linux Kernel’ini aşağıdaki linkten, Microsoft'tan indirmeniz gerekir.

  https://docs.microsoft.com/en-us/windows/wsl/install-win10#step-4---download-the-linux-kernel-update-package

* İlgili kurulumlar yapıldıktan ve Docker programı başlatıldıktan sonra komut istemine gidin ve docker'ı çalıştırın::

   docker run -p 6080:80 -v /dev/shm:/dev/shm obminator/lammps_playground

LAMMPS Playground'a erişebilmek için bilgisayarınızda Docker güvenlik duvarı erişimine izin verdiğinizden emin olun.

.. image:: files/docker-firewall.png

* İndirme işlemi tamamlandığında, çalışan görüntüye erişmek için web tarayıcınızdan 

   http://127.0.0.1:6080/ 

adresine gidebilirsiniz.

  (eğer kullandığınız işletim sistemi tarafından istenirse, makineniz içinde engelsiz iletişim için güvenlik duvarlarına izin verin (bu genellikle varsayılandır)).

* http://127.0.0.1:6080/ bağlantısını desteklenen bir web tarayıcısında açmak sizi Ubuntu masaüstüne götürür.

.. image:: files/docker-desktop.png

* Görevlerinizin çoğu LXTerminal'i kullanacaktır. Masaüstü kısayoluna çift tıklayabilir veya sol alttaki uygulamalar menüsüne gidip orada terminal uygulamasını bulabilirsiniz.

* Ayrıca ilgili paket kurulumu içerisine hazır olarak jmol, ovito ve gnuplot programları eklenmiş durumdadır. Bunlar LAMMPS sonuçlarını görselleştirmek için kullanabileceğiniz programlardır.

* LAMMPS kaynak kodu ve örnekler sırasıyla lammps-stable ve lammps-stable/examples dizinleri altındadır.

Docker İle İlgili Ayrıntılı Bilgiler
-------------------------------------

Bazı Faydalı Docker Komutları
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

docker images : 
   Çalıştırılmaya hazır olan paketi listeler. Disk alanı sorununuz varsa bazı görüntüleri kaldırabilirsiniz. Önceki adımı yaptıysanız obminator/lammps_playground’u görebiliyor olmanız lazım. Eğer göremiyorsanız aşağıdaki komutu çalıştırmanız gerekmektedir::

    docker pull obminator/lammps_playground

docker pull DOCKER_IMAGE: 
  Belirttiğiniz DOCKER_IMAGE imaj dosyasını bilgisaayrınıza indirir. Ve ilgili imaj dosyası  mevcut imajlar kısmında yer alır.

docker ps -l : 
  Çalışan (yakın zamanda çalıştırılmış olan) Docker imajlarını listeler. İlgili imajları “CONTAINER ID” bilgisini kullanarak kontrol edebilirsiniz.

docker stop CONTAINER_ID : 
  İlgili “CONTAINER ID” etiketine sahip imajını çalışmasını durdurur.

docker rm CONTAINER ID : 
  İlgili “CONTAINER ID” etiketine sahip imajı listeden siler.

docker run -p 6080:80 obminator/lammps_playground : 

Bu komut aşağıdaki işlemi gerçekleştirir:

   1. Yerel imajlar arasında obminator/lammps_playground imajını arar. Yerel kopya yoksa, görüntüyü docker hub'dan indirir (Uyarı! İmaj görüntüsü > 5 Gb!).

   2. İmaj dosyasını çalıştırır ve imajın 80 numaralı bağlantı noktasını yerel makinenin 6080'ine eşler (VNC bağlantınız bu bağlantı noktası üzerinden olacaktır)

docker image rm DOCKER_IMAGE : 
  Yerel imaj dosyasını diskinizden kaldırarak disk alanını boşaltır. İmaj dosyasını tekrar çalıştırmak isterseniz, sıfırdan bir kez daha indirmeniz gerekecek.


