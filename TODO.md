# TODO

Son güncelleme: 17 Kasım 2026. Önemli tarihler: GSC Phase 1 teslimi 22 Kasım 23:59 UTC, İstanbul buluşması Aralık, ilk pilot fırsatı Ağustos 2027 hasadı. Ayrıntılı plan: [ROADMAP.md](ROADMAP.md).

## Bu hafta: GSC teslimi

- [x] GSC teklifi hazırlandı, yeni adla güncellendi; rakip/benzer firmalar slaytı eklendi (21 slayt)
- [ ] GSC takım adını ve özetini formda "Gleanly" yap; takım görselini yenisiyle değiştir (`docs/gsc/gleanly_team_1024x576.png`)
- [ ] Teklifi PDF olarak dışa aktar (10 MB altı), 5. sayfadaki rakip slaytının taşmadığını kontrol et, forma yükle
- [ ] 2 dakikayı geçmeyen proje tanıtım videosunu çek, YouTube'a "liste dışı" yükle, bağlantıyı forma yapıştır
- [ ] Formdaki üç beyan kutusunu işaretle (belge yüklendikten sonra) ve gönder
- [ ] LinkedIn gönderisindeki görselleri yenileriyle değiştir (`docs/linkedin/`)
- [ ] GitHub "About" bölümündeki web sitesi alanı `https://blosny.github.io/gleanly/` olsun

## Marka (Gapçuk AI → Gleanly)

- [x] Arayüz, kod, README, simülasyon ve kaynakça yeni adla; yeni logo ve favicon
- [x] Depo adı `gleanly`, Pages adresi `blosny.github.io/gleanly` (eski adres kapandı)
- [x] Site açık (kırık beyaz) temaya geçti: koyu orman yeşili `#14532D`, açık yeşil `#84CC16`, zemin `#F7F5EF`. Simülasyon sayfası koyu sahne olarak kaldı
- [ ] TÜRKPATENT ve WIPO marka araması ("Glean" adlı büyük bir yazılım firması var, benzerlik riski)
- [ ] gleanly.ai / .io / .co alan adlarını ve sosyal medya hesaplarını ayır (.com alınmış)
- [ ] Vercel yedek adresi ve eski belgeler (PDR, Creathon decki) yeni adla güncellenecek ya da kaldırılacak
- [ ] Video anlatısını en sonda güncelle: ilk pilot fındık zürufu, amaç toplanabilecek tüm biyokütle atıkları ve biyoyakıt hammaddeleri

## Hesaplar (yüksek öncelik)

- [ ] Yakıt tasarrufunu OSRM mesafeleriyle doğru hesapla (yöntem: yakıt tasarrufu hesabı belgesi)
- [ ] `compareOrders()` ve "plansız / optimize / fark" kartı
- [ ] Mesafe için OSRM `table` servisi, 9 duraktan fazlası için 2-opt
- [ ] Yakıt tüketimi ve dizel CO2 faktörü için kaynak bul; 0,36 L/km varsayımını parametreye taşı
- [ ] Taşıma emisyonunu net etki hesabından düş
- [ ] Santralde fosil yakıt ikamesini hesapla (kaynaklı faktörlerle), ayrı satır olarak göster
- [ ] Hesap fonksiyonları için birim testler

## Ürün

- [ ] Dil modeli destekli çiftçi asistanı: serbest metinden konum, çuval ve yol durumunu çıkar
- [ ] Alıcı kaydı (ad, konum, fiyat, azami nem, kabul ettiği atık, saatler)
- [ ] İsteğe göre fabrikaya yönlendirme: operatör yükün gideceği alıcıyı seçebilsin; sistem fiyat, mesafe ve nem şartına göre varsayılan öneri versin
- [ ] Tonaj tahmini: köy bildirimleri ve hava verisinden önümüzdeki iki hafta için beklenen ton ve nem
- [ ] Hasat doğrulaması: WhatsApp'ta tek soruluk "Patoz bitti mi?"
- [ ] Atık türüne göre ayarlar (nem sınırı, çuval ağırlığı, alıcı); ikinci bir atık türü örneği
- [ ] Kantar fişi ve fiyat bilgisinin çiftçiye WhatsApp'tan gitmesi
- [ ] Gerçek WhatsApp Business API entegrasyonu
- [ ] Arka uç ve veritabanı (bildirimler sayfa yenilenince kaybolmasın)
- [ ] Kullanıcı rolleri: operatör, çiftçi, alıcı
- [ ] Kendi OSRM sunucusu
- [ ] İngilizce arayüzü tamamla
- [ ] Külleme risk skorunu saha verisiyle kalibre et ya da yayımlanmış bir modele bağla

## Saha ve doğrulama

- [ ] En az 15 çiftçi görüşmesi (form hazırla; görüşmeleri kayda al, izin al)
- [ ] Ziraat odasıyla görüşme: rolü ne olabilir?
- [ ] Nakliyeci ve kamyon sahibiyle fiyat konuşması
- [ ] Alıcıdan kurumsal yazılı teyit ve ödeme vadesi
- [ ] Biyolink, Ersis ve benzeri firmalara zürüf alımı için kısa e-posta
- [ ] Zürüf miktarı için üçüncü bir kaynak
- [ ] Trichoderma ile zürufta kompost süresi için pilot deneyi planı

## Hukuki ve şirket

- [ ] Tarımsal atık toplama ve taşıma için izin gerekip gerekmediğini il müdürlüğüne sor
- [ ] KDV ve çiftçi muaflığı konusunda muhasebeci görüşü
- [ ] KVKK aydınlatma metni ve açık rıza akışı
- [ ] Ekip rolleri ve pay konuşması
- [ ] Şirketleşme kararı için eşikler belirlendi mi? (bkz. ROADMAP)

## Tasarım

- [x] Açık tema ve yeni renk paleti (ana site, bilgi merkezi, kaynakça)
- [ ] Biyolink benzeri sade bir tanıtım sayfası: büyük başlık, nasıl çalışır, hizmet kartları, atık türü etiketleri, tek çağrı butonu
- [ ] "Rakamlarla" bölümü yalnızca ölçülmüş pilot sayılarıyla; o zamana kadar "pilot hedefleri" etiketli
- [ ] Uydurma müşteri yorumu koyma; gerçek yorum gelince ekle
- [ ] Operatör paneli ile tanıtım sayfasını ayrı tut
- [ ] Mobil görünümü kontrol et

## Tamamlananlar

- [x] Rakamların kaynak taraması ve `kaynakca.html` (K1-K13)
- [x] "%34 yakıt tasarrufu" ve doğrulanamayan iddiaların kaldırılması
- [x] CO2 hesabının IPCC faktörleriyle yeniden yapılması
- [x] Santral fiyatının yazışmaya göre 2.000 TL/ton + KDV olarak düzeltilmesi
- [x] GitHub Pages ile erişilebilir yayın
- [x] GSC takımı kuruldu ve teklif hazırlandı
- [x] Yeniden adlandırma, yeni logo, açık tema, güncel ekran görüntüleri
