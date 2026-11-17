# Yol Haritası

Son güncelleme: 17 Kasım 2026. Bu plan bugünkü bilgiyle yapıldı; saha görüşmeleri geldikçe değişecek. Günlük işler için [TODO.md](TODO.md).

## Hedef

Zürüfün köylerden toplanıp nemine göre santrale ya da komposta yönlendirildiği, ölçülmüş bir pilotu 2027 hasadında yapmak ve sonuca göre sürdürülebilir bir iş modeline karar vermek.

## Aşamalar

| Aşama | Zaman | Amaç | Bitti sayılır |
|---|---|---|---|
| **1. Teslimler** | Kasım 2026 | GSC teklifi ve videosu | Teklif ve video gönderildi |
| **2. Doğrulama** | Aralık 2026 - Ocak 2027 | Gerçek kullanıcıdan ve alıcıdan kanıt | En az 15 çiftçi görüşmesi; ziraat odası ve nakliyeci görüşmesi; alıcıdan kurumsal teyit; ikinci bir alıcıdan cevap |
| **3. Doğru hesap ve yapay zekâ** | Ocak - Nisan 2027 | Rakamların ve botun sağlamlaştırılması | Yakıt/mesafe hesabı OSRM matrisiyle çalışıyor ve testli; dil modeli asistanı çalışıyor; alıcı kaydı ve fabrikaya yönlendirme çalışıyor |
| **4. Altyapı** | Şubat - Mayıs 2027 | Gerçek kullanıma hazırlık | Arka uç, veritabanı, kullanıcı rolleri, WhatsApp Business API, kendi OSRM sunucusu |
| **5. Pilot hazırlığı** | Mayıs - Temmuz 2027 | Bir köy kümesi, bir nakliyeci, bir alıcı | Anlaşmalar yazılı; nem ölçerler alındı; kompost denemesi başladı |
| **6. Pilot** | Ağustos - Ekim 2027 | Hasat sezonunda toplama | Ton, km, nem, yakıt, çiftçi geri bildirimi kayda alındı |
| **7. Karar** | Kasım - Aralık 2027 | Sonuca göre yol | Aşağıdaki eşiklere göre karar verildi |

## Şirketleşme kararı için eşikler

Pilot sonunda şirket kurma, ortaklığa girme ya da yazılıma odaklanma kararı şu ölçülere göre verilir:

- Gerçek maliyetle ton başına marj pozitif mi, ne kadar?
- Alıcı yazılı olarak tekrar alım istiyor mu?
- Çiftçilerin yarıdan fazlası ikinci kez katılmak istiyor mu?
- Ödeme vadesi sermaye ihtiyacını yönetilebilir tutuyor mu?
- Gerekli izinlerin yolu açık mı?

Ayrıntı: `docs/SIRKETLESME.md` (özel belge).

## Genişleme (pilot başarılıysa)

1. İkinci bir atık türü (örneğin zeytin pirinası veya budama artığı) aynı sistemle.
2. İkinci bir bölge.
3. Sanayi alıcıları için izlenebilirlik ve emisyon raporu.

## Riskler

- Alıcı tek; fiyat veya koşul değişirse model sarsılır.
- Hasat dönemi kısa; gecikme tüm sezonu kaçırtır. Pilot hazırlıkları Temmuz'a yetişmeli.
- Çiftçi katılımı ve güven.
- Hukuki izinlerin gecikmesi.
