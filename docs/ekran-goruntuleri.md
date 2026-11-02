# Ekran görüntüleri

[← README](../README.md)

## Ön çalışma hakkında

Önerinin uygulanabilirliğini göstermek için sistemin iki bileşeni, yerel sunucuda çalışan **PHP tabanlı birer arayüz ve iş mantığı simülasyonu** olarak geliştirilip test edilmiştir. Bu sayfadaki tüm görüntüler bu simülasyonlardan alınmıştır.

| Simülasyon | Kapsam |
|---|---|
| **Mobil uygulama** | Yönetici, Satıcı ve Depo/Üretim rolleri arasında anlık geçiş; telefon boyutlu çerçevede **30'dan fazla ekranın** rol bazlı davranışı. Malzeme ve ürün kayıtları, reçete ve azami üretim hesabı, sayım düzeltmesi, kamera okuma senaryoları (kayıtlı ürün, kayıtlı malzeme, tanımsız kod), etiket üretimi, satın alma ve kısmi mal kabul, kredi limiti kontrollü satış, vade takibi, tahsilat/ödeme, ters kayıtla iptal, davet koduyla şirkete katılım, işlem kaydı, CSV dışa aktarma ve rol kısıtlı asistan yanıt kuralları. |
| **Pazaryeri** | Katalog ve kategori listeleri, ürün sayfası, satıcı bazlı sepet, adres ve fatura bilgileriyle ödeme adımı, demo kart ödemesi, sipariş ve kargo takibi, iptal/iade talepleri, müşteri hesabı, e-posta önizlemesi ve yasal metin sayfaları. |
| **Ortak veri** | İki simülasyon aynı oturum verisini kullandığından sipariş onayı, kargoya verme, teslim ve iade akışları iki taraf arasında birlikte doğrulanmıştır. |
| **Test** | HTTP istekleriyle uçtan uca senaryoları çalıştıran otomatik test betikleri, kullanıcı girdilerinin sayfaya kaçışlı basıldığını denetleyen güvenlik testleri ve telefon genişliğinde (390 px) görsel denetimler. Son sürümde PHP uyarısı alınmamıştır. |

> [!NOTE]
> Simülasyonlar akışları, iş kurallarını ve rol yetkilerini doğrulamak içindir; hedef sistem [.NET MAUI ve Supabase](mimari.md) ile geliştirilecektir. Simülasyonların kaynak kodu bu repoda yer almaz. Ekranlardaki şirket, kişi, adres ve tutarlar örnek verilerdir.

## İçindekiler

