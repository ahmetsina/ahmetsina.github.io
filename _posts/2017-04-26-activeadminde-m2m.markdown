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

[Activeadmin](http://activeadmin.info) Rails'de Modellerinize göre CRUD işlemleri yapabiliceğiniz sayfaları oluşturacak şekilde admin panel sunan güzel bir gem. Varsayılan tasarımı sitesinde gördüğünüz şekilde. Ben kurduktan sonra o tasarımı başka bir gemle değiştirdim:[Flat Skin](https://github.com/ayann/active_admin_flat_skin). Eğer siz de tasarımını değiştirmek isterseniz buradan farklı tasarımlara [buradan](https://github.com/paladini/activeadmin-themes) bakabilir ve uygulamanıza entegre edebilirsiniz.

Bu arada Activeadmin'in kendine has DSL yapısı var. **DSL**, aklınıza ADSL'i çağrıştırmış olabilir fakat o değil.
> _DSL (Domain Spesific Language), akla gelebilecek her türlü amaç veya konu için geliştirilmiş özelleştirilmiş dildir._

Activeadmin'deki DSL ise Ruby'nin özelleştirilmiş versiyonu. Birazdan kodlarda da daha rahat göreceğiz.

### Ruby on Rails'te many-to-many ilişkisi
Öncelikle Ruby on Rails'de **many to many** ilişkisi nasıl oluyor bir bakalım. Rails'in kendi [dokümantasyonunda](http://guides.rubyonrails.org/association_basics.html) olduğu gibi many-to-many ilişkisi şu şekilde kuruluyor. Benim ilişkim Haber ve Hategori modeli arasında oluşuyor.  <span class="evidence">Bir haber birden fazla kategoriye sahip olabilir ve bir kategoride de birden fazla haber olabilir.</span>
{% highlight ruby %}
class Haber < ApplicationRecord
  has_many :categorizations
  has_many :kategoriler, through :categorizations
  # Modelinizi oluştururken Türkçe çoğul olarak bu şekilde almasını istiyorsanız
  # config/initializers/inflections.rb dosyasında istisna olarak eklemeniz gerekmekte.
  # Örnek olarak:  inflect.irregular 'kategori', 'kategoriler'

  accepts_nested_attributes_for :kategoriler
  # kategorilerin içerdiği özellikleri kabul ediyoruz.
end

class Kategori < ApplicationRecord
  has_many :categorizations
  has_many :haberler, through :categorizations

  accepts_nested_attributes_for :haberler
  # haberlerin içerdiği özellikleri kabul ediyoruz.

end


class Categorization < ApplicationRecord # İlişkiyi oluşturan model
  belongs_to :haber
  belongs_to :kategori
end
{% endhighlight %}

Modelleriniz arasında ilişki kurmak istiyorsanız biraz daha basit ve hızlı bir çözümü daha var: [**Localtower**](https://github.com/damln/localtower).
O kadar basit bir gem ki ReadMe dosyasını okumaya bile gerek kalmıyor.☺

Modellerimizi oluşturup ilişkiyi de kurduktan sonra Activeadmin panelinde yer alması için komut satırından modellerimizi kayıt ettiriyoruz.
```zh
$> rails generate active_admin:resource Haber
```
```zh
$> rails generate active_admin:resource Kategori
```
Modellerimizi kayıt ettikten sonra admin panelinin menüsünde direk olarak modellerimiz gözükecek. Ve aynı zamanda projemizin `app/admin/haber.rb` ve `app/admin/kategori.rb` diye rb dosyalarımız oluşmuş olacak. Bu dosyalardan controller ve view'imizi rahatlıkla yönetebileceğiz. Fakat önceden de dediğim gibi Activeadmin'in biraz farklı bir syntaxı var.

`haber.rb` dosyamız en başta şu şekilde:
{% highlight ruby %}
ActiveAdmin.register Haber do

# permit_params methodu ile değiştirilebilir değerlerimizi belirtiyoruz.
# https://github.com/activeadmin/activeadmin/blob/master/docs/2-resource-customization.md#setting-up-strong-parameters
#
permit_params :title, :body, :image
#
index title: "Haberler" do
    selectable_column
    column "Resim", :image, max_width: "100px" do |img|
        image_tag img.image_url(:thumb)
    end
    column "Başlık", :title
    column "Olusturulma Tarihi", :created_at
    actions
end
form do |f|
      f.inputs 'Haber İçeriği', :multipart => true do
        f.input :title, label:  "Haber Başlığı"
        f.input :body,  label: "Haber Açıklaması"
        f.input :image, :as => :file
        f.input :kategoriler, :as => :check_boxes, :collection => Kategori.all
      end
    end
	f.actions
end
{% endhighlight %}

Yukarıdaki `haber.rb` dosyamızı bir inceleyelim. `permit_params` methodu ile modelimizde var olan ve değeri değiştirilecek değişkenleri tanımlıyoruz. Yani formdan bir kayıt alındığında veya değişiklik yapıldığında `permit_params` ın daha önceden bu değişkenlerden haberi olmalı.

index blokunda ise var olan model değerlerimizin listelendiği veya gösterildiği yer. Seçilebilir bir tablo oluşturuluyor zaten ilk modelimizi kayıt ettirdiğimizde zaten. İsterseniz bu tabloları değiştirebilir index sayfasını kendinize göre ayarlayabilirsiniz.

Form bölümü ise haber girdiğimiz yer. Multipart özelliği resim, dosya vb. kayıtları yapmamızı sağlıyor. Zaten gördüğünüz gibi formda da input olarak dosya olarak resim ekleme yapıyoruz. Resim ekleme olayı Burada asıl mevzu bizim için kategori girilmesi. Haberin hangi kategorilere dahil olduğunu göstermek için bir checkbox oluşturduk. Ve checkboxda olmasını istediğimiz değerleri de `:collection => Kategori.all` yazarak bütün kategori değerlerini gösterecek şekilde ayarladık.

Asıl patladığım olay ise bunların habere bağlanması olayı. Tabi ki önceliğim activeadminin kendi dokümantasyonuna baktım sonra stackoverflow'da soruları inceledim. En sonunda Özgür Yazılım Günleri'nde tanıştığımız [Eyüp Atış](https://github.com/eyupatis) ve [Göktuğ Göktaş](https://github.com/goktuggoktas)'a sormuştum. Onlar da sorunun neyle alakalı olduğunu söylediler ve o şekilde araştırma yapınca olayı çözdüm. Çözüm basitmiş: `permit_params` methoduna `kategori_ids[]` eklemek. Yani şöyle olacak:
{% highlight ruby %}
  permit_params :title, :body, :image, :kategori_ids[]
{% endhighlight%}
 Çünkü burada yaptığımız işlemde bir habere birden fazla kategori yapacağımızdan o habere birden fazla kategorinin idsini giriyoruz. Çekme işlemi de aynı şekilde gerçekleşiyor.

Kategoriler eklendikten sonraki adım ise bunları göstermek. Bunun için de [Eileen Uchitelle](https://github.com/eileencodes)'ın takip ettiğim blogunun [şu yazısından](http://eileencodes.com/posts/has-many-relationships-in-activeadmin/) faydalandım.
{% highlight ruby %}
column :categories do |post|
    table_for post.categories.order('title ASC') do
      column do |category|
        link_to category.title, [ :admin, category ]
      end
    end
  end
{% endhighlight %}

Bu kod bloğu Eileen'inkine göre yapmam gereken kısımdı. Fakat bir sıkıntı vardı ki o da `table_for` methodu. Benim kategorilerim zaten tablonun bir hücresinde tutuluyordu. Ben virgülle veya boşlukla onların gösterilmesini istiyordum. `table_for` methodu ise o hücrede yeni bir tablo oluşturuyordu. Bu sorunu da çözmem için stackoverflow'a başvurdum ve tam istediğim gibi çözüm buldum. Soruya ve cevabına [buradan](http://stackoverflow.com/questions/15799566/how-do-add-a-link-to-an-activeadmin-view) bakabilirsiniz... Bu çözümle birlikte ben de şu şekilde kodu değiştirdim.
{% highlight ruby %}
column "Kategoriler", :kategoriler do |haber|
  haber.kategoriler.each.map do |category|
      link_to category.name, [ :admin, category ]
  end.join(', ').html_safe
end
{% endhighlight %}

Bu kod satırıyla birlikte Haberler tablomuzdaki kategoriler hücresi şu şekilde:
![Kategorilerin hücredeki şekli](/assets/images/post-images/active-admin-mam.png)

Bu aşamalarla birlikte many-to-many ilişkisinin en azından Rails ve Activeadmin'deki işleyişini görmüş oldum. Umarım size de faydalı olmuştur.. :)
