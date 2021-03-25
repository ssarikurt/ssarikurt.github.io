.. _spinhx:

==================================================
SPINHX Kullanarak GitHub'da Web Sayfası Hazırlamak
==================================================

*GitHub'da web sayfaları barındırabileceğinizi biliyor musunuz? Web sayfanızı Spinhx ile özelleştirebilirsiniz!*

 * GitHub, kişisel sayfalar ve projeleriniz için web sayfaları oluşturmanıza imkan tanır. Kişisel sayfanız, kullanıcı adınızla aynı olması gereken özel bir depoda (repository) tutulur. Bu kişisel web sayfası varsayılan olarak https://kullanciadi.github.io'da yer alacaktır. İstediğiniz bir alan adı yönlendirmesine de sahip olabilirsiniz. Proje web sayfaları, varsayılan olarak, https://kullaniciadi.github.io/repository şeklinde sunulur; burada "repository" projeniz için oluşturduğunuz deponun ismidir.

 * GitHub üzerinde web sayfası oluşturmak için ilgili yönergelere `buradan <https://pages.github.com/>`_ ulaşabilirsiniz. Spinhx'i kullanmak istiyorsanız işlem adımları biraz farklıdır. Spinhx kullanarak bir proje için web sayfasının nasıl kurulacağına dair bilgileri aşağıda bulabilirsiniz. Kişisel web sayfası için de işlem adımları benzerdir, sadece 'repository' yerine kullanıcı adınızı kullanmanız gerekecektir.

  * 'YBH' adında boş bir proje ile başlayalım.
  * Proje havuzunu GitHub'da belirtildiği şekilde oluşturun. 
  * Daha sonra kendi bilgisayarınızda, projenizin kök dizininin altında **docs** adlı bir dizin oluşturun. Bu, web sayfası dosyalarının bulunacağı dizindir.    

  .. code-block:: bash

     Kendi bilgisayarınızda GitHub hesabınızdaki içeriği düzenleme konusunda !!reeff!! sayfasına bakabilirsiniz.
 
  * Spinhx'i kullanmak istediğimiz için GitHub'ın ``jekyll`` ini devre dışı bırakmamız gerekmektedir. Bu, web kök dizinine ``.nojekyll`` adlı bir dosya yerleştirilerek yapılır. Bu dosya mevcut olduğunda GitHub, *index.html* 'yi doğrudan sunacaktır. (Not: Bu aynı zamanda ``Spinhx hızlı başlangıç betiği`` tarafından da sunulmaktadır, ancak burada ilk aşamada yapılması daha iyidir.)

   - mkdir docs
   - cd docs
   - touch .nojekyll 
   - git add .nojekyll 
   - git commit -m "Disable jekyll" 
   - git push

  * GitHub sayfanıza gidin ve projenizin ayarlar sayfasını açın.
  * Eğer projeyi oluştururken GitHub önerilerini takip ettiyseniz projenize ait bir ``ana dal`` olacaktır. GitHub'a, bu projenin **docs** klasöründe ve **ana dalda** yer alan bir web sayfası olacağına dair tanımlama yapmamız gerekmektedir.   
