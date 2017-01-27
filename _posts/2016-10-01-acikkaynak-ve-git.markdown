---
title: "Açık Kaynak Projeler ve Git"
layout: post
date: 2016-10-01 12:44
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


Açık kaynak(open-source) projeler, katkı sağlama yoluyla erişime açık repositorylerde saklanan ve üzerinde çalışılan (türkçesi depo ama biraz tuhaf geldiği için bunu kullanacağım) genellikle geliştirme aşamasında Git sistemi kullanılan, geliştirici topluluklarının oluşturduğu projelerdir.

Bir dağıtılmış versiyon kontrol sistemi olarak Git, takım bazlı ve açık kaynak projelerde katkıda bulunma ve sürdürülebilirlik sağlar. Ücretsiz indirip kullanmanız buna bir örnek olabilir.

Bu yazımda, açık kaynak (bundan sonra open-source olarak geçecek) projeleri ve bu projelere katkıda bulunmanın faydalarına, Git sisteminin bilgisayarınıza kurulumunu ve bu sistemi kullanarak nasıl bir projeye katkıda bulunabileceğinize değineceğim.

### Open-Source projelere katkıda bulunmak

Open-source projeler, ücretsiz ulaşabileceğiniz, tekrardan yayımlayabileceğiniz ve düzenleyebileceğiniz projelerdir.

Open-source projelere katkıda bulunmak, son kullanıcıların teknolojinin olanaklardan daha fazla faydalanmalarını sağlar. Son kullanıcılar sözü ileride sizin şirket kurduğunuzda müşteriniz olabilir. Bu yüzden şimdiden herhangi bir ücret almadan son kullanıcıların ihtiyaçlarını belirlemek ve ona göre bu ihtiyaçları gidermek iş hayatınızda sizin önceden kazandığınız bir yetenek olacaktır ve size artı puan katacaktır. Aynı zamanda takım çalışmasına yatkınlığınız, süreç yönetimi ve planlama yeteneğiniz de gelişir.

Eğer bir open-source projeye katkıda bulunmak istiyorsanız başlangıç olarak en iyi yol, sevdiğiniz ve iyi kullandığınız bir open-source uygulamanın veya projeyi incelemek ve katkıda bulunmaktır. Çünkü sevdiğiniz ve iyi kullandığınız uygulamanın birçok özelliğini zaten çözmüşsünüzdür ve diğer özelliklerin de üstüne korkmadan gidebilirsiniz. Open-source projelere katkıda bulunurken bilmeniz gereken başlıca konular vardır. Bunlardan ilki **CONTRIBUTING.md** dosyasıdır. Bu dosyada katkıda bulunmak için gerekli talimatlar yer alır. Mesela projenin neresine katkıda bulunabileceğiniz, katkıda bulunma sürecinde dikkat edilmesi gereken yerler, vb. birçok talimat yer alır. Bunların gözardı edilmesi durumunda projeye olan katkınız kabul görmeyebilir. Bu yüzden bu dosyayı incelemek önemlidir. Sonuçta emek harcayıp da neticesini görememek hayal kırıklığını sebep olur.

Son olarak open-source olarak katkıda bulunmaya başlamışsanız projelerde küçük çaplı değişiklikler yapmak ve özellikler eklemek iyi fikir olabilir. Mesela ufak tefek yazma hataları, yorum ekleme veya dökümantasyonun daha anlaşılır olması gibi katkılarda bulunabilirsiniz.

### Git

Ve gelelim Git’e. Git yazılım dünyasındaki en popüler versiyon kontrol sistemidir. Bunun en önemli sebeplerinden biri de 2005’te Linux çekirdeğinin kurucusu Linus Torvalds tarafından oluşturuldu.

Birçok proje de dosyalarını Git altyapısına uygun Github, GitLab veya BitBucket gibi paylaşıma uygun ve basitçe katkıda bulunulabilecek sitelerde barındırır. Git’te çalışılan her dosya bir merkezi sunucu yada ağ erişimi ile geçmişinin tamamen izlendiği tam teşekkülü bir repository’dir. Repository’ni Türkçe karşılığı depo veya haznedir fakat biz sürekli repository veya onun kısaltması repo kelimesini göreceğimizden bu iki kelimeyi kullanacağız.

Öncelikle Git kurulumundan başlayalım.

**Windows** için:

**[Git-Scm](https://git-scm.com/download/win)** adresinden kurulum dosyasını indirip Git’i sistemimize kuruyoruz.

**Linux** için:

Normalde çoğu Linux sistemlerde git hali hazırda kuruludur. Bunu, komut satırında:

<pre>$ git --version</pre>

yazarak versiyon bilgisini verip vermediğine bakarak kurulu olup olmadığını anlayabilirsiniz.

Eğer kurulu değilse dağıtımlara göre:

**Debian/Ubuntu** :

<pre>$ apt-get install git</pre>

**Fedora** :
<pre>
$ yum install git (up to Fedora 21)
$ dnf install git (Fedora 22 and later)
</pre>
**Gentoo** :

<pre>$ emerge --ask --verbose dev-vcs/git </pre>

**Arch Linux** :

<pre>$ pacman -S git</pre>

**openSUSE** :

<pre>$ zypper install git</pre>

**FreeBSD** :
<pre>
$ cd /usr/ports/devel/git
$ make install
</pre>
**Solaris 9/10/11 (OpenCSW)** :
<pre>
$ pkgutil -i git
</pre>
**Solaris 11 Express** :
<pre>
$ pkg install developer/versioning/git
</pre>
**OpenBSD** :
<pre>
$ pkg_add git
</pre>

**macOS** için :

[Şu adresten](https://git-scm.com/download/mac) indirip kurabilirsiniz.

Bu yazımızda Git’in kurulumundan bahsettik. Daha detaylı bilgi için Git’in kendi sitesini inceleyebilirsiniz. Gelecek yazımda **Git (configrasyonu)** ayarlamaları ile başlangıç işlemleri alakalı olacak. Bol kodlamalı günler.. 🙂
<iframe src="//giphy.com/embed/ZVik7pBtu9dNS?html5=true" width="530" height="310" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>
