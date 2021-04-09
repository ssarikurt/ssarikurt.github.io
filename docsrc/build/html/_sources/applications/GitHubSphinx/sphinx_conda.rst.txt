.. _sphinx_conda:


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

Komutu ile ``sphinx`` isimli (veya farklı bir isimde) çevre değişkeni oluşturunuz.

.. code-block::

   conda activate sphinx

Komutu ile ``sphinx`` adını verdiğiniz çevre değişkenini aktif hale getiriniz. Çevre değişkenini aktif hale getirdikten sonra terminalinizde parantez içerisinde çevre değişkeninizin ismi yer alacaktır:

.. code-block::

   (sphinx) $

.. note::

   İlgili çevre değişkenini aktif durumdan çekmek için ``conda deactive`` komutunu kullanmanız yeterli olacaktır.

Conda ile etkinleştirilen ortam ``pip`` ile birlikte gelir. Burada ``pip`` komutu ile belirttiğiniz paketler sadece etkinleştirilmiş ortam için kurulacaktır. Aktif çevre değişkeni içerisinde ``sphinx`` kurmadan önce ``sphinx`` ile ilgili paketleri aşağıdaki komutu kullanarak arayabilirsiniz.

.. code-block::

   (sphinx) $ wget -O - https://pypi.org/simple/ | grep -i sphinx

Terminalde ``sphinx`` ile ilgili bir sürü paketin listelendiğini göreceksiniz. Temel kullanım için bu paketlerin hepsine ihtiyacınız olmayacaktır. Aşağıdaki örnek komut satırında belirtildiği gibi istediğiniz özellikleri sağlayan paketleri araştırıp (matematiksel yazım, jupyter ortamı gibi) kurabilirsiniz.

.. code-block::

   pip install jupyter-sphinx nbsphinx  sphinx sphinx-bootstrap-theme sphinxcontrib-jsmath

 Yukarıdaki komut satırı belirtilen paketler için gerekli tüm paketleri kuracaktır. Daha sonra klasik sphinx kurulum adımına geçebilirsiniz.

Sphinx'i projenizin *kök dizini* nde başlatın. Bunun için Spinhx'in sayfasındaki `başlangıç betiği <https://www.sphinx-doc.org/en/master/usage/quickstart.html>`_ incelenebilir. Aşağıdaki örnek komut satırında, projenin kök dizininde ``docsrc`` klasörü oluşturularak bu klasör altında ``sphinx`` başlatılmaktadır.

.. code-block:: 

   (sphinx) $ mkdir docsrc
   (sphinx) $ cd docsrc
   (sphinx) ~docsrc$ sphinx-quickstart

Aşağıda Linux işletim sisteminde çalıştırılan örnek betik ayarları verilmiştir. Diğer işletim sistemleri için ekrana çıkan bilgiler değişiklik gösterebilir.

.. code-block::

   Welcome to the Sphinx 3.5.3 quickstart utility.

   Please enter values for the following settings (just press Enter to 
   accept a default value, if one is given in brackets).

   Selected root path: .

   You have two options for placing the build directory for Sphinx output.
   Either, you use a directory "_build" within the root path, or you separate
   "source" and "build" directories within the root path.
   > Separate source and build directories (y/n) [n]: y

   The project name will occur in several places in the built documentation.
   > Project name: hpc
   > Author name(s): hpc-contributer
   > Project release []: 2021

   If the documents are to be written in a language other than English,
   you can select a language here by its language code. Sphinx will then
   translate text that it generates into that language.

   For a list of supported codes, see
   https://www.sphinx-doc.org/en/master/usage/configuration.html#confval-language.
   > Project language [en]:

   Creating file /home/sevil/hpcnotes/docsrc/source/conf.py.
   Creating file /home/sevil/hpcnotes/docsrc/source/index.rst.
   Creating file /home/sevil/hpcnotes/docsrc/Makefile.
   Creating file /home/sevil/hpcnotes/docsrc/make.bat.

   Finished: An initial directory structure has been created.

   You should now populate your master file ./source/index.rst and create other documentation    source files. Use the Makefile to build the docs, like so:
   make builder
   where "builder" is one of the supported builders, e.g. html, latex or linkcheck.

Kurulum tamamlandıktan sonra web sayfasına dair önemli ayarların (tema, eklentiler gibi) tamamının bulunduğu ``conf.py`` dosyasını oluşturur. 

