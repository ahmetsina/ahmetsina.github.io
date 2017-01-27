---
title: "Tasarım Kalıbı Nedir?"
layout: post
date: 2016-12-31 12:44
tag:
- Design Patterns
- WEB
- MVC
blog: true
author: ahmetsina
description:
---

10 kişinin bir problem hakkında çözüm oluşturduğunu düşünün. Muhtemel 10 farklı çözüm yolu olabilir değil mi? Ve bu çözüm yollarının sadece biri de doğru olmayabilir. Yani birden fazla doğru yol olabilir. Fakat bu çözüm yollarından sizin için daha performanslı, daha az maliyetli, daha okunaklı gibi bir takım kriterleri göz önüne alarak çözüm yolunuzu ve stratejinizi belirlemeniz gerekir. İşte bu karmaşıklığı önlemek amacıyla bir tasarım kalıbı önümüze bir çözüm olarak geliyor.

Eğer takım olarak çalışmak istiyorsanız yazdığınız kod üzerinde çalışacak diğer takım arkadaşlarınızın da kod üzerinde çalışabiliyor olması lazım. Bunun için kendi aranızda bir standart belirlemeniz gerekir. Bu var olan standartları kullanarak da olabilir, kendi aranızda sıfırdan oluşturduğunuz bir standart da olabilir.

Misal olarak web geliştirme alanında yaygın bir standart da **MVC**‘dir. MVC, açılımdaki **Model-View-Controller** yapısını kullanır.

### MVC’nin bileşenleri:

 * **Model**, veriyi, mantığı ve uygulamanızda bulunan kuralları (mesela validation gibi) yönetir.
 * **View**, veriniz bir grafiğe dökülmesi gibi çıktı olarak sunumulmasını sağlar. Bir view, birden fazla modelden veri alabilir.
 * **Controller** ise girişleri ve çıkışların kontrolünü yapar. Bir nevi denetim mekanizması.

Kullanıcı gözünden senaryo şu şekilde işler. Kullanıcı web siteye girdiğinde karşılaştığı arayüz view’dir. Karşılaştığı kişisel ve spesifik veriler modeldir. Ve bu veriler ile herhangi bir işlem yaptığında arkada dönen controller sistemidir.

MVC’ye alternatif diğer tasarım kalıpları da **MVP ( Model-View-Presenter) ve MVVM (Model-View-ViewModel)**’dir.

Bu tasarım kalıplarından en azından birini -özellikle çok yaygın olan MVC’yi- öğrenmeniz sizin açınızdan çok faydalı olacaktır. Çünkü şuanki bir çok web kütüphanesi bu kalıba göre şekilleniyor. Mesela Ruby On Rails, -ki kendisini çok severiz..- CodeIgniter, Laravel, Zend, Django ve daha bir çok kütüphane bu kalıbı kullanıyor. Tasarım kalıbı kullanılmamış ve dökümante edilmemiş projeler de yeni geliştiricilerini deli eder. Bu tecrübeyle sabittir çünkü az karşılaşmadık. Bu yüzden lütfen bunlardan en az birini öğrenin ya da kendi tasarımınızı oluşturun. İyi kodlamalar. 🙂
