# CSV Audit Workbench

Jira CSV export dosyalarını analiz eden, tamamen tarayıcı içinde çalışan tek dosyalık bir audit aracı.

## 🎯 Amaç

Bu proje, ekiplerin Jira'dan dışa aktardığı issue listelerini hızlıca kontrol etmesi için tasarlandı. Araç her issue'yu yerelde inceler ve eksik ya da hatalı noktalar için açık gerekçeler üretir.

Kontrol edilen başlıklar özetle:

- issue type uygun mu
- geçerli component var mı
- description içinde zorunlu başlıklar mevcut mu
- description içinde Confluence linki var mı
- hariç tutulan label varsa issue audit dışı mı sayılmalı

## ⚙️ Nasıl Çalışır

Uygulama tamamen tarayıcıda çalışır. Jira API, token veya sunucu taraflı bir servis gerekmez.

Akış şu şekildedir:

1. Jira'da issue listesini aç.
2. `Export Excel CSV (all fields)` ile CSV dosyasını indir.
3. Repo içindeki `index.html` dosyasını tarayıcıda aç.
4. CSV dosyasını sürükle-bırak veya seç.
5. Araç CSV kolonlarını tanır, her satırı kurallara göre analiz eder ve sonucu tabloda gösterir.
6. İstersen filtreleme yapıp sonucu tekrar CSV olarak dışa aktarabilirsin.

## ✨ Özellikler

- Tek dosyalı istemci tarafı uygulama
- Kuralları `Ayarlar` ekranından güncelleme
- Sonuçları filtreleme ve sıralama
- Issue detaylarını drawer içinde inceleme
- Filtrelenmiş sonucu CSV olarak indirme
- Ayarları tarayıcıdaki `localStorage` alanında saklama

## 📄 Beklenen Veri

Araç, Jira'nın CSV export formatını hedefler.

Zorunlu kolonlar:

- `Issue Key`
- `Summary`

Desteklenen ek kolonlar:

- `Issue Type`
- `Component/s`
- `Description`
- `Labels`

Kolon tespiti yaygın başlık varyasyonları, küçük-büyük harf farkları ve BOM gibi giriş farklılıklarına toleranslıdır.

## 🔧 Yapılandırma

`Ayarlar` ekranından şu alanları değiştirebilirsin:

- geçerli issue type listesi
- geçerli component listesi
- audit dışı label listesi
- Confluence domain
- description içinde zorunlu olan başlıklar
- opsiyonel Jira Base URL

## 🔒 Güvenlik ve Gizlilik

- Tüm analiz yerel olarak tarayıcıda yapılır.
- Jira veya Confluence'a otomatik istek atılmaz.
- API token gerekmez.
- Veriler tarayıcıdan dışarı gönderilmez.
- Ayarlar yalnızca kullandığın tarayıcının `localStorage` alanında tutulur.

## ▶️ Çalıştırma

Build adımı yoktur. Bağımlılık yoktur.

`index.html` dosyasını açman yeterlidir.
