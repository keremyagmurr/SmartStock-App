# Yol haritası

[← README](../README.md)

Proje **12 ay** sürer ve **altı iş paketiyle** yürütülür. Her iş paketinin ölçülebilir başarı ölçütleri vardır; testleri geçmeyen bir iş paketi tamamlanmış sayılmaz. İlerleme her iş paketi sonunda danışmanla değerlendirilir.

## İçindekiler

- [Zaman çizelgesi](#zaman-çizelgesi)
- [Ayrıntılı iş paketleri](#ayrıntılı-iş-paketleri)
- [Risk yönetimi](#risk-yönetimi)
- [Kapsam dışı](#kapsam-dışı)
- [Araştırma olanakları](#araştırma-olanakları)
- [Beklenen çıktılar ve yaygın etki](#beklenen-çıktılar-ve-yaygın-etki)

## Zaman çizelgesi

| İş paketi | Ay 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | Katkı |
|---|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| İP-1 Çok kiracılı veri modeli ve kimlik doğrulama | ■ | ■ | | | | | | | | | | | %15 |
| İP-2 Stok ve üretim çekirdeği | | | ■ | ■ | | | | | | | | | %20 |
| İP-3 Ticari işlemler | | | | | ■ | ■ | | | | | | | %20 |
| İP-4 Çok satıcılı pazaryeri | | | | | | | ■ | ■ | ■ | | | | %25 |
| İP-5 YZ asistanı | | | | | | | | | | ■ | | | %10 |
| İP-6 Bütünleşik doğrulama | | | | | | | | | | | ■ | ■ | %10 |

<sub>Katkı: iş paketinin araştırmanın başarısına katkısı (toplam %100).</sub>

## Ayrıntılı iş paketleri

### İP-1 · Çok kiracılı veri modeli, kimlik doğrulama ve yetki altyapısı <sub>Ay 1–2</sub>

Şirket, üyelik, rol ve davet tablolarının, RLS politikalarının ve yetki yardımcı fonksiyonlarının yazılması; e-posta ve Google (PKCE) ile giriş; şirket kurma/davetle katılma; etkin şirket seçimi ve rol bazlı menü; ortak model ve veri erişim katmanı.

> **Başarı ölçütü:** Bu iş paketinde oluşturulan tüm tablolarda RLS etkin; kiracı yalıtım testlerinin %100'ü geçer; Android'de iki giriş yöntemi ve üç rolün menüsü çalışır.

### İP-2 · Stok ve üretim çekirdeği <sub>Ay 3–4</sub>

Malzeme ve ürün kartları, gerekçeli sayım düzeltmesi, reçete düzenleyici, azami üretim hesabı ve atomik üretim fonksiyonu; karekod/barkod etiket üretimi, kamerayla kod okuma ve okunan koda göre rol bazlı işlem penceresi.

> **Başarı ölçütü:** Üretim fonksiyonu testleri (başarılı, yetersiz malzeme, yetkisiz rol) geçer; normal ışıkta test etiketlerinin en az %95'i ilk denemede okunur.

### İP-3 · Ticari işlemler <sub>Ay 5–6</sub>

Tedarikçi (IBAN doğrulamalı) ve müşteri (kredi limitli) kayıtları; satın alma siparişi ve kısmi mal kabul; peşin/vadeli satış; vade sıralı cari; tahsilat/ödeme; eksiye düşmeyen kasa; ters kayıtla iptal; ana sayfa uyarıları, işlem kaydı ve kullanıcı yönetimi.

> **Başarı ölçütü:** En az 200 işlemlik karma senaryoda stok–cari–kasa mutabakat farkı 0; ilgili fonksiyon testlerinin %100'ü geçer.

### İP-4 · Çok satıcılı pazaryeri <sub>Ay 7–9</sub>

Satıcı başvurusu ve platform onayı; mağaza ayarları ve ürün yayını; vitrin, arama ve ürün sayfası; satıcı bazlı sepet ve sipariş bölme; 30 dakikalık stok ayırma; test ortamında kartla ödeme; sipariş durum akışı ve gerçek zamanlı bildirimler; iptal/iade talepleri; kategori komisyonu ve hakediş.

> **Başarı ölçütü:** Uçtan uca sipariş senaryolarının %100'ü tamamlanır; 20 eşzamanlı alıcı testinde fazla satış 0; hakediş tutarları komisyon kuralıyla birebir tutar.

### İP-5 · Rol kısıtlı, salt okunur YZ asistanı <sub>Ay 10</sub>

Rol bazlı salt okunur veri özetleri, sunucu fonksiyonu üzerinden dil modeli çağrısı, sohbet arayüzü ve kural tabanlı yedek yanıt motoru.

> **Başarı ölçütü:** Üç rol için en az 60 soruluk (rol başına en az 20) test setinde rol dışı veri sızıntısı 0; yetkili sorularda doğru yanıt oranı en az %90.

### İP-6 · Bütünleşik doğrulama <sub>Ay 11–12</sub>

Karşılaştırma sürümleriyle tutarlılık ve yetkisiz erişim testleri, performans ölçümü, simülasyonla davranış karşılaştırması, kamera/manuel görev süresi deneyi ve SUS anketi, en az bir işletmede iki haftalık pilot kullanım; bulgulara göre iyileştirme.

> **Başarı ölçütü:** Tanımlı yetkisiz erişim senaryolarının %100'ü engellenir; bulut ortamında 95. yüzdelik yanıt süresi 500 ms'nin altında; kamerayla süre kazancı en az %30 (p < 0,05); ortalama SUS en az 70.

## Risk yönetimi

B planlarının hiçbiri projenin temel hedeflerinden sapmaya yol açmaz.

| Risk | B planı |
|---|---|
| **1 · Eşzamanlı işlemlerde yarış durumu**<br><sub>Stoğun veya kasanın eksiye düşmesi, pazaryerinde fazla satış</sub> | Hiçbir işlem istemcide hesaplanıp yazılmaz; satır kilitleyen atomik fonksiyonlar ve `stok ≥ 0`, `kasa ≥ 0` kısıtları. Pazaryerinde stok sipariş anında ayrılır. Testte hata bulunursa ilgili fonksiyonun kilit sırası düzeltilip test yinelenir; yöntem değişmez. |
| **2 · Kamerayla kod okumanın başarısız olması**<br><sub>Düşük ışık, odaklama, yıpranmış etiket</sub> | Kamera zorunlu değildir, tüm işlemler manuel tamamlanabilir. Etiketler yüksek hata düzeltme düzeyiyle üretilir, fener uygulamadan açılabilir. Okuma başarısı hedefin altında kalırsa farklı bir açık kaynak okuma kütüphanesi denenir; H2 deneyi standart ışık koşullarında yapılır. |
| **3 · YZ asistanının hatalı ya da yetkisiz bilgi vermesi**<br><sub>Halüsinasyon, rol dışı yanıt, dış hizmete erişilememesi</sub> | Asistana yazma ve tablo okuma yetkisi verilmez; yalnızca sunucuda üretilen rol süzülmüş özet verilir. Dış hizmete erişilemezse kural tabanlı niyet sınıflandırıcı devreye girer. Sızıntı testi başarısız olursa önce ilgili özet alanı kaldırılır; yine başarısız olursa asistan kural tabanlı modda sunulur. Yalnızca yanıt üretme yöntemi değişir; salt okunurluk ve rol sınırlaması korunur. |
| **4 · İstemci tarafında yetkinin aşılması ya da gizli anahtar sızıntısı** | Yetki yalnızca arayüzde bırakılmaz; RLS ve fonksiyon içi rol denetimi asıl güvenlik katmanıdır. İstemcide yalnızca herkese açık anahtar bulunur; yönetici anahtarları sürüm kontrolüne girmez ve şüphede yenilenir. |
| **5 · Ödeme kuruluşu test ortamına erişimde gecikme** | Ödeme katmanı bir arayüzle soyutlanır; önce demo sağlayıcıyla başarılı, başarısız, iptal, iade ve hakediş senaryolarının tamamı sınanır. Test ortamı zamanında açılmazsa değerlendirme demo sağlayıcıyla yapılır. |
| **6 · Katılımcı veya pilot işletme bulunamaması, takvim gecikmesi** | 20 kişiye ulaşılamazsa en az 12 katılımcıyla Wilcoxon testi uygulanır ve sınırlılık raporlanır. İşletme bulunamazsa pilot kullanım, günlük iş akışlarını canlandıran gönüllülerle laboratuvarda yapılır. Gecikmede öncelik çekirdek akışlara (İP-1 – İP-3) verilir. |

## Kapsam dışı

- Gerçek banka ve kargo entegrasyonu (ödemeler test ortamında sınanır, kargo takip numarası elle girilir)
- e-Fatura / e-Arşiv, KDV hesaplaması
- Çoklu para birimi (yalnızca TL), çoklu depo
- Çevrim dışı eşzamanlama
- Uygulama mağazalarında yayın
- Satıcı belgelerinin otomatik doğrulanması (platform panelinde elle onaylanır)

## Araştırma olanakları

| Altyapı / ekipman | Kullanım amacı |
|---|---|
| Bilgisayar laboratuvarları | Kullanılabilirlik deneyleri, görev süresi ölçümleri, çok istemcili eşzamanlılık testleri |
| Geliştirme bilgisayarı (.NET 10 SDK ve MAUI iş yükü, Android SDK ve emülatör, konteynerde yerel PostgreSQL arka ucu, Git) | Mobil ve web kodlaması, yerel veritabanı geliştirme, otomatik testler, sürüm kontrolü |
| Kameralı Android akıllı telefon | Gerçek cihazda kod okuma, bildirim ve kullanılabilirlik testleri |
| Bulut arka uç hizmeti (ücretsiz katman) ve ödeme kuruluşunun test ortamı | Çok kullanıcılı pilot kullanım, gerçek zamanlı bildirim, kartla ödeme ve hakediş akışları |
| Büyük dil modeli API erişimi (deneme kotası) | YZ asistanının geliştirilmesi ve test setiyle değerlendirilmesi |
| Yazıcı ve etiket kâğıdı | Karekod/barkod etiketlerinin basılması ve okuma testleri |

## Beklenen çıktılar ve yaygın etki

| Kategori | Çıktı |
|---|---|
| **Bilimsel / akademik** | Mimariyi, RLS ile kiracı yalıtımını ve deney bulgularını sunan en az 1 ulusal hakemli kongre bildirisi (proje bitimini izleyen 6 ay içinde başvuru) |
| | Deney verilerini ve güvenlik test kataloğunu içeren 1 hakemli dergi makalesi taslağı |
| | Bilgisayar Mühendisliği bitirme projesi tezi ve teknik rapor |
| **Ekonomik / ticari / sosyal** | Çalışan prototip: Android uygulama, web pazaryeri ve bulut arka uç; iki örnek şirketle hazır demo verisi |
| | En az bir küçük üretim işletmesinde iki haftalık pilot kullanım ve geri bildirim raporu |
| | Lisans maliyeti olmadan stok kayıt hatalarının, malzeme eksikliğinden doğan üretim aksamalarının ve vade takibindeki aksaklıkların azaltılması; küçük üreticilerin çevrim içi satışa açılması |
| | Sade arayüz ve doğal dil asistanıyla çalışanların dijital becerilerinin gelişmesi, kâğıt kayıt kullanımının azalması |
| **Yeni projeler** | Hizmet olarak yazılım (SaaS) modeliyle ticarileştirme için TÜBİTAK 1512 Girişimcilik Destek Programı (BiGG) başvurusu |
| | E-fatura entegrasyonu, çoklu depo, çevrim dışı eşzamanlama ve geçmiş satış verisiyle talep tahmini konularında yeni bir araştırma projesi önerisi (ör. TÜBİTAK 1002) |

---

[Araştırma](arastirma.md) · [Mimari](mimari.md)
