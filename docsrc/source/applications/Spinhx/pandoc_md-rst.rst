.. _pandoc:

===============
Pandoc Kurulumu
===============

Pandoc, açık kaynak kodlu bir belge dönüştürme aracıdır. Yaygın olarak, özellikle akademisyenler tarafından, bir yazma aracı ve de iş akışlarını yayınlamak için temel olarak kullanılır. Dosyaları bir biçimlendirme biçiminden diğerine dönüştürmeniz gerekiyorsa, pandoc sizin için bir isviçre çakısıdır.

`Çevrimiçi pandoc uygulamasını <https://pandoc.org/try/>`_ kullanarak da elinizdeki mevcut içerikleri programın izin verdiği formata (.html, .md, .rst, .tex vb. gibi) dönüştürebilirsiniz.

Farklı işletim sistemleri için kurulum yönergelerine ve de kurulum paketleri hakkındaki bilgiye `Pandoc web sayfasından <https://pandoc.org/installing.html>`_ ulaşabilirsiniz. Pandoc kurulum paketinin son sürümüne ulaşmak için aşağıdaki linki kontrol edebilirsiniz:

`Pandoc GitHub sayfası <https://github.com/jgm/pandoc/releases/latest>`_

Bilgisayarınıza Pandoc'u kurmak için öncelikle terminalden ``wget`` komutu ile, işletim sisteminize uygun olan kurulum dosyasını indiriniz. Ubuntu işletim sistemi için:

.. code-block::

  wget https://github.com/jgm/pandoc/releases/download/2.13/pandoc-2.13-1-amd64.deb

Terminal ekranınızda aşağıdaki gibi bir çıktı görüntülenecektir:

.. code-block::

 --2021-04-07 12:16:10--  https://github.com/jgm/pandoc/releases/download/2.13/pandoc-2.13-1-amd64.deb
 Resolving github.com (github.com)... 140.82.121.3
 Connecting to github.com (github.com)|140.82.121.3|:443... connected.
 HTTP request sent, awaiting response... 302 Found
 Location: https://github-releases.githubusercontent.com/571770/b2ba0f00-89c6-11eb-865f-abff793703ea?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20210407%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20210407T091610Z&X-Amz-Expires=300&X-Amz-Signature=3ea8e56667002b77fb69b085067ffa8c8c448f1e7c993e0a7a75a645989d9340&X-Amz-SignedHeaders=host&actor_id=0&key_id=0&repo_id=571770&response-content-disposition=attachment%3B%20filename%3Dpandoc-2.13-1-amd64.deb&response-content-type=application%2Foctet-stream [following]
 --2021-04-07 12:16:11--  https://github-releases.githubusercontent.com/571770/b2ba0f00-89c6-11eb-865f-abff793703ea?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20210407%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20210407T091610Z&X-Amz-Expires=300&X-Amz-Signature=3ea8e56667002b77fb69b085067ffa8c8c448f1e7c993e0a7a75a645989d9340&X-Amz-SignedHeaders=host&actor_id=0&key_id=0&repo_id=571770&response-content-disposition=attachment%3B%20filename%3Dpandoc-2.13-1-amd64.deb&response-content-type=application%2Foctet-stream
 Resolving github-releases.githubusercontent.com (github-releases.githubusercontent.com)... 185.199.109.154, 185.199.110.154, 185.199.111.154, ...
 Connecting to github-releases.githubusercontent.com (github-releases.githubusercontent.com)|185.199.109.154|:443... connected.
 HTTP request sent, awaiting response... 200 OK
 Length: 14799022 (14M) [application/octet-stream]
 Saving to: ‘pandoc-2.13-1-amd64.deb’

 pandoc-2.13-1-amd64.deb           100%[============================================================>]  14,11M  9,40MB/s    in 1,5s    

 2021-04-07 12:16:12 (9,40 MB/s) - ‘pandoc-2.13-1-amd64.deb’ saved [14799022/14799022]

Daha sonra Pandec paketinin kurulumu için aşağıdaki komutu yazınız:

.. code-block::

   sudo dpkg -i pandoc-2.13-1-amd64.deb

Kurulum sırasında terminalde aşağıdaki gibi bilgiler görüntülenecektir:

.. code-block::

  Selecting previously unselected package pandoc.
  (Reading database ... 201241 files and directories currently installed.)
  Preparing to unpack pandoc-2.13-1-amd64.deb ...
  Unpacking pandoc (2.13-1) ...
  Setting up pandoc (2.13-1) ...
  Processing triggers for man-db (2.9.1-1) ...

Kurulum tamamlandıktan sonra terminalden ``pandoc`` komutunu test edebilirsiniz. ``pandoc -h`` ile omut hakkında ayrıntılı bilgi elde edebilirsiniz.

``.md`` formatından ``.rst`` formatına dönüştürmek istediğiniz dosyaların bulunduğu klasöre gidiniz. Dönüştürmek istediğiniz her dosya için aşağıdaki komutu yazınız:

.. code-block::

   pandoc -s --toc -f markdown <girdidosyası.md> -t rst -o <ciktidosyası.rst>

.. code-block::

  -s pandoc'a bağımsız bir belge oluşturmasını söyler

  --toc, pandoc'a içindekiler tablosu oluşturmasını söyler (isteğe bağlı)

  -t pandoc'a reStructuredText çıktısı üretmesini söyler

  -f pandoc'a girdi biçimini söyler

Formatlar hakkındaki bilgiye `Pandoc kullanım kitapçığından <https://pandoc.org/MANUAL.html>`_ ulaşabilirsiniz.

Kısa kod blokları kullanılarak klasörün içindeki mevcut .md formatındaki dosyalar .rst formatına otomatik olarak kolayca dönüştürülebilir. Örnek olarak `<https://gist.github.com/ldong/48f0df6f99396266970d>`_ linkindeki kodu inceleyebilirsiniz.








