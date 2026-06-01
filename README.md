BenimYazilim Restaurant POS; kafe, restaurant, fast food ve benzeri isletmeler icin gelistirilen yerel ag destekli masaustu POS uygulamasidir. Masa adisyonu, garson siparis girisi, tahsilat, stok, mutfak/bar yonlendirme, QR menu, X/Z raporu ve analiz ekranlarini tek sistemde toplar.

Program musterinin bilgisayarina setup ile kurulur. Kullanici masaustundeki kisayola tiklar, uygulama kendi yerel servisini baslatir ve POS ekranini acarak masaustu program gibi calisir.

One cikan ozellikler
Masa yonetimi: isletmenin masa sayisi ayarlanabilir, masalar dolu/bos olarak izlenir.
Adisyon: masaya urun ekleme, adet artirma/azaltma, satir iptali, masa notu ve masa tasima.
Tahsilat: nakit, kart, parcali odeme, secili urun odemesi ve kisi bazli odeme akislari.
Garson hesaplari: kullanici adi/sifre ile personel girisi, her siparis kaleminde giren personel takibi.
Mutfak ve bar ekranlari: yemekler mutfaga, icecekler bara yonlendirilebilir.
Iptal takibi: satir iptali ve fis iptali raporlara detayli sekilde islenir.
Stok sistemi: urun bazli opsiyonel stok takibi, kritik stok ve stok hareketleri.
QR menu: musterinin telefonunda urun listesi, fiyat, aciklama ve fotograf gosterimi.
Raporlama: X raporu, Z raporu, nakit/kart dagilimi, satilan urunler, iptaller ve grafikler.
Analiz: yogun saatler, garson performansi, urun/kategori satislari ve isletme icin yorumlar.
Lisans sistemi: cihaz kimligi ile lisans aktivasyonu ve lisans durumu takibi.
Yedekleme altyapisi: yerel SQLite veri saklama ve gunluk/Z raporu yedekleri.
Guncelleme altyapisi: Velopack ile GitHub Releases uzerinden yeni surum yayinlama.
Surum
Guncel surum: 1.0.4

Bu surumle birlikte X/Z rapor mantigi kasa donemine gore duzenlendi. Z raporu alindiginda kasa kapanir ve sonraki X raporu yeni donemden baslar. Acik masalar ve acik siparisler korunur.

Kurulum
Musteri tarafinda ekstra Visual Studio, .NET SDK veya SQLite kurulumu gerekmez.

GitHub Releases bolumunden BenimYazilimCafePos-win-Setup.exe dosyasini indirin.
Setup dosyasini calistirin.
Masaustundeki BenimYazilim Restaurant POS kisayoluna tiklayin.
Ilk giris bilgileri:
Kullanici adi: admin
Sifre: admin123
Ayarlar > Lisans bolumunden lisans aktivasyonu yapin.
Not: Program self-contained Windows paketi olarak yayimlanir. Gerekli calisma dosyalari paketin icindedir.

Gunluk kullanim
Masalar ekranindan ilgili masayi acin.
Sag menuden urunleri secerek masaya ekleyin.
Gerekirse masa notu girin veya urunleri baska masaya tasiyin.
Gonder ile siparisleri mutfak/bar ekranlarina iletin.
Yonetici hesabiyla tahsilat alin.
Gun sonunda Z raporu alarak kasayi kapatin.
X raporu ve Z raporu mantigi
X raporu, son Z raporundan sonra olusan acik kasa donemini gosterir. X raporu almak satislari sifirlamaz.

Z raporu, kasa kapanisi yapar. Z raporu alindiktan sonra yeni kasa donemi baslar ve X raporu yeni doneme gore sifirdan hesaplanir. Acik masalar kapatilmaz, siparisler silinmez.

Bu mantik gece gec kapanan isletmeler icin uygundur. Ornegin kafe gece 02:00'de kapaniyorsa Z raporu o saatte alinabilir; sistem takvim gunune bagli kalmadan kasa donemini takip eder.

Garson telefon girisi
Garsonlar ayni Wi-Fi agina bagli telefonlardan POS bilgisayarinin LAN adresine girerek siparis ekleyebilir. Telefonla girilen siparislerde urunu hangi garsonun girdigi kalem bazinda kayit altina alinir.

Ayarlar ekraninda gorunen adres ornekleri:

http://localhost:5077
http://192.168.x.x:5077
Telefonlarin bu adrese erisebilmesi icin POS bilgisayari ve telefonlar ayni yerel agda olmalidir.

Mutfak ve bar ekranlari
Isletmede kasa, mutfak ve bar icin ayri ekranlar kullanilabilir.

Icecek kategorileri bar ekranina yonlendirilebilir.
Yiyecek ve tatli kategorileri mutfak ekranina yonlendirilebilir.
Satir iptalleri ilgili hazirlama ekranina iptal olarak duser.
Ayarlar ekraninda POS cihazlari ve kategori rotalari tanimlanabilir.
QR menu
QR menu musterinin telefonunda sadece urunleri gosterir. QR menu uzerinden siparis girisi yapilmaz.

Yerel kullanimda QR menu ayni Wi-Fi agindaki cihazlarda calisir. Musterilerin mobil internetten de erismesi istenirse QR menu icin ayrica internette yayinlanan bir alan adi veya hosting yapisi kurulmalidir.

Veri saklama
Kurulu surumde canli veriler yerel SQLite altyapisinda saklanir. Program, isletmenin interneti kesilse bile yerel POS olarak calismaya devam edecek sekilde tasarlanmistir.

Kurulu surum veri klasoru:

C:\ProgramData\BenimYazilim\CafePos
Gelistirme surumunde test verileri proje icindeki data klasorunde tutulur. Bu klasor GitHub'a ve setup paketine dahil edilmez.

Guncelleme ve yayinlama
Yeni Windows paketi olusturmak icin:

.\build-release.ps1 -Version 1.0.4
Paketler Releases klasorune olusur. GitHub Release yayinlarken su dosyalar yuklenmelidir:

BenimYazilimCafePos-win-Setup.exe
BenimYazilimCafePos-1.0.4-full.nupkg
BenimYazilimCafePos-1.0.4-delta.nupkg
RELEASES
releases.win.json
assets.win.json
Velopack kullanan kurulu uygulamalar GitHub Releases uzerinden yeni surumleri alabilecek sekilde hazirlanmistir.

Gelistirme
Projeyi Visual Studio ile calistirmak icin:

CafePos.csproj dosyasini acin.
Calistirma profili olarak CafePos secili olsun.
F5 ile baslatin.
Tarayici otomatik acilmazsa http://localhost:5077 adresini acin.
Terminal ile calistirmak icin:

dotnet run
Teknolojiler
.NET 10
ASP.NET Core Minimal API
SQLite
Vanilla HTML/CSS/JavaScript
Server-Sent Events ile canli guncelleme
Velopack ile Windows setup ve guncelleme paketi
Destek
Destek ve iletisim:

E-posta: destek@benimyazilim.com
Web: BenimYazilim
Instagram: BenimYazilim
Not
Bu proje BenimYazilim tarafindan gelistirilen Restaurant POS uygulamasidir. Kurulum, lisanslama, guncelleme ve musteri uyarlamalari icin BenimYazilim ile iletisime gecilebilir.
