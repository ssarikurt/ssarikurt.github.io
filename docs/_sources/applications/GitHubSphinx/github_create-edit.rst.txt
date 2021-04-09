.. _github_create-edit:

==================================================
Spinhx Kullanarak GitHub'da Web Sayfası Hazırlamak
==================================================


GitHub Web Sayfası İçin Hazırlık
================================

*GitHub'da web sayfaları barındırabileceğinizi biliyor musunuz? Web sayfanızı Spinhx ile özelleştirebilirsiniz!*

GitHub, kişisel sayfalar ve projeleriniz için web sayfaları oluşturmanıza imkan tanır. Kişisel sayfanız, kullanıcı adınızla aynı olması gereken özel bir depoda (repository) tutulur. Bu kişisel web sayfası varsayılan olarak https://kullanciadi.github.io'da yer alacaktır. İstediğiniz bir alan adı yönlendirmesine de sahip olabilirsiniz. Proje web sayfaları, varsayılan olarak, https://kullaniciadi.github.io/repository şeklinde sunulur; burada "repository" projeniz için oluşturduğunuz deponun ismidir.

GitHub üzerinde web sayfası oluşturmak için ilgili yönergelere `buradan <https://pages.github.com/>`_ ulaşabilirsiniz. Spinhx'i kullanmak istiyorsanız işlem adımları biraz farklıdır. Spinhx kullanarak, bir proje için web sayfasının nasıl kurulacağına dair bilgileri aşağıda bulabilirsiniz. Kişisel web sayfası için de işlem adımları benzerdir, sadece 'repository' yerine kullanıcı adınızı kullanmanız gerekecektir.

GitHub İçeriği Oluşturma ve Düzenleme
---------------------------------------

GitHub hesabınızda projelerinize ait içerekleri yerel olarak kendi bilgisayarınızda *komut satırı* kullanarak oluşturabilirsiniz. İçerik oluşturmak için bilgisayarınıza kurabileceğiniz grafik arayüzü sağlayan programlar da bulunmaktadır. Örneğin; `GitHub Desktop <https://desktop.github.com/>`_, `Visual Studio Code <https://code.visualstudio.com/>`_.

https://kullaniciadi.github.io/repository şeklinde web sayfası yayınlamak için öncelikle bir repository oluşturmamız gerekmektedir. Bunun için https://github.com/username GitHub kullanıcı sayfanızda sağ üstteki kullanıcı avatarınızın yanında ``+`` ikonuna tıklayınız ve ``new repository`` i seçiniz. Ve repository için bir isim belirleyiniz. Bu repository altında oluşturacağınız içeriğin web sayfası olarak yayınlanabilmesi için oluşturduğunuz repository ``public`` olmalıdır.  

.. image:: files/github-newrepo.png

``Create repository`` i seçtikten sonra boş bir repository oluşturulacak ve aşağıdaki gibi bir ekran karşınıza çıkacak.

.. image:: files/github-repolocal.png

Kendi bilgisayarınızdan içeriği oluşturup düzenlemek için çalışmak istediğiniz klasöre gidiniz ve burada, tercihen, GitHub üzerinden oluşturduğunuz ``repository`` ile aynı isimde olacak şekilde bir klasör oluşturunuz. Aşağıdaki komutları kullanarak klasör içerisinde bir dosya oluşturup, ``repository`` niz için branch yaratınız ve bunları GitHub sayfanıza gönderiniz:

.. code-block::

   mkdir hpcnotes
   cd hpcnotes
   touch testfile
   git init
   git add testfile
   git commit -m "first commit"
   git branch -M main
   git remote add origin git@github.com:ssarikurt/hpcnotes.git

``git push`` komutu ile yerel bilgisayarda oluşturduğunuz, düzenlediğiniz içerikleri GitHub'a göndermeden önce ``ssh-keygen`` oluşturup ilgili şifreleme anahtarını GitHub kullanıcı hesabınızda tanımlamanız gerekmektedir. Bunun için aşağıdaki adımları takip edebilirsiniz.

