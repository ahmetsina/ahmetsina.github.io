---
title: "Git Başlangıç Komutları"
layout: post
date: 2016-10-16 12:44
image: http://ipengineer.net/wp-content/uploads/2015/04/git-logo.jpg
headerImage: http://ipengineer.net/wp-content/uploads/2015/04/git-logo.jpg
tag:
- git
- open source
- version control
blog: true
author: ahmetsina
description: Açık Kaynak Projeler ve Git
---


Hatırladığımız gibi **Git** proje versiyon kontrol sistemidir.  Ve tabi ki versiyon kontrolünü de çalıştığımız dosyalar üzerinde yapacağız. Git bizim için çalıştığımız dosyalar üzerinde izlemeler yapar ve bize bunu bildirir. Bunun öncelikle Git’in proje dosyamızda yer alması gerekiyor. Buna Git repostiyory’si, yada reposu diyeceğiz. Bu repoyu isterseniz boş bir klasörde de oluşturabilirsiniz isterseniz dolu bir klasörde de oluşturabilirsiniz.

Bu komutlarımızı da tabi ki komut satırında bulundumuz klasör içinde yazıyoruz.


### Git init

Bu komut bulunduğumuz klasörde yeni bir “.git” klasörü oluşturur. Bu klasör git ile yapacağımız işlemleri kayıt altına alır ve denetler.

  `git init` : Girilen adresteki klasöre boş bir Git reposu açar

  `git init --bare` : Şuan girilen klasör haricinde girilen adrese boş bir Git reposu açar.

  Mesela :
    {% highlight zsh %}
    cd path/above/repo
    git init --bare my-project.git
    {% endhighlight %}

### Git clone

Bu komut var olan bir Git reposunu kopyalar.

  `git clone <repo>`

`<repo>` adresinde yer alan repoyu lokal makinenize klonlamanıza yarar. Orjinal repo bir local dosya sisteminde veya HTTP, SSH ile uzaktan erişimli bir makinede yer alır.

  <pre>git clone</pre>

`<repo>` adresinde yer alan repoyu makinenizde klonlamak istediğiniz adrese klonlar.

Mesela :
      {% highlight zsh %}
      git clone ssh://john@example.com/path/to/my-project.git
      cd my-project
      # Projeye başla
      {% endhighlight %}



Daha detaylı bilgiler için:

[Github](https://try.github.io/) (interaktif bir alıştırma)

[Atlassian](https://www.atlassian.com/git/tutorials/setting-up-a-repository)

[Git-Scm](https://git-scm.com/book/tr/v1)
