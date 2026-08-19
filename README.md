<div align="center">

<img src="https://nycr0x.github.io/Haxora/site/Haxora_Icon.png" width="128" alt="Haxora" />

# Haxora

**HaxBall için yeni nesil masaüstü istemcisi**

[![Sürüm](https://img.shields.io/github/v/release/nycr0x/Haxora?label=s%C3%BCr%C3%BCm&color=4f8fbd)](https://github.com/nycr0x/Haxora/releases/latest)
[![İndirme](https://img.shields.io/github/downloads/nycr0x/Haxora/total?label=indirme&color=4f8fbd)](https://github.com/nycr0x/Haxora/releases)
[![Platform](https://img.shields.io/badge/platform-Windows%20x64-4f8fbd)](https://github.com/nycr0x/Haxora/releases/latest)

[**İnternet sitesi**](https://nycr0x.github.io/Haxora/) · [**İndir**](https://github.com/nycr0x/Haxora/releases/latest) · [**Sorun bildir**](https://github.com/nycr0x/Haxora/issues)

</div>

---

Haxora, HaxBall'ı tarayıcı sekmesi yerine kendi penceresinde çalıştıran bir masaüstü istemcisidir. Kurulum gerektirmez: tek bir `.exe` indirip çalıştırırsın.

Tarayıcıda elde edemediğin şeyleri veriyor — çünkü tarayıcı bir web sayfasına o yetkileri vermiyor. Kare hızı freni gerçekten kaldırılabiliyor, arka plana düşen sekmenin zamanlayıcıları kısılmıyor, oyun süreci öncelik alıyor. Üstüne arkadaş listesi, özel mesajlaşma, yerel susturma ve antrenman modu gibi istemci tarafı özellikler geliyor.

> [!NOTE]
> Haxora **bağımsız ve resmi olmayan** bir projedir. HaxBall'ın kendisiyle, geliştiricisiyle veya markasıyla hiçbir bağı yoktur. Oyun sunucuları ve oyun kuralları HaxBall'a aittir; Haxora yalnızca oyuna bağlanan bir istemcidir.

## Ne yapıyor

**Oyun deneyimi**
- Kare hızı modu seçimi: ekran hızına kilitli (en akıcı) ya da sınırsız
- Donanım hızlandırma açıp kapatılabiliyor — bazı makinelerde işlemciyle çizmek daha akıcı
- Arka plana düşünce oyun yavaşlamıyor; Chromium'un zamanlayıcı kısıtlamaları kapalı
- Oyun süreci işletim sisteminden yüksek öncelik alıyor, ping sıçramaları azalıyor

**Sosyal**
- Haxora hesabı, arkadaş listesi ve özel mesajlaşma
- Oda geçmişi ve favori odalar
- Oda istatistikleri

**Sohbet ve moderasyon**
- Yerel susturma: rahatsız eden oyuncuyu yalnızca kendi ekranında susturursun. Odaların çoğu sohbeti bir bot üzerinden duyuru olarak yeniden yayımlıyor; Haxora o satırları da yakalıyor, adın önünde emoji, rozet ya da ülke etiketi olması fark etmiyor
- Özel mesajlar ayrı bir pencerede toplanıyor

**Kişiselleştirme**
- Tema ve vurgu rengi
- Avatar tepkileri: bir tuşa emoji atarsın, basılı tuttukça avatarın o olur
- Top görünümü, saha efektleri, gol efektleri
- Tuş atamaları

**Diğer**
- Antrenman modu
- Maç kaydı ve tekrar izleme
- Korumalı odalar için doğrulama akışı uygulamanın içinde

## İndirme ve kurulum

1. [**Son sürümü indir**](https://github.com/nycr0x/Haxora/releases/latest) — `Haxora.exe`
2. Çalıştır. Kurulum yok, yönetici yetkisi istemez.

### Windows uyarı verirse

İlk çalıştırmada Windows **"Windows bilgisayarınızı korudu"** uyarısı gösterebilir. Sebebi Haxora'nın kötü amaçlı olması değil, `.exe`'nin ücretli bir kod imzalama sertifikasıyla imzalanmamış olması — Windows tanımadığı yayıncıları böyle karşılıyor.

Devam etmek için: **Ek bilgi** → **Yine de çalıştır**.

Güvenmek zorunda kalmamak için her sürümün SHA256 özetini sürüm notlarına yazıyoruz. İndirdiğin dosyayı PowerShell'de doğrulayabilirsin:

```powershell
Get-FileHash Haxora.exe -Algorithm SHA256
```

Çıkan değer [sürüm notlarındaki](https://github.com/nycr0x/Haxora/releases/latest) değerle aynı olmalı. Tutmuyorsa dosyayı çalıştırma.

### Gereksinimler

- Windows 10 veya 11, 64 bit
- Yaklaşık 250 MB disk alanı
- İnternet bağlantısı

## Güvenlik

Bir masaüstü uygulamasını tersine mühendislikten tamamen korumak mümkün değil; kod sonuçta senin makinende çalışıyor. Yine de dağıtılan kopyanın bütünlüğü için şunlar yapıldı:

- **İstemci kaynakları arşivin içinde.** Kurulumun yanında açılıp okunabilecek düz metin bir klasör yok.
- **Değiştirilmiş kopya açılmıyor.** Arşivin özeti çalıştırılabilir dosyanın içine gömülü; içeriği değiştirilip yeniden paketlenen bir kopya başlamadan kapanıyor.
- **Uzaktan hata ayıklama kapalı.** `--remote-debugging-port` gibi anahtarlarla açılan bir kopya çalışmıyor; `--inspect` ve `NODE_OPTIONS` devre dışı.
- **Yerel sunucu kilitli.** Haxora içeride yerel bir sunucu çalıştırıyor. Her açılışta üretilen bir anahtarla korunuyor, yani makinendeki başka bir program ya da tarayıcı sekmesi ona erişemiyor.
- **Sohbet içeriği ekrana metin olarak basılıyor**, HTML olarak değil. Oda ve oyuncu adları ağdan geliyor; bu sayede ad alanına kod yazarak bir şey çalıştırmak mümkün değil.

Bir güvenlik açığı bulursan lütfen [issue aç](https://github.com/nycr0x/Haxora/issues).

## Sık sorulanlar

**Hesabım banlanır mı?**
Haxora oyunun kurallarını değiştirmiyor, hile içermiyor ve sunucuya normal bir istemci gibi bağlanıyor. Yine de resmi bir istemci değil; kullanım kararı sana ait.

**Verilerim nerede duruyor?**
Ayarların ve oda geçmişin kendi bilgisayarında. Hesap açtıysan arkadaş listesi ve mesajlar Haxora'nın sunucusunda tutuluyor.

**Mac veya Linux sürümü var mı?**
Şu an yalnızca Windows x64.

**Güncellemeler nasıl geliyor?**
Haxora açılışta buradaki son sürüme bakıyor ve yenisi varsa oda listesinde bir şerit gösteriyor. İndirme kararı sende.

**Neden dosya boyutu bu kadar büyük?**
Uygulama kendi tarayıcı motorunu (Chromium) taşıyor. Kare hızı frenini kaldırmak ve zamanlayıcı kısıtlamalarını kapatmak ancak böyle mümkün.

## Teşekkür

Haxora'nın oyun katmanı [wxyz-abcd/node-haxball](https://github.com/wxyz-abcd/node-haxball) üzerine kuruludur (MIT). O kütüphane olmasa bu proje olmazdı.

## Lisans

MIT

---

<div align="center">
<sub>Haxora bağımsız bir projedir ve HaxBall ile resmi bir bağı yoktur.</sub>
</div>