``ev dizini`` gibi tercih ettiğiniz bir klasör altında ``keys`` adlı bir klasör açıp anahtar dosyalarınızı burada saklayabilirsiniz:

.. code-block::
   
   mkdir keys
   cd keys
   ssh-keygen

komutunu yazdığınızda ekranda aşağıdaki bilgiler görüntülecek::

  Generating public/private rsa key pair.
  Enter file in which to save the key (/Users/sevilsarikurt/.ssh/id_rsa): hpcnotes_rsa
  Enter passphrase (empty for no passphrase):
  Enter same passphrase again:

Bu aşamada herhangi bir şifre girmeyip sadece ``enter`` a basabilirsiniz. Sonuç olarak iki tane rsa şifreleme dosyaları oluşacak (buradaki örnek için; *hpcnotes_rsa* ve *hpcnotes_rsa.pub*). Tarayıcınızdan GitHub kullanıcı sayfanızı açınız ve ``Settings -> SSH and GPG Keys`` sayfasına gidiniz. Sayfanın sağ üst kısmındaki ``New SSH key`` butonuna tıklayınız. Çıkan ekranda ``Title`` a bir tanımlama yapıp ``Key`` kısmına da ``hpcnotes_rsa.pub`` içerisindeki şifreleme bilgisini kopyalayınız. ``Add SSH key`` dedikten sonra kendi bilgisayarınızda komut satırında aşağıdaki komutu yazdığınızda şifre, anahtarlığınıza eklenecektir:

.. code-block::

   ssh-add /home/username/keys/hpcnotes_rsa

Terminalde ``ssh-add`` komutu ile anahtarlamayı ekleme adımını atladığınızda ise aşağıdaki gibi bir hata mesajı ile karşılaşacaksınız:

.. code-block::

   git push -u origin main
      git@github.com: Permission denied (publickey).
      fatal: Could not read from remote repository.

      Please make sure you have the correct access rights and the repository exists.

Anahtar oluşturma ve ekleme işlemi bittikten sonra ``git push`` komutu ile, içerikte yaptığınız değişiklikleri GitHub' a aktarabilirsiniz:

.. code-block::

   git push -u origin main

      Enumerating objects: 3, done.
      Counting objects: 100% (3/3), done.
      Writing objects: 100% (3/3), 209 bytes | 209.00 KiB/s, done.
      Total 3 (delta 0), reused 0 (delta 0)
      To github.com:ssarikurt/hpcnotes.git
      * [new branch]      main -> main
      Branch 'main' set up to track remote branch 'main' from 'origin'.

Artık GitHub üzerindeki repository sayfanız güncellenmiş olacaktır.

* Spinhx'i kullanmak istediğimiz için GitHub'ın ``jekyll`` ini devre dışı bırakmamız gerekmektedir. Bu, web kök dizinine ``.nojekyll`` adlı bir dosya yerleştirilerek yapılır. Bu dosya mevcut olduğunda GitHub, *index.html* 'yi doğrudan sunacaktır. (Not: Bu aynı zamanda ``Spinhx hızlı başlangıç betiği`` tarafından da sunulmaktadır, ancak burada ilk aşamada yapılması daha iyidir.)

.. code-block::

   mkdir docs
   cd docs
   touch .nojekyll 
   git add .nojekyll 
   git commit -m "Disable jekyll" 
   git push

* GitHub sayfanıza gidin ve projenizin ayarlar sayfasını açınız.
    
 .. image:: files/project_settings.png

* Eğer projeyi oluştururken GitHub önerilerini takip ettiyseniz projenize ait bir **``ana dal``** olacaktır. GitHub'a, bu projenin **docs** klasöründe ve **ana dal** da yer alan bir web sayfası olacağına dair tanımlama yapmamız gerekmektedir. Bunun için ``Settings -> Pages`` sayfasına giderek ayarları yapabilirsiniz.

.. note::
   *Projenizin web sayfası olarak yayınlanabilmesi için oluşturduğunuz depo ``public`` olmalıdır.*

.. image:: files/project_page.png