- [Giriş ve ana sayfa](#giriş-ve-ana-sayfa)
- [Depo ve üretim](#depo-ve-üretim)
- [Kod okuma ve etiket](#kod-okuma-ve-etiket)
- [Satın alma, satış, cari ve kasa](#satın-alma-satış-cari-ve-kasa)
- [Web satış (mobil taraf)](#web-satış-mobil-taraf)
- [Yönetim ve YZ asistanı](#yönetim-ve-yz-asistanı)
- [Rollere göre karşılaştırma](#rollere-göre-karşılaştırma)
- [SmartShop pazaryeri](#smartshop-pazaryeri)

---

## Giriş ve ana sayfa

<table>
  <tr>
    <td align="center" width="25%"><img src="screenshots/mobile/00-giris.png" alt="Giriş ekranı"><br><sub><b>Giriş</b><br>E-posta/şifre; yeni işletme kaydı</sub></td>
    <td align="center" width="25%"><img src="screenshots/mobile/01-ana-sayfa-yonetici.png" alt="Yönetici ana sayfası"><br><sub><b>Ana sayfa</b><br>Kasa, aylık satış, kritik stok, geciken borç, bekleyen sipariş ve mal kabul</sub></td>
    <td align="center" width="25%"><img src="screenshots/mobile/03-uyarilar.png" alt="Uyarılar"><br><sub><b>Uyarılar</b><br>Vadesi geçen borç, yaklaşan alacak</sub></td>
    <td align="center" width="25%"><img src="screenshots/mobile/02-menu-yonetici.png" alt="Yönetici menüsü"><br><sub><b>Menü</b><br>Role göre karo listesi</sub></td>
  </tr>
</table>

## Depo ve üretim

<table>
  <tr>
    <td align="center" width="25%"><img src="screenshots/mobile/04-depo.png" alt="Depo"><br><sub><b>Depo</b><br>Kategorili malzeme listesi, arama ve sıralama</sub></td>
    <td align="center" width="25%"><img src="screenshots/mobile/05-malzeme-karti.png" alt="Malzeme kartı"><br><sub><b>Malzeme kartı</b><br>Stok, uyarı eşiği, son alış fiyatı, bekleyen sipariş ve kullanıldığı ürünler</sub></td>
    <td align="center" width="25%"><img src="screenshots/mobile/06-uretim.png" alt="Üretim"><br><sub><b>Üretim</b><br>Kategorili ürün listesi</sub></td>
    <td align="center" width="25%"><img src="screenshots/mobile/07-urun-recete.png" alt="Ürün kartı ve reçete"><br><sub><b>Ürün kartı</b><br>Reçete, depodaki miktarlar ve üretilebilir azami adet</sub></td>
  </tr>
  <tr>
    <td align="center"><img src="screenshots/mobile/10-uretim-onayi.png" alt="Üretim onayı"><br><sub><b>Üretim onayı</b><br>Her kalem için önce / sonra stok</sub></td>
    <td></td><td></td><td></td>
  </tr>
</table>

## Kod okuma ve etiket

<table>
  <tr>
    <td align="center" width="25%"><img src="screenshots/mobile/08-kamera-okuma.png" alt="Kayıtlı ürün bulundu"><br><sub><b>Kayıtlı ürün okutuldu</b><br>Üret · Sat · Reçete</sub></td>
    <td align="center" width="25%"><img src="screenshots/mobile/12-tanimsiz-kod.png" alt="Tanımsız kod"><br><sub><b>Tanımsız kod</b><br>Yeni malzeme ya da ürün kaydı</sub></td>
    <td align="center" width="25%"><img src="screenshots/mobile/09-etiket.png" alt="Etiket"><br><sub><b>Etiket</b><br>SVG indirme ve yazdırma<br><i>(simülasyonda temsili desen)</i></sub></td>
    <td width="25%"></td>
  </tr>
</table>

## Satın alma, satış, cari ve kasa

<table>
  <tr>
    <td align="center" width="25%"><img src="screenshots/mobile/13-satin-alma.png" alt="Satın alma"><br><sub><b>Satın alma</b><br>Bekleyen, geciken, açık borç</sub></td>
    <td align="center" width="25%"><img src="screenshots/mobile/14-satin-alma-detay.png" alt="Satın alma siparişi ve mal kabul"><br><sub><b>Sipariş ve mal kabul</b><br>Kısmi teslimat, irsaliye no</sub></td>
    <td align="center" width="25%"><img src="screenshots/mobile/15-satis.png" alt="Satış"><br><sub><b>Satış</b><br>Peşin, vadeli, web, iptal</sub></td>
    <td align="center" width="25%"><img src="screenshots/mobile/16-cari.png" alt="Cari hesap"><br><sub><b>Cari hesap</b><br>Vade sıralı borç ve alacak</sub></td>
  </tr>
  <tr>
    <td align="center"><img src="screenshots/mobile/17-kasa.png" alt="Kasa"><br><sub><b>Kasa</b><br>Giriş/çıkış hareketleri, komisyon kesintisi</sub></td>
    <td></td><td></td><td></td>
  </tr>
</table>

## Web satış (mobil taraf)

<table>
  <tr>
    <td align="center" width="25%"><img src="screenshots/mobile/18-web-satis.png" alt="Web satış"><br><sub><b>Web Satış</b><br>Mağaza ayarları ve yayındaki ürünler</sub></td>
    <td align="center" width="25%"><img src="screenshots/mobile/20-web-siparisleri-yeni.png" alt="Yeni web siparişi"><br><sub><b>Yeni web siparişi</b><br>Onayla ve stoktan düş</sub></td>
    <td align="center" width="25%"><img src="screenshots/mobile/21-web-siparisleri-kargoda.png" alt="Kargodaki web siparişi"><br><sub><b>Kargodaki sipariş</b><br>Tutar, komisyon, satıcıya kalan<br><i>(komisyon oranı örnektir)</i></sub></td>
    <td width="25%"></td>
  </tr>
</table>

## Yönetim ve YZ asistanı

<table>
  <tr>
    <td align="center" width="25%"><img src="screenshots/mobile/22-kullanicilar.png" alt="Kullanıcılar"><br><sub><b>Kullanıcılar</b><br>Personel, roller, süreli davet kodları</sub></td>
    <td align="center" width="25%"><img src="screenshots/mobile/23-log.png" alt="İşlem kaydı"><br><sub><b>İşlem kaydı</b><br>Kim, ne zaman, manuel / kamera</sub></td>
    <td align="center" width="25%"><img src="screenshots/mobile/24-ayarlar.png" alt="Ayarlar"><br><sub><b>Ayarlar</b><br>Profil, bildirim, koyu tema, vade uyarısı</sub></td>
    <td align="center" width="25%"><img src="screenshots/mobile/25-asistan-yonetici.png" alt="YZ asistanı"><br><sub><b>YZ asistanı</b><br>Salt okunur, rol kısıtlı</sub></td>
  </tr>
</table>

## Rollere göre karşılaştırma

| | Yönetici | Satıcı | Depo/Üretim |
|---|:-:|:-:|:-:|
| **Ana sayfa** | <img src="screenshots/mobile/01-ana-sayfa-yonetici.png" width="180" alt="Yönetici ana sayfası"> | <img src="screenshots/mobile/30-ana-sayfa-satici.png" width="180" alt="Satıcı ana sayfası"> | <img src="screenshots/mobile/40-ana-sayfa-depo.png" width="180" alt="Depo ana sayfası"> |
| **Menü** | <img src="screenshots/mobile/02-menu-yonetici.png" width="180" alt="Yönetici menüsü"> | <img src="screenshots/mobile/31-menu-satici.png" width="180" alt="Satıcı menüsü"> | <img src="screenshots/mobile/41-menu-depo.png" width="180" alt="Depo menüsü"> |
| **Ürün kartı** | <img src="screenshots/mobile/07-urun-recete.png" width="180" alt="Yönetici ürün kartı"> | <img src="screenshots/mobile/32-urun-satici.png" width="180" alt="Satıcı ürün kartı"> | <img src="screenshots/mobile/42-urun-depo.png" width="180" alt="Depo ürün kartı"> |
| **YZ asistanı / Tedarikçi** | <img src="screenshots/mobile/25-asistan-yonetici.png" width="180" alt="Yönetici YZ asistanı"> | <img src="screenshots/mobile/33-asistan-satici.png" width="180" alt="Satıcı YZ asistanı"> | <img src="screenshots/mobile/43-tedarikci-depo.png" width="180" alt="Depo tedarikçi listesi"> |

Ayrıntılı yetki matrisi: [Güvenlik ve roller](guvenlik-ve-roller.md#rol-ve-yetki-matrisi).

## SmartShop pazaryeri

Müşterinin uçtan uca alışverişi: vitrinden ürüne, sepetten ödemeye, onay e-postasından kargo takibine.

<table>
  <tr>
    <td align="center" width="50%"><img src="screenshots/web/01-vitrin.png" alt="Vitrin"><br><sub><b>1 · Vitrin</b></sub></td>
    <td align="center" width="50%"><img src="screenshots/web/02-katalog.png" alt="Katalog"><br><sub><b>2 · Katalog</b>: kategori, fiyat ve stok filtresi; tükenen ürünler işaretli</sub></td>
  </tr>
  <tr>
    <td align="center"><img src="screenshots/web/03-urun.png" alt="Ürün sayfası"><br><sub><b>3 · Ürün sayfası</b>: stok depoyla ortak</sub></td>
    <td align="center"><img src="screenshots/web/04-sepet.png" alt="Sepet"><br><sub><b>4 · Sepet</b>: ücretsiz kargo eşiği</sub></td>
  </tr>
  <tr>
    <td align="center"><img src="screenshots/web/05-odeme-bilgileri.png" alt="Teslimat ve fatura"><br><sub><b>5 · Teslimat ve fatura</b>: bireysel/kurumsal fatura, yasal onaylar<br><i>Simülasyonda havale/EFT seçeneği de denenmiştir; hedef sistemde ödeme yalnızca kartla alınır.</i></sub></td>
    <td align="center"><img src="screenshots/web/06-guvenli-odeme.png" alt="Ödeme kuruluşu sayfası"><br><sub><b>6 · Ödeme</b>: kart bilgisi ödeme kuruluşunun sayfasında girilir (demo sağlayıcı)</sub></td>
  </tr>
  <tr>
    <td align="center"><img src="screenshots/web/07-siparis-alindi.png" alt="Sipariş alındı"><br><sub><b>7 · Sipariş alındı</b></sub></td>
    <td align="center"><img src="screenshots/web/08-onay-epostasi.png" alt="Onay e-postası"><br><sub><b>8 · Onay e-postası önizlemesi</b></sub></td>
  </tr>
  <tr>
    <td align="center"><img src="screenshots/web/09-siparis-takibi.png" alt="Sipariş takibi"><br><sub><b>9 · Sipariş takibi</b>: satıcı mobil uygulamadan onaylayıp kargoya verdikten sonra</sub></td>
    <td align="center"><img src="screenshots/web/10-vitrin-mobil.png" width="300" alt="Vitrin mobil görünüm"><br><sub><b>Mobil görünüm</b>: duyarlı tasarım</sub></td>
  </tr>
</table>

---

[İş akışları](is-akislari.md) · [Mimari](mimari.md)
