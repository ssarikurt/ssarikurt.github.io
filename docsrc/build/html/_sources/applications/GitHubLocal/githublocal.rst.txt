.. _githublocal:

================================================
Kendi Bilgisayarınızda GitHub İçeriği Düzenleme
================================================

GitHub hesabınızda projelerinize ait içerekleri yerel olarak kendi bilgisayarınızda *komut satırı* kullanarak oluşturabilirsiniz. İçerik oluşturmak için bilgisayarınıza kurabileceğiniz grafik arayüzü sağlayan programlar da bulunmaktadır. Örneğin; `GitHub Desktop <https://desktop.github.com/>`_, `Visual Studio Code <https://code.visualstudio.com/>`_.

Bunun için öncelikle, her defasında düzenleme yaptıkça şifre girmemek için, bilgisayarınızda ``ssh-keygen`` oluşturmanız gerekmektedir. ``keys`` adlı bir klasör açıp anahtar dosyalarınızı burada saklayabilirsiniz::

   mkdir keys
   cd keys
   ssh-keygen

komutunu yazdığınızda ekranda aşağıdaki bilgiler görüntülecek::

  Generating public/private rsa key pair.
  Enter file in which to save the key (/Users/sevilsarikurt/.ssh/id_rsa): hpcnotes_rsa
  Enter passphrase (empty for no passphrase):
  Enter same passphrase again:

Bu aşamada herhangi bir şifre girmeyip sadece ``enter`` a basabilirsiniz. Sonuç olarak iki tane rsa şifreleme dosyaları oluşacak (örneğin; *hpcnootes_rsa* ve *hpcnotes_rsa.pub*). Tarayıcınızdan GitHub kullanıcı sayfanızı açınız ve ``Settings -> SSH and GPG Keys`` sayfasına gidiniz. Sayfanın sağ üst kısmındaki ``New SSH key`` butonuna tıklayınız. Çıkan ekranda Title a bir tanımlama yapıp ``Key`` kısmına da ``hpcnotes_rsa.pub`` içerindeki şifreleme bilgisini kopyalayınız. ``Add SSH key`` dedikten sonra kendi bilgisayarınızda komut satırında aşağıdaki komutu yazdığınızdam şifre, anahtarlığınıza eklenecektir::

    ssh-add /home/username/keys/hpcnotes_rsa

Daha sonra GitHub içerisinde oluşturduğunuz proje (*repository*) sayfanızı açınız ve sağ üst kısımda bulunan yeşil renkli ``Code`` menüsüne giriniz. Buradan ``SSH`` sekmesi altında "*git*" ile başlayan kısmı kopyalayınız ve komut satırında aşağıdaki komutu yazınız::

  git clone git@github.com:ssarikurt/hpcnotes.git

Bu komut, GitHub üzerindeki proje klasörünüzün içeriğini kendi bilgisayarınıza indirmenizi sağlamaktadır. İçeride yer alan bir dosyayı kullandığınız editör yardımıyla düzenleyip kaydettikten veya yeni bir dosya ekledikten sonra aşağıdaki komutları kullanarak projenize ait web sayfanızı güncelleyebilirsiniz::

 git add dosyaadi
 git commit -m 'icerik guncelleme bilgisi'
 git push 


