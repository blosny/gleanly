<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="brand/gleanly-logo-dark.png">
    <img src="brand/gleanly-logo.png" alt="Gleanly: Circular Resource Intelligence" width="420">
  </picture>
</p>

<p align="center">
  <img alt="Climathon 2026" src="https://img.shields.io/badge/Climathon%202026-Siemens%20%C2%B7%20YGA%20%C2%B7%20UP%20School-0F2E24">
  <img alt="İlk pilot" src="https://img.shields.io/badge/%C4%B0lk%20pilot-Ordu%20%2F%20%C3%9Cnye-167A45">
  <a href="https://blosny.github.io/gleanly/"><img alt="Demo" src="https://img.shields.io/badge/Demo-GitHub%20Pages-1E9E5A"></a>
</p>

**Gleanly** (eski adı Gapçuk AI), tarlada ve bahçede kalan tarımsal biyokütleyi (meyve ve sebze artıkları, hasat ve budama artığı) yakılan bir atıktan temiz enerjiye ve komposta dönüştürmeyi hedefleyen döngüsel bir kaynak lojistiği platformu. Amaç, toplanabilecek tüm bu atıkları aynı sistemle köyden alıcıya taşımak; bildirim, rota, nem ve alıcı eşleştirmesi atık türünden bağımsız bir yapıya taşınacak.

**İlk pilot** Ordu / Ünye'de **fındık zürufu** (yöresel adıyla gapçuk) ile planlanıyor. Bu sayfadaki sayılar, uygulama ve hesaplar şu an yalnızca fındık zürufu için hazırlandı; diğer atık türleri pilot sonrasında eklenecek. **Siemens, YGA ve UP School Climathon 2026** programında geliştirildi.

**Stack:** HTML · CSS · Vanilla JavaScript · Leaflet · OpenStreetMap · OSRM · Open-Meteo · React 18 · GitHub Pages

