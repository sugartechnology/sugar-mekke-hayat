# Hayat Mekke · Villa Sunumu

Hayat Mekke projesinin villa mobilya paketleri için sunum sitesi: paket karşılaştırması, kat planları, oda renderları, 360° panoramalar ve tam ekran sunum modu.

## Klasör yapısı

```
index.html                 Sitenin kendisi (tek sayfa)
data/
  data.js                  Sitenin okuduğu veri (config + media)
  config.json              Paketler, kat tutarları (USD), oranlar, KDV, villa adedi, kur
  media.json               Görsellerin listesi: villa, kat, oda, paket, dosya yolu
assets/
  villa-a/renders/         Oda renderları
  villa-a/renders/thumbs/  Galeride kullanılan küçük önizlemeler
  villa-*/plans/           Kat planları (yüklendikçe)
  villa-*/panoramas/       360° panoramalar (yüklendikçe)
src/
  claude-artifact.html     Claude'da yayınlanan sürümün kaynağı (yönetim paneli dahil)
```

## Yerelde açmak

`index.html` dosyasına çift tıklamak yeterli. 360° görüntüleyici internetten three.js yüklediği için bağlantı gerekir.

## GitHub Pages ile yayınlamak

1. Repo ayarlarında **Settings → Pages → Branch: `main` / root** seçin.
2. Birkaç dakika içinde site `https://<kullanıcı>.github.io/<repo>/` adresinde açılır.

> Fiyatlar ve renderlar müşteriye özel bilgi. Repoyu **private** tutmanız önerilir. GitHub Pages'te private repo yayını ücretli planlarda vardır.

## Veriyi güncellemek

- **Rakamlar:** `data/config.json` içinde her paketin `values` alanı villa başına `[Zemin kat, 1. kat, Çatı katı, Ev tamamlayıcı ürünler]` tutarlarını (USD) tutar. `rates` alanı navlun, montaj ve sigorta oranlarını tutar.
- **Görseller:** Dosyayı `assets/` altına koyup `data/media.json` dosyasına bir kayıt ekleyin. `kind` alanı `render`, `plan` ya da `pano` olabilir.
- **WebP:** Site görselleri `.webp` olarak yükler (renderlar en fazla 3840 px, önizlemeler 900 px). Orijinal JPG/PNG dosyaları aynı klasörde durur ve `media.json` içindeki `original` alanında yazılıdır.
- Her iki dosyayı değiştirdikten sonra `data/data.js` dosyasını da güncelleyin. Site bu dosyayı okur.

Yönetim paneli (yükleme, oda işaretleme, Google Sheets'ten çekme) yalnızca Claude'daki sürümde çalışır. Bu klasör o sürümün bir anlık dışa aktarımıdır.

## Paket adları

Paketler fiyat sırasına göre Silver'dan başlayarak adlandırılır ve firma adıyla birlikte gösterilir (ör. "Silver · Bellona"). Kaynak Google Sheets bağlantısı bu klasöre dahil edilmedi.

## Sunum ve PDF

Üst menüdeki **Sunum** düğmesi iki biçim sunar: ekranda ilerleyen **interaktif sunum** ve **PDF**. PDF A4 yatay hazırlanır; her sayfada Emlak Konut ve RapidRender logoları, villa tiplerinin kat planları, paket maliyetleri ve paket bazlı oda görselleri (ürün fiyatlarıyla) yer alır. Logolar `assets/brand/` altında, yolları `config.json` içindeki `logos` alanında. PDF görselleri okuyabilmek için sitenin bir web adresinden (GitHub Pages ya da yerel sunucu) açılması gerekir; dosyaya çift tıklayarak açıldığında tarayıcı görselleri PDF'e eklemeye izin vermez.
