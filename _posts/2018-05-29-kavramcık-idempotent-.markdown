---
title: Değişik Bir Kavram, Idempotent
layout: post
date: 2018-05-29 13:07
image: https://i.imgflip.com/2b6jzu.jpg
headerImage: https://i.imgflip.com/2b6jzu.jpg
tag:
- Math
- Linguistics
- Computer Science
blog: true
author: ahmetsina
description: Son bir asırdır yaşayan, önümüze farklı farklı alanlarda hep çıkan bir İngilizce kelime, Idempotent. Peki nedir bu idempotent?
---

Idempotent, Idempotence, Idempotency,... Makalelerde ve özellikle Medium yazılarında sık rastladığım bir kelime. [Bu yazı gibi](https://hackernoon.com/idempotency-apis-and-retries-34b161f64cb4) daha çok HTTP ve REST API yazılarında, ya da aşağıdaki gibi tweetlerde karşılaştığım bu kelimeyi tabi ki araştırma gereksinimi duydum.
<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">You know how HTTP GET requests are meant to be idempotent? Well, do I have the story for you ... a while back I added WiFi control to our garage doors with little Wemos D1s.</p>&mdash; Will Pearse (@rombulow) <a href="https://twitter.com/rombulow/status/990684453734203392?ref_src=twsrc%5Etfw">April 29, 2018</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

Idempotent, aslında bizim matematik derslerinde üzerine bastığımız ama onun orda olduğunda farkında olmadığımız bir taş gibi. **[Google Ngram Viewer grafiğine göre](https://books.google.com/ngrams/interactive_chart?content=idempotent&year_start=1800&year_end=2000&corpus=15&smoothing=3&share=&direct_url=t1%3B%2Cidempotent%3B%2Cc0)** 1920'den bu yana sürekli kullanılan bu kelime aslında birleşik bir kelime. "Idem", Latince aynı veya eş anlamına gelirken potent de güç anlamına geliyor. Birleşimi de eşgüç veya aynıgüç olarak düşünebiliriz.  



  Bu terimin **29 Nisan 2017**'den beri kapalı olan **Wikipedia**'ya -çare [Wikiwand](http://www.wikiwand.com/)- göre tanımı şöyle:
>   **Idempotence:** *(/ˌaɪdᵻmˈpoʊtəns/ eye-dəm-poh-təns[citation needed])* is the property of certain operations in mathematics and computer science, that can be applied multiple times without changing the result beyond the initial application.

Yani "Idempotence" matematik ve bilgisayar bilimlerinde, ilk uygulamayı aşmadan sonucu değiştirmeden, birden çok kez uygulanabilen belirli işlemlerin özelliğidir *(property)*. Uygulama alanlarına göre farklı anlamlara da sahip olabiliyor bu kelime.
* Tek bir işlem (veya işlev), herhangi bir değere iki kez uygulandığında, bir kez uygulanmış gibi aynı sonucu verirse, idempotenttir; yani, ƒ (ƒ (x)) ≡ ƒ (x). Örneğin, mutlak değer fonksiyonu, abs (abs (x)) ≡ abs (x), idempotenttir.
* Bir ikili işlem verildiğinde, işlem için bir idempotent eleman (veya basitçe bir "idempotent"), işlemin, her iki işleneni için bu değer verildiğinde sonuç olarak bu değeri verdiği bir değerdir. Örneğin, 1 sayısı bir çarpımın idempotentidir: 1 × 1 = 1.

* Tüm elemanlar işlem açısından idempotent elemanlar ise, ikili bir işlem idempotent denir. Başka bir deyişle, iki eşit değere uygulandığında, sonuç olarak bu değeri verir. Örneğin, iki eşit değerin maksimum değerini veren fonksiyon idempotenttir: max (x, x) ≡ x.

Bilgisayar biliminde, idempotent terimi, bir veya birkaç kez uygulandığında aynı sonuçları verecek bir operasyonu tanımlamak için daha kapsamlı bir şekilde kullanılmaktadır. Bu, uygulandığı bağlama bağlı olarak farklı bir anlama sahip olabilir. Örneğin, yan etkiler içeren yöntem veya altprogram çağrıları söz konusu olduğunda, değiştirilen durum ilk aramadan sonra aynı kalır. Fonksiyonel programlamada, bir idempotent fonksiyonu, herhangi bir x değeri için f (f (x)) = f (x) özelliğine sahip olan bir işlevdir.

Bu, birçok durumda, bir operasyonun, istenmeyen etkilere neden olmadan, sık sık tekrarlanabileceği veya tekrarlanabileceği anlamına gelen çok kullanışlı bir özelliktir. Idempotent olmayan işlemlerde, algoritmanın, işlemin gerçekleştirilip gerçekleştirilmediğini takip etmesi gerekebilir.

Örnekleri
------
Bir veritabanında müşterinin adını ve adresini arayan bir işlev genellikle idempotenttir, çünkü bu veritabanı değişmesine neden olmaz. Benzer şekilde, bir müşterinin adresini değiştirmek genellikle temkinlidir, çünkü nihai adresin kaç kez gönderilip gönderilmediği önemli değildir. Bununla birlikte, müşteri için bir araba için bir sipariş vermek genellikle idempotent değildir, çünkü aramanın birkaç kez çalıştırılması birkaç siparişin verilmesine yol açacaktır. Bir siparişin iptal edilmesi idempotenttir, çünkü kaç talep olursa olsun sipariş iptal edilir.

Birçok insanın günlük yaşamlarında karşılaşabileceği uygulamalı örnekler arasında da asansör çağrı butonları ve yaya geçme düğmeleri yer alıyor. Düğmenin ilk etkinleştirilmesi, istek yerine getirilene kadar sistemi istekte bulunan bir duruma taşır. Sistem, aktivasyon sayısına bağlı olarak talebi karşılayacak zamanı ayarlamak için tasarlanmadıkça, ilk aktivasyon ile tatmin edilen talep arasındaki düğmenin sonraki aktivitelerinin bir etkisi yoktur.


Okumak ve İzlemek
-----------------
Bu yabancı kelimelere İngilizce makalelerde ve yazılarda denk geliyorum genellikle. Arada sırada da yabancı dizilerden duyduğum güzel kelimelere ve kavramlara rastlıyorum. Onlardan biri de: **[Manhunt: Unabomber](https://g.co/kgs/hZgWAj)**

![Manhunt: Unabomber](https://i.ytimg.com/vi/IMOmv8WpVh8/maxresdefault.jpg)

Dizi FBI özel profilleme ajanı Fitz'in, 15 bombalama suçuyla aranan Unabomber'ın tek izi olan yazılarından profilinin çıkarıp ona ulaşmasını konu alıyor. Bu diziden öğrendiğim bir kelime de _**"idiolect"**_. _**"Idiolect"**_ dil biliminde kişilerin kendilerine has farkederek veya farketmeyerek kullandığı dil yapısıdır. Kullanılan kelimeler, noktalama işaretleri, içerik ve hatta yapılan hatalar bile kişi hakkında iyi bir profilleme olanağı sunabilir. Dizinin 1. sezonunun daha ilk 5 bölümünü izledim. Fakat IMDB ve Rotten Tomatoes oranlarına destekte bulunarak izlemenizi tavsiye ederim.

Bir diğer tavsiye edebileceğim bir dizi de **[Halt And Catch Fire](https://www.imdb.com/title/tt2543312/)**

![İşte bu dediğim bir dizi](http://images.amcnetworks.com/amc.com/wp-content/uploads/2017/07/HALT-S4-KeyArt-1200x707.jpg)

Dizi 1980'lerin bilişim dünyasında yer alan kişileri konu alıyor. Nedendir bilmiyorum dizinin jeneriğini ve oyuncu kadrosunu çok beğendim. Umarım siz de beğenirsiniz..

<iframe width="560" height="315" src="https://www.youtube.com/embed/yD_kCKiSkoI" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