**Canlı demo:** [blosny.github.io/gleanly](https://blosny.github.io/gleanly/) · **Simülasyon:** [Döngüyü başlat](https://blosny.github.io/gleanly/simulasyon.html)

---

## Modüller

| Modül | Ne yapar | Durum |
|---|---|---|
| GleanlyRoute | Çiftçi bildirimlerinden durak sırası ve gerçek yol rotası çıkarır | Çalışıyor |
| GleanlyBot | WhatsApp üzerinden bildirim alır, hava durumuna göre yanıt verir | Kural tabanlı |
| GleanlyBio | Külleme riskini hesaplar, atığı santrale ya da komposta yönlendirir | Çalışıyor |
| Döngü simülasyonu | Atığın harmandan santrale ve toprağa dönüşünü canlandırır | Çalışıyor |

## Problem (ilk pilot: fındık zürufu)

Aşağıdaki veriler yalnızca ilk pilot olan fındık zürufu içindir. Aynı toplama ve yönlendirme sorununun meyve, sebze ve diğer tarımsal atıklarda da olduğu, pilot sonrasında saha görüşmeleriyle doğrulanacak.

- Patoz çoğu zaman tek şeritli köy yollarında yapılır; çıkan zürufun düzenli bir toplama mekanizması yoktur.
- Çiftçi yolu açmak için atığı ya **yakar** ya da bahçeye **çiğ serer**. Zürufun C/N oranı yüksektir (yaklaşık 33:1) ve literatürde doğrudan tarlaya uygulanması uygun bulunmaz [K3]. Açıkta yakma ise CH₄ ve N₂O açığa çıkarır [K5].
- Yılda yaklaşık 200 bin ile 500 bin ton züruf açığa çıktığı bildirilmektedir; iki kaynak arasında fark vardır [K2, K3].
- Bölgedeki biyokütle enerji santrali zürufu satın alıyor, ancak satın alma sorumlusuna göre ürün sonbahara geç geldiği ve bölge yağışlı olduğu için istenen tonajı alamıyor [K13]. Eksik olan, küçük üreticiyle alıcıyı buluşturacak lojistik.

## GleanlyRoute: Rota Motoru

- Her bildirim haritada numaralı bir durak olur. Sıralama en yakın komşu yöntemiyle yapılır ve **yolu kapalı** köyler öne alınır (`optimizeStopSequence`).
- Rota kuş uçuşu değil, **OSRM** `route/v1/driving` ile gerçek köy yolu geometrisi üzerinden çizilir.
- OSRM yanıt vermezse sıralı noktalarla yedek bir rota çizilir.

## GleanlyBot: Çiftçi Asistanı

- Çiftçi uygulama indirmeden konumunu, çuval sayısını ve yol durumunu tek mesajla bildirir.
- Yanıt, **Open-Meteo**'dan gelen anlık sıcaklık ve nem verisine göre değişir: nem yüksekse atığı örtme ve yakmama uyarısı, yol kapalıysa öncelikli toplama bilgisi.
- Şu an yanıtlar kural tabanlı; bir dil modeline taşınması yol haritasında.

## GleanlyBio: Erken Uyarı ve Kompost

- Sıcaklık ve nemden külleme (*Erysiphe corylacearum*) için sezgisel bir risk skoru hesaplanır (`calculateMildewRisk`). Eşikler yayımlanmış bir modele dayanmaz ve saha verisiyle kalibre edilmemiştir.
- Nem sınırının altındaki atık **biyokütle santraline**, üstündeki atık **Trichoderma** ile kompostlama hattına gider.
- Araç köye bir önceki partinin kompostunu götürür, dönüşte gapçuk yükler: boş dönüş olmaz.

## Döngü Simülasyonu

- [`src/simulasyon.html`](src/simulasyon.html): harman ve patoz, dağ lojistiği, enerji santrali ve biyo-kompost aşamalarını anlatan interaktif simülasyon.
- React 18 ve lucide-react ile tek dosya; build adımı yok. Değerler tek bir köy rotası için örnektir.

## İş Modeli

- Gelir, toplanan biyokütlenin santrale satışından gelir. Pilot bölgeye en yakın alıcı Samsun Çarşamba'daki biyokütle enerji santralidir (27 MWe) [K4].
- Santralin satın alma sorumlusuyla yapılan e-posta yazışmasına göre (22 Ekim 2026) zürufun alım fiyatı Ordu–Giresun bölgesi için **2.000 TL/ton + KDV**, azami nem **%35**'tir. Alım santralin kendi kantarında yapılır, nakliyeyi tedarikçi üstlenir ve alım miktarı sınırsızdır [K13]. Yazışma kurumsal bir şartname değildir; kurumsal yazılı teyit alınacaktır. Gelir hesapları KDV hariç tutarla yapılır.
- Çiftçiye ücretsiz kompost geri döner. Birim ekonomi varsayımlara dayanır ve saha pilotunda gerçek maliyetlerle doğrulanacak.

## Etki Hesabı

Açıkta yakmanın önlenen emisyonu IPCC 2006 faktörleriyle hesaplanır: 0,80 × (2,7 g CH₄/kg × 28 + 0,07 g N₂O/kg × 265) ≈ **0,075 t CO₂e / ton atık** [K5, K6]. Biyokütle yanmasından çıkan CO₂ sayılmaz ve nem düzeltmesi yapılmaz; bu yüzden değer bir üst sınırdır. Santralde fosil yakıt ikamesi hesaba katılmamıştır.

Uygulamadaki tüm sayıların dayanağı ve doğrulama durumu [Kaynakça ve Doğrulama](https://blosny.github.io/gleanly/kaynakca.html) sayfasındadır.

## Yol Haritası

- Bot yanıtlarını bir dil modeline taşımak, WhatsApp Business API ile gerçek mesajlaşma
- Ünye'de üreticiler, ziraat odası ve santralle saha görüşmeleri
- Rota tasarrufunu saha verisiyle ölçmek
- Sistemi fındık dışındaki meyve, sebze ve diğer tarımsal atıklara uyarlamak (atık türüne göre nem sınırı, çuval ağırlığı ve alıcı ayarları)

## Yerel Çalıştırma

```bash
git clone https://github.com/blosny/gleanly.git
cd gleanly
python -m http.server 3000 --directory src
```

Ana platform `http://localhost:3000`, simülasyon `http://localhost:3000/simulasyon.html` adresinde açılır.

## Kaynaklar

Her kaynağın hangi rakamı desteklediği [Kaynakça ve Doğrulama](src/kaynakca.html) sayfasında verilmiştir.

- **K1** Demirel, B., Gürdil, G. A. K. (2018). Fındık zurufu atığından yakıt briketi elde edilmesi ve brikete ait bazı özelliklerin belirlenmesi. *Anadolu Tarım Bilimleri Dergisi*, 33. [doi:10.7161/omuanajas.302527](https://doi.org/10.7161/omuanajas.302527)
- **K2** Gürdil, G. A. K., Demirel, B. (2020). Effect of moisture content, particle size and pressure on some briquetting properties of hazelnut residues. *Anadolu Tarım Bilimleri Dergisi*, 35. [doi:10.7161/omuanajas.736851](https://doi.org/10.7161/omuanajas.736851)
- **K3** Aygün, S., Bender Özenç, D. (2023). Fındık Atığı Ürünlerinin Buğday Yetiştiriciliğinde Değerlendirilmesi. *Akademik Ziraat Dergisi*, 12 (Özel Sayı), 213–226. [doi:10.29278/azd.1362301](https://doi.org/10.29278/azd.1362301)
- **K4** Electricity Turkey (2019). [Siemens steam turbines in Samsun Biomass Power Plant](https://www.electricityturkey.com/haber/samsun-carsamba-biyokutle-enerji-santralinde-siemens-buhar-turbinleri-kullanilecek-turkiyenin-en-buyuk-ikinci-biyokutle-santralnin-preferi-siemens-oldu-21473)
- **K5** IPCC (2006). *2006 IPCC Guidelines for National Greenhouse Gas Inventories*, Vol. 4, Ch. 2, Tablo 2.5 ve 2.6. [ipcc-nggip.iges.or.jp](https://www.ipcc-nggip.iges.or.jp/public/2006gl/vol4.html)
- **K6** Myhre, G. vd. (2013). Anthropogenic and Natural Radiative Forcing. *IPCC AR5, WG I*, Bölüm 8, Tablo 8.7. [ipcc.ch](https://www.ipcc.ch/report/ar5/wg1/)
- **K7** Sezer, A. vd. (2019). Erysiphe corylacearum'un neden olduğu külleme hastalığına karşı Giresun ili fındık üretim alanlarında kimyasal mücadele olanaklarının belirlenmesi. *Akademik Ziraat Dergisi*, 8 (Özel Sayı), 71–78. [doi:10.29278/azd.656526](https://doi.org/10.29278/azd.656526)
- **K8** Sezer, A., Şahin, S. (2022). Fındıkta Külleme Hastalığının Uzun Süreli Depolamada Bazı İç Bozuklukları ve Kalite Parametrelerine Etkisi. *Ordu Üniversitesi Bilim ve Teknoloji Dergisi*, 12 (2), 179–188. [dergipark](https://dergipark.org.tr/en/pub/ordubtd/article/1207968)
- **K9** Organo, N. D. vd. (2022). Assessing the potential of a Trichoderma-based compost activator to hasten the decomposition of incorporated rice straw. *Scientific Reports*. [doi:10.1038/s41598-021-03828-1](https://doi.org/10.1038/s41598-021-03828-1)
- **K10** Komolafe, A. F. vd. (2020). Maturity indices of composting plant materials with Trichoderma asperellum as activator. *Agricultura Tropica et Subtropica*, 53 (1), 19–27. [doi:10.2478/ats-2020-0003](https://doi.org/10.2478/ats-2020-0003)
- **K11** T.C. 2872 sayılı Çevre Kanunu, madde 8. [mevzuat.gov.tr](https://www.mevzuat.gov.tr/mevzuat?MevzuatNo=2872&MevzuatTur=1&MevzuatTertip=5)
- **K12** Servisler: [OpenStreetMap](https://www.openstreetmap.org/copyright) · [OSRM](https://project-osrm.org/) · [Open-Meteo](https://open-meteo.com/)
- **K13** Çarşamba biyokütle santralinin satın alma sorumlusu ile e-posta yazışması, 22 Ekim 2026 (fındık zürufu tedarik bilgisi). Kamuya açık değildir.
