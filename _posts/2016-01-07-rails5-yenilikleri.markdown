---
title: "Rails 5 Yenilikleri"
layout: post
date: 2016-07-01 22:44
image: weblog.rubyonrails.org/images/rails-logo.svg
headerImage: http://weblog.rubyonrails.org/images/rails-logo.svg
tag:
- rails
- ruby
blog: true
author: ahmetsina
description: Rails 5. sürümü ile gelen yenilikler
---


Ruby’nin en iyi web geliştirme frameworklerinden biri olan Rails bugün yeni sürümünü duyurdu. Bu sürümdeki yenilikler nedir, hangi işimize yarar biraz bundan bahsedeceğim.

4 beta, 2 aday sürümle birlikte 6 aylık parlatmadan sonra Rails 5 sonunda tamamlandı. Yüzlerce katkı sağlayanı ve binlerce commiti bulunan Rails 5 hiç şüphesiz bütün sürümlere nazaran şuanda en iyi sürüm. Bu topluluğun hala bunun üzerinde yoğun çaba sarf etmesi gerçekten inanılmaz.

Ve gelelim yeniliklere.. 2 tane baş tacı yenilik getirilmiş. Action Cable ve API Mode..

## Action Cable
**Action Cable**, Rails’te WebSocket kullanımını sağlayan yepyeni bir framework. Bağlantıları düzenleme için tamamen bütünleşmiş bir çözüm, sunucu taraflı işlemler için kanallar katmanı ve istemci etkileşimleri için de JavaScript katmanı içeren bir yapıya sahip. Chat, bildirim gibi anlık işlemleri rahatlıkla uygulama imkanı sunan ve kullanımı da oldukça kolay. Bu yeniliklerin demosuna da göz atmak istiyorsanız BaseCamp 3 sitesine bir uğrayın derim.

Action Cable’ın asıl sevimli tarafı WebSocket çalışmanızda size Active Record ve PORO domain modele erişimi sağlaması. Websocket cevapları için sunucu taraflı şablonları tekrar kullanmak istediğinizde önemsiz şablonlarınızı controller olmadan da render yapmanızı sağlayan ActionController::Renderer sistemi bile eklenmiş.

## API Mode

HTML şablonlarını sunucu tarafında renderlayan bir full-stack uygulama yapmak istiyorsanız, Rails sadece iyi bir seçim değildir. Ayrıca arka planda sadece JSON formatına ihtiyaç duyduğunuz istemci taraflı Javascript veya native uygulamalar için de bir yoldaştır. Bunun için de Rails ekibi yeni bir -api mode yapmış.

**rails new backend --api** ile yapmış olduğunuz yeni uygulama, size HTML ile değil, JSON ile çalışabileceğiniz daha hafif bir iskelet ve ayarlama sunar. Bu yeniliğin üzerinde hala çalışılıyor ama iyi bir başlangıç yapıldı. Varsayılan olarak API Mode model sınıflarında **to_json**‘ı çağırmasına dayanır. Fakat daha gelişmiş çözümler için Jbuilder, Active Model Serializers ve yeni olan JSONAPI::Resources projelerine bakılabilir.
