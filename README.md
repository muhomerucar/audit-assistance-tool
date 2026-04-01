# CSV Audit Workbench

Standalone bir HTML araci olarak Jira CSV export dosyalarini analiz eder ve issue'larin belirli audit kurallarina uyup uymadigini gosterir.

## Amaci

Bu proje, ekiplerin Jira'dan disa aktardigi issue listelerini hizlica kontrol etmesi icin tasarlandi. Arac, her issue'yu yerelde inceler ve eksik ya da hatali noktalar icin acik gerekceler uretir.

Kontrol edilen basliklar ozetle:

- issue type uygun mu
- gecerli component var mi
- description icinde zorunlu basliklar mevcut mu
- description icinde Confluence linki var mi
- haric tutulan label varsa issue audit disi mi sayilmali

## Nasil Calisir

Uygulama tamamen tarayicida calisir. Jira API, token veya sunucu tarafli bir servis gerekmez.

Akis su sekildedir:

1. Jira'da issue listesini ac.
2. `Export Excel CSV (all fields)` ile CSV dosyasini indir.
3. Repo icindeki `index.html` dosyasini tarayicida ac.
4. CSV dosyasini surukle-birak veya sec.
5. Arac CSV kolonlarini tanir, her satiri kurallara gore analiz eder ve sonucu tabloda gosterir.
6. Istersen filtreleme yapip sonucu tekrar CSV olarak disa aktarabilirsin.

## Ozellikler

- Tek dosyali istemci tarafi uygulama
- Kurallari `Ayarlar` ekranindan guncelleme
- Sonuclari filtreleme ve siralama
- Issue detaylarini drawer icinde inceleme
- Filtrelenmis sonucu CSV olarak indirme
- Ayarlari tarayicidaki `localStorage` alaninda saklama

## Beklenen Veri

Arac, Jira'nin CSV export formatini hedefler. Zorunlu kolonlar:

- `Issue Key`
- `Summary`

Desteklenen ek kolonlar:

- `Issue Type`
- `Component/s`
- `Description`
- `Labels`

Kolon tespiti yaygin baslik varyasyonlari, kucuk-buyuk harf farklari ve BOM gibi giris farkliliklarina toleranslidir.

## Yapilandirma

`Ayarlar` ekranindan su alanlari degistirebilirsin:

- gecerli issue type listesi
- gecerli component listesi
- audit disi label listesi
- Confluence domain
- description icinde zorunlu olan basliklar
- opsiyonel Jira Base URL

## Guvenlik ve Gizlilik

- Tum analiz yerel olarak tarayicida yapilir.
- Jira veya Confluence'a otomatik istek atilmaz.
- API token gerekmez.
- Veriler tarayicidan disari gonderilmez.
- Ayarlar yalnizca kullandigin tarayicinin `localStorage` alaninda tutulur.

## Calistirma

Build adimi yoktur. Bagimlilik yoktur.

`index.html` dosyasini acman yeterlidir.
