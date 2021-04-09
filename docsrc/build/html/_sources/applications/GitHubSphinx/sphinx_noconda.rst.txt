.. _spinhx_noconda:


2) **İzole edilmemiş** yerel kurulum
======================================

Farklı işletim sistemleri için `Spinhx kurulum yönergelerine <https://www.sphinx-doc.org/en/master/usage/installation.html>`_ web sayfasından ulaşabilirsiniz. Linux bilgisayarınıza yerel olarak Sphinx'i kurmak için aşağıdaki adımları takip edebilirsiniz::

 sudo apt install python3-sphinx

Kurulduktan sonra, Sphinx'i projenin *kök dizini* nde başlatın. Bunun için Spinhx'in sayfasındaki `başlangıç betiği <https://www.sphinx-doc.org/en/master/usage/quickstart.html>`_ incelenebilir::

  mkdir docsrc
  cd docsrc
  sphinx-quickstart

Aşağıda Linux işletim sisteminde çalıştırılan örnek betik ayarları verilmiştir. Diğer işletim sistemleri için ekrana çıkan bilgiler değişiklik gösterebilir::

 Welcome to the Sphinx 1.8.5 quickstart utility.

 Please enter values for the following settings (just press Enter to accept a default value,
 if one is given in brackets).
 Selected root path: .

 You have two options for placing the build directory for Sphinx output.
 Either, you use a directory "_build" within the root path, or you separate
 "source" and "build" directories within the root path.
 > Separate source and build directories (y/n) [n]: y

 Inside the root directory, two more directories will be created; "_templates" for custom 
 HTML templates and "_static" for custom stylesheets and other static files. You can enter 
 another prefix (such as ".") to replace the underscore.
 > Name prefix for templates and static dir [_]:


 The project name will occur in several places in the built documentation.
 > Project name: hpcnotes
 > Author name(s): hpcnotes
 > Project release []:

 If the documents are to be written in a language other than English,
 you can select a language here by its language code. Sphinx will then
 translate text that it generates into that language.

 For a list of supported codes, see
 http://sphinx-doc.org/config.html#confval-language.
 > Project language [en]:

 The file name suffix for source files. Commonly, this is either ".txt" or ".rst".
 Only files with this suffix are considered documents.
 > Source file suffix [.rst]:

 One document is special in that it is considered the top node of the "contents tree", 
 that is, it is the root of the hierarchical structure of the documents. Normally, this 
 is "index", but if your "index" document is a custom template, you can also set this to 
 another filename.
 > Name of your master document (without suffix) [index]:
 Indicate which of the following Sphinx extensions should be enabled:
 > autodoc: automatically insert docstrings from modules (y/n) [n]: y
 > doctest: automatically test code snippets in doctest blocks (y/n) [n]: y
 > intersphinx: link between Sphinx documentation of different projects (y/n) [n]: y
 > todo: write "todo" entries that can be shown or hidden on build (y/n) [n]: y
 > coverage: checks for documentation coverage (y/n) [n]: y
 > imgmath: include math, rendered as PNG or SVG images (y/n) [n]: n
 > mathjax: include math, rendered in the browser by MathJax (y/n) [n]: y
 > ifconfig: conditional inclusion of content based on config values (y/n) [n]: n
 > viewcode: include links to the source code of documented Python objects (y/n) [n]: y
 > githubpages: create .nojekyll file to publish the document on GitHub pages (y/n) [n]: y

 A Makefile and a Windows command file can be generated for you so that you only have to 
 run e.g. 'make html' instead of invoking sphinx-build directly.
 > Create Makefile? (y/n) [y]: y
 > Create Windows command file? (y/n) [y]: y

 Creating file ./source/conf.py.
 Creating file ./source/index.rst.
 Creating file ./Makefile.
 Creating file ./make.bat.

 Finished: An initial directory structure has been created.

Daha sonra ./source/index.rst ana dosyanızı doldurmalı ve diğer kaynak dökümantasyon belgelerinizi oluşturmalısınız. Dökümanları oluşturmak için Makefile'ı aşağıdaki gibi kullanabilirsiniz::

  make builder

Burada ``builder``, desteklenen oluşturuculardan biridir. Örneğin; *html, latex veya linkcheck*. 

Bu komut dosyası, web sayfasının tüm ayarlarının (tema gibi) bulunduğu tüm önemli ``conf.py`` dosyasını oluşturur. Site halihazırda bir örnekle doldurulmuştur, bu nedenle oluşturulmaya hazırdır, ancak Makefile'da küçük bir değişiklik yapmak kullanışlıdır, böylece çıktıyı otomatik olarak docs dizinine kopyalar.

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

``make github`` komutunu yazmadan önce dosyaları ekleyip, işlemek ve de iletmek gerekmektedir. Bunun için kök dizininize (buradaki örnek için ``hpcnotes`` klasörüne) gidip aşağıdaki komutları uygulamanız gerekmektedir::

 git add docsrc/ --all
 git commit -m "Sphinx source" 
 git push

Bu komutlar sadece kaynak dosyaları iletecektir. Web sayfasının kendisini derlemek ve de iletmek için ise aşağıdaki komutları kullanmanız gerekmektedir::

 cd docsrc
 make github
 cd ..
 git add --all
 git commit -m "Web page update"
 git push

GitHub'a yenilenmesi için biraz zaman tanıyın. Ve artık proje web sayfanız hazır!

.. note::

   reStructuredText (rst) yazım dili hakkında `ayrıntılı bilgilere ulaşmak için tıklayınız. <https://www.sphinx-doc.org/en/master/usage/restructuredtext/index.html>`_

   rst formatında denemeler yapmak isterseniz `linkteki çevrimiçi editörü <http://rst.ninjs.org/#>`_ kullanabilirsiniz.

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
