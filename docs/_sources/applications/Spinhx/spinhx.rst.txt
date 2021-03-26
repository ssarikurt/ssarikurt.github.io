.. _spinhx:

==================================================
Spinhx Kullanarak GitHub'da Web Sayfası Hazırlamak
==================================================


GitHub Web Sayfası İçin Hazırlık
================================

*GitHub'da web sayfaları barındırabileceğinizi biliyor musunuz? Web sayfanızı Spinhx ile özelleştirebilirsiniz!*

GitHub, kişisel sayfalar ve projeleriniz için web sayfaları oluşturmanıza imkan tanır. Kişisel sayfanız, kullanıcı adınızla aynı olması gereken özel bir depoda (repository) tutulur. Bu kişisel web sayfası varsayılan olarak https://kullanciadi.github.io'da yer alacaktır. İstediğiniz bir alan adı yönlendirmesine de sahip olabilirsiniz. Proje web sayfaları, varsayılan olarak, https://kullaniciadi.github.io/repository şeklinde sunulur; burada "repository" projeniz için oluşturduğunuz deponun ismidir.

GitHub üzerinde web sayfası oluşturmak için ilgili yönergelere `buradan <https://pages.github.com/>`_ ulaşabilirsiniz. Spinhx'i kullanmak istiyorsanız işlem adımları biraz farklıdır. Spinhx kullanarak bir proje için web sayfasının nasıl kurulacağına dair bilgileri aşağıda bulabilirsiniz. Kişisel web sayfası için de işlem adımları benzerdir, sadece 'repository' yerine kullanıcı adınızı kullanmanız gerekecektir.

* 'hpcnotes' adında boş bir proje ile başlayalım.
* Proje havuzunu GitHub'da belirtildiği şekilde oluşturun. 
* Daha sonra kendi bilgisayarınızda, projenizin kök dizininin altında **docs** adlı bir dizin oluşturun. Bu, web sayfası dosyalarının bulunacağı dizindir.    

 .. note::

  Kendi bilgisayarınızda GitHub hesabınızdaki içeriği nasıl düzenleyeceğiniz ile ilgili bilgilere `ulaşmak için tıklayınız. <https://ssarikurt.github.io/applications/GitHubLocal/githublocal.html>`_

* Spinhx'i kullanmak istediğimiz için GitHub'ın ``jekyll`` ini devre dışı bırakmamız gerekmektedir. Bu, web kök dizinine ``.nojekyll`` adlı bir dosya yerleştirilerek yapılır. Bu dosya mevcut olduğunda GitHub, *index.html* 'yi doğrudan sunacaktır. (Not: Bu aynı zamanda ``Spinhx hızlı başlangıç betiği`` tarafından da sunulmaktadır, ancak burada ilk aşamada yapılması daha iyidir.)

   - mkdir docs
   - cd docs
   - touch .nojekyll 
   - git add .nojekyll 
   - git commit -m "Disable jekyll" 
   - git push

* GitHub sayfanıza gidin ve projenizin ayarlar sayfasını açın.
    
 .. image:: files/project_settings.png

* Eğer projeyi oluştururken GitHub önerilerini takip ettiyseniz projenize ait bir **``ana dal``** olacaktır. GitHub'a, bu projenin **docs** klasöründe ve **ana dal** da yer alan bir web sayfası olacağına dair tanımlama yapmamız gerekmektedir. Bunun için ``Settings->Options->GitHub Pages`` sayfasına giderek ayarları yapabilirsiniz.

  .. note::
   *Projenizin web sayfası olarak yayınlanabilmesi için oluşturduğunuz depo ``public`` olmalıdır.*

.. image:: files/project_page.png

Spinhx Kurulumu
===============

Spinhx, anlaşılabilir ve güzel dökümantasyon oluşturmayı kolaylaştıran bir araçtır. Temel olarak, kod yazıyormuş gibi belgeler yazabilirsiniz ve kodlaması kolaydır. `Spinhx web sayfasından <https://www.sphinx-doc.org/>`_ ayrıntılı bilgilere ulaşabilirsiniz.

Öncelikle Spinhx'i kurmanız gerekiyor. Farklı işletim sistemleri için `Spinhx kurulum yönergelerine <https://www.sphinx-doc.org/en/master/usage/installation.html>`_ web sayfasından ulaşabilirsiniz. Linux için aşağıdaki adımları takip edebilirsiniz::

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

Sondaki``github`` bölümü, belgeleri kaynak dizinde (*source*) derler ve ilgili dosyaları ``build/html``'den ``docs`` klasörüne kopyalar. 

``make github`` yapmadan önce dosyaları ekleyip, işlemek ve de iletmek gerekmektedir. Bunun için *kök* dizininize gidip aşağıdaki komutları uygulamanız gerekmektedir::

 git add docsrc/ --all
 git commit -m "Sphinx source" 
 git push

Bu komutlar sadece kaynak dosyaları iletecektir. Web sayfasının kendisini derlemek ve de iletmek için ise aşağıdaki komutları kullanmanız gerekmektedir::

 cd docsrc
 make github
 cd ..
 git add docs/ -all
 git commit -m "Web page update"
 git push

GitHub'a yenilenmesi için biraz bekleyin ve artık proje web sayfanız hazır. 

.. note::

   reStructuredText yazım dili hakkında `ayrıntılı bilgilere ulaşmak için tıklayınız. <https://www.sphinx-doc.org/en/master/usage/restructuredtext/index.html>`_

