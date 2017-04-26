---
title: Activeadmin'de has_many through iliskisi
layout: post
date: 2017-04-26 13:07
image: https://qph.ec.quoracdn.net/main-qimg-dfe391703106039fde937a6238ca6aaf
headerImage: https://qph.ec.quoracdn.net/main-qimg-dfe391703106039fde937a6238ca6aaf
tag:
- Ruby
- Rails
- Activeadmin
blog: true
author: ahmetsina
description: Ruby on Rails'de many to many ilişkisini ve bunun activeadmine uyarlanması.
---
Bu blog yazısını yazmak için çok uğraştım. Neden mi? Çünkü bu konuyla alakalı yapmak isteyip de yapamadığım ve aldığım hatalar yüzünden. 2-3 aydır bununla uğraştım diyebilirim. Arada sırada başka branche atlayıp bu aşamaya ara verdiğim çok oldu. Hatta Ruby temel bilgilerimi bile tazelediğim, Hackerrank'ta kendimi avuttuğum zamanlar oldu. Şimdi bu kadar lafazanlık yeter. Gelelim ne yapmak istediğime..

[Activeadmin](http://activeadmin.info)

### Ruby on Rails'te many-to-many ilişkisi
Öncelikle Ruby on Rails'de **many to many** ilişkisi nasıl oluyor bir bakalım. Rails'in kendi [dokümantasyonunda](http://guides.rubyonrails.org/association_basics.html) olduğu gibi many-to-many ilişkisi şu şekilde kuruluyor. Benim ilişkim Haber ve Hategori modeli arasında oluşuyor.  <span class="evidence">Bir haber birden fazla kategoriye sahip olabilir ve bir kategoride de birden fazla haber olabilir.</span>
{% highlight raw %} { % gist ahmetsina/5ac9890ae51f6eecf22b92bfc9451936 % } {% endhighlight %}
