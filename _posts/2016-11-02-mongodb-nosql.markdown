---
title: "MongoDB ve NoSQL"
layout: post
date: 2016-11-02 12:44
image: https://webassets.mongodb.com/_com_assets/cms/MongoDB-Logo-5c3a7405a85675366beb3a5ec4c032348c390b3f142f5e6dddf1d78e2df5cb5c.png
headerImage: https://webassets.mongodb.com/_com_assets/cms/MongoDB-Logo-5c3a7405a85675366beb3a5ec4c032348c390b3f142f5e6dddf1d78e2df5cb5c.png
tag:
- nosql
- sql
- mongodb
blog: true
author: ahmetsina
description: Açık Kaynak Projeler ve Git
---

MongoDB’yi anlamak için öncelikle bir konuyu ele alıp kavramamız gerekir: **NoSQL**.

**NoSQL**, “Not Only SQL” diye açılımı olan yaygın ve çok büyük veri setleri için çok kullanışlı bir veri yönetimi ve veritabanı tasarımı yaklaşımıdır. NoSQL, geniş alanları kapsayan teknolojilerin ve mimarilerinin ölçeklenebilirlik ve büyük veri performansı konusunda çözümler arar. NoSQL, özellikle bir kurumun masif sayıdaki yapısız verilere erişme ve analiz etme ihtiyacını karşılar.

İsminden anlaşılanın tam aksine, NoSQL SQL’i önlemez. NoSQL sistemleri tamamen ilişkisel olmayan şekildededir. Diğerleri tablo şemaları ve join operasyonları gibi belirli ilişkisel fonksiyonları kullanmaktan kaçınır. Örneğin bir NoSQL veritabanı , tabloları kullanmasına rağmen verileri anahtar­değer veya demetler(t uples) ş eklinde organize edebilir.

Tartışmasız en popüler NoSQL veritabanı **Apache Cassandra**’dır. Cassandra, 2008’de açık kaynak kodlu yayımlanan ve Facebook tarafından kullanılan yaygın bir veritabanıdır. Diğer NoSQL implementasyonları ise SimpleDB, Google BigTable, Apache Hadoop, MapReduce, MemcacheDB and Voldemort. Netflix, LinkedIn ve Twitter, NoSQL’i kullanan başlıca şirketlerdendir.

MongoDB ise, C++ dili ile yazılmış, yüksek performans, yüksek kullanılabilirlik ve otomatik ölçeklenebilirlik sağlayan açık kaynak ve belge tabanlı (document  database) bir NOSQL veritabanı uygulamasıdır. MongoDB, bir Nesne­ İlişkisel Haritalama (ORM) ihtiyacını ortadan kaldırarak geliştirmeyi kolaylaştırmaktadır.

### Belgeler (Documents)

MongoDB’deki bir kayıt, alan ve değer eşlemesinden oluşan bir veri yapısına sahip bir belgedir. Bu özelliği ile MongoDB belgeleri, JSON nesneleriyle benzerlik gösterir. Alanların değerleri diğer bir alanı, diziyi vyea belgelerin dizilerini içerebilir.

![MongoDB'de key-value eşlemesi](/assets/images/post-images/mongodb.png)

#### 1. Yüksek Performans

MongoDB veri sürekliliğinde yüksek performans sağlar. Bilhassa,

Veritabanı sistemlerindeki giriş çıkıç aktivitelerinde azaltmalar yaparak gömülü veri modellerini destekler.
Kuyrukları hızlı bir şekilde indekslenmesi sağlar ve gömülü belgelerin ve dizilerin anahtarlarını içerir.

#### 2. Zengin Kuyruk Dili

MongoDB, okuma ve yazma işlemlerini zengin bir kuyruk diliyle sahip olduğu veri birleştirme(d ata aggregation) v e metin arama (t ext search) ö zellikleriyle destekler.

#### 3. Çoklu Saklama Motorlarını Destekleme

MongoDB; WiredTiger Storage Engine ve MMAPv1 Storage Engine gibi çoklu saklama motorlarını destekler.

Ayrıca MongoDB, saklama motoru geliştirmek için sonradan edinilebilen(p luggable) 3 . parti API’ler sunar.

#### 4. Yatay Ölçeklendirebilirlik

MongoDB, kendi çekirdek fonksiyonelliğinin bir parçası olan yatay ölçeklerilebilirlik sağlar.

#### 5. Yüksek Kullanılabilirlilik

MongoDB’nin “replica set” denilen bir çoğaltma sistemi vardır. Bu sistem:
* Otomatik yük devretme ve
* ­Veri fazlalığı
sağlar.

Bir “replica set”, aynı veri setlerinden oluşan, fazlalık sağlayan ve veri kullanılabilirliğini arttıran bir grup MongoDB sunucularıdır.