.. hint:: Kaynak dizininizin (*docsrc/source*) içerisinde bulunan ``conf.py`` konfigürasyon dosyasında, aşağıdaki örnekte olduğu gibi, web sayfanızı oluşturmak için gerekli eklentileri tanımlayabilirsiniz. Örneğin; matematiksel yazım formatı için ``sphinx.ext.mathjax``, jupyter için ``jupyter_sphinx`` ve ``nbsphinx`` gibi::

      # Add any Sphinx extension module names here, as strings. They can be
      # extensions coming with Sphinx (named 'sphinx.ext.*') or your custom
      # ones.
      extensions = [
        'sphinx.ext.intersphinx',
        'sphinx.ext.todo',
        'sphinx.ext.coverage',
        'sphinx.ext.mathjax',
        'sphinx.ext.viewcode',
        'sphinx.ext.githubpages',
        'jupyter_sphinx',
        'nbsphinx',
       ]

  Spinhx ile oluşturacağınız web sayfanız için farklı temalar kullanabilirsiniz. Bunun için de `conf.py` dosyasında ``html_theme`` kısmında ilgili değişiklikleri yapmanız gerekmektedir (örnek: html_theme = 'bizstyle' )
  `Spinhx temalarına ulaşmak için tıklayınız. <https://www.sphinx-doc.org/en/master/usage/theming.html#builtin-themes>`_

Site halihazırda bir örnekle doldurulmuştur, bu nedenle oluşturulmaya hazırdır, ancak Makefile’da küçük bir değişiklik yapmak kullanışlıdır. Makefile dosyasında aşağıdaki gibi son kısımda yapılan değişiklikle çıktının otomatik olarak docs dizinine kopyalanması sağlanmaktadır.

.. code-block::

   # Minimal makefile for Sphinx documentation
   #

   # You can set these variables from the command line.
   SPHINXOPTS    =
   SPHINXBUILD   = sphinx-build
   SOURCEDIR     = source
   BUILDDIR      = build

   # Put it first so that "make" without argument is like "make help".
   help:
	@$(SPHINXBUILD) -M help "$(SOURCEDIR)" "$(BUILDDIR)" $(SPHINXOPTS) $(O)

   .PHONY: help Makefile

   # Catch-all target: route all unknown targets to Sphinx using the new
   # "make mode" option.  $(O) is meant as a shortcut for $(SPHINXOPTS).
   %: Makefile
	@$(SPHINXBUILD) -M $@ "$(SOURCEDIR)" "$(BUILDDIR)" $(SPHINXOPTS) $(O)
   github:
	@make html
	cp -a build/html/. ../docs

Sona eklediğimiz ``github`` bölümü, belgeleri ``source`` dizininde (daha net olarak; buradaki akışta ``hpcnotes/docsrc/source`` dizininde) derler ve ilgili dosyaları ``build/html``'den ``docs`` klasörüne kopyalar. 

.. note::

   Makefile dosyasında yapılan değişiklikle ``build/html`` klasörünü içerisindeki tüm html sayfaları ``docs`` klasörüne kopyalandığı için ``build`` klasörü ``git push`` komutu ile karşı tarafa (GitHub sayfanıza) iletilecek içerikten hariç tutulabilir. Çünkü halihazırda tüm html bilgileri ``docs`` klasörünü eşlenmesiyle iletilmektedir. Bunun için ana dizine (buradaki akışta hpcnotes klasörü altında), dosya trafiğini azaltmak adına, ``.gitignore`` dosyası eklenerek içerisinde ``build`` klasörü tanımlanabilir.

``make github`` komutundan önce dosyaları ekleyip, işlemek ve de iletmek gerekmektedir. Bunun için kök dizininize (buradaki örnek için ``hpcnotes`` klasörüne) gidip aşağıdaki komutları uygulamanız gerekmektedir:

.. code-block::

   git add docsrc/ --all
   git commit -m "Sphinx source" 
   git push

Bu komutlar sadece kaynak dosyaları iletecektir. Web sayfasının kendisini derlemek ve de iletmek için ise aşağıdaki komutları kullanmanız gerekmektedir:

.. code-block::

   cd docsrc
   make github
   cd ..
   git add --all
   git commit -m "Web page update"
   git push

GitHub'a yenilenmesi için biraz zaman tanıyın. Ve artık proje web sayfanız hazır!

.. note::

   reStructuredText (rst) yazım dili hakkında `ayrıntılı bilgilere ulaşmak için tıklayınız. <https://www.sphinx-doc.org/en/master/usage/restructuredtext/index.html>`_


