# Atlas

Premiere Pro için harita animasyonu paneli. Türkçe bir cümle yazarsın, Atlas haritayı kurar: füze ve uçak rotaları,
boyanan ülkeler ve iller, deprem, menzil halkası, cephe hattı, istatistik kartları. Sonra render edip sekansına koyar.
Bu depoda kaynak kod yok, yalnız kurulum paketleri var.

## İndir

**[Atlas_1.34.0.dmg](https://github.com/menestopal/Atlas-releases/releases/download/v1.34.0/Atlas_1.34.0.dmg)** (sürüm 1.34.0)

Önceki sürümler: [Sürümler](https://github.com/menestopal/Atlas-releases/releases). Sürüm sayfasında yalnız `.dmg` dosyasını indir.
"Source code" arşivlerini GitHub kendiliğinden ekler, kurulum için gerekmez.

Gereksinimler: Mac (Apple Silicon ya da Intel), Premiere Pro 2022 ve üstü (Premiere Pro 2026'da denendi), internet bağlantısı
(harita ve yer arama için). Windows desteklenmez. Claude Desktop isteğe bağlı.

## Kurulum

### 1. Diski aç

İndirdiğin `Atlas_1.34.0.dmg` dosyasını çift tıkla. Finder'da **Atlas 1.34.0** adlı bir disk açılır:

| | |
|---|---|
| `Atlas-Kur.command` | Kurulum. Bunu çalıştıracaksın. |
| `Claude-Bagla.command` | Claude Desktop bağlantısını sonradan kurmak ya da yenilemek için (isteğe bağlı). |
| `KURULUM.html` | Kurulum talimatları, bu metin. |
| `Atlas` | Panelin kendisi. Kurulum bunu yerine kopyalar, elle bir şey yapman gerekmez. |

### 2. Kur

`Atlas-Kur.command`'ı çift tıkla. Terminal açılır, ne yaptığını yazar.

macOS ilk seferde "Apple doğrulayamadı" ya da "tanımlanamayan geliştirici" diyerek dosyayı açmayabilir. Bu beklenen bir
durum, çünkü dosya App Store'dan değil doğrudan geliyor. İki yol var:

- Uyarıda **Bitti**'ye bas. **Sistem Ayarları › Gizlilik ve Güvenlik**'i aç. Sayfanın altındaki "Atlas-Kur.command engellendi"
  satırında **Yine de Aç**'a bas, parolanı gir, çıkan pencerede **Aç**'a bas.
- Ya da Terminal'i aç (**Uygulamalar › İzlenceler › Terminal**), `bash ` yaz (sonunda bir boşluk), `Atlas-Kur.command`
  dosyasını Terminal penceresine sürükleyip bırak ve Enter'a bas.

Kurulum şunları yapar, başka hiçbir yere dokunmaz:

```
~/Library/Application Support/Adobe/CEP/extensions/com.atlas.harita/   panel (diskten kopyalanır)
~/Library/Application Support/Atlas/                                    dünya haritası, uydu görüntüsü, önbellek
```

Atlas imzasız bir panel olduğu için kurulum Premiere'de imzasız panellere izin veren ayarı da açar (`PlayerDebugMode`).
Kurulum bitince diski çıkarabilirsin (Finder'da diskin yanındaki ⏏), `.dmg` dosyasını silebilirsin.

### 3. Claude bağlantısı (isteğe bağlı)

Bilgisayarında Claude Desktop varsa kurulum sonunda "Atlas'ı Claude'a da bağlayayım mı?" diye sorar. **E** dersen Claude'a
serbest cümlelerle harita yaptırabilirsin, kendi Claude aboneliğinle. API anahtarı gerekmez.

- Bağlantı Node.js ile çalışır. Bilgisayarında yoksa kurulum izin ister ve yalnız Atlas'ın kullanacağı bir kopyayı indirir
  (resmî nodejs.org paketi, ~50 MB). Yönetici parolası gerekmez, sistemde başka bir şey değişmez.
- Bağladıktan sonra Claude Desktop'ı ⌘Q ile tamamen kapatıp yeniden aç.
- Premiere'de Atlas paneli açıkken Claude'a yaz, örneğin: "Atlas'ta Kıbrıs açığındaki bir gemiden İran'a füze atılan bir
  harita yap". İlk seferde araç izni sorar: **Her zaman izin ver**.
- Şimdi bağlamazsan sonra panelde **ⓘ › Claude Desktop'a bağla** düğmesiyle ya da diskteki `Claude-Bagla.command` ile bağlayabilirsin.

### 4. Premiere'i yeniden başlat

Premiere Pro açıksa tamamen kapatıp aç. Sonra **Pencere (Window) › Uzantılar (Extensions) › Atlas — Harita Animasyonu**.

### 5. İlk harita

Paneldeki komut kutusuna Türkçe yaz, **Oluştur ✦**'e bas (⌘↩). Örnekler:

- İran'dan İsrail'e 8 füze
- Türkiye'yi kırmızıya boya
- Kahramanmaraş'ta 7.7 deprem
- Tahran'dan 500, 1000 ve 2000 km menzil
- İstanbul'dan Londra'ya uçak
- Halfeti'nin bağlı olduğu ili kırmızıya boya

Hazır örnekler için **Galeri** düğmesi (G): kartların üzerine gelince oynarlar, tıklayınca sahne açılır. Beğenmediğin bir
şeyi ⌘Z ile geri alırsın.

**Premiere'e Gönder** haritayı render eder ve aktif sekansa koyar. Dosyalar projenin yanındaki `Atlas Haritalar` klasörüne
yazılır (proje kaydedilmemişse `Filmler/Atlas Haritalar`). Bilgisayarında ffmpeg varsa şeffaf ProRes 4444 `.mov`, yoksa PNG
dizisi gönderilir. ffmpeg için (Homebrew varsa): `brew install ffmpeg`

## Güncelleme

Yeni bir sürüm çıkınca panelin başlığında mavi **Yeni sürüm** rozeti belirir (1.25.6 ve sonrasında); tıklayınca bu indirme
sayfası açılır. Panel hiçbir şey indirmez ya da kurmaz, yalnız haber verir. Yeni sürümün `.dmg` dosyasını indir, aynı adımları izle. `Atlas-Kur.command` eskisinin üzerine kurar; önbellek ve Claude
bağlantısı olduğu gibi kalır. Premiere açıksa kurulumdan sonra yeniden başlat.

## Kaldırma

```bash
rm -rf ~/Library/Application\ Support/Adobe/CEP/extensions/com.atlas.harita
rm -rf ~/Library/Application\ Support/Atlas      # önbellek ve Atlas'a özel Node.js
```

Claude'a bağladıysan: Claude Desktop › Ayarlar › Geliştirici › **Yapılandırmayı düzenle**, açılan dosyada `"atlas"` bölümünü
sil. Render ettiğin videolar proje klasörlerinde kalır.

## Sorun olursa

- **Panel menüde yok:** Premiere'i tamamen kapatıp aç. Kurulum çıktısında "✓ Kurulum tamam" satırı var mı bak; yoksa
  `Atlas-Kur.command`'ı yeniden çalıştır.
- **"Servis yoğun" ya da yer bulunamadı:** yer adları internetten (OpenStreetMap) aranır. Çok art arda komutta servis kısa süre
  yoğun diyebilir, bir dakika bekleyip yeniden dene. Yer adını büyük harfle ve kesme işaretiyle yazmak (Halfeti'yi) en güvenlisi.
- **Claude, Atlas'ı görmüyor:** Atlas paneli Premiere'de açık olmalı. Claude Desktop'ı ⌘Q ile kapatıp aç; panelde **ⓘ**'ye bas,
  oradaki denetim listesinde kırmızı satır var mı bak.

Harita verisi: © OpenStreetMap katkıcıları (OpenFreeMap, Nominatim), Natural Earth, NASA Blue Marble, geoBoundaries.
