# META — Güven Etiketleme + Başarısızlık Modları
*Her zaman yükle. Her modül çıktısına uygulanır.*

---

## Güven Etiketi

Her modül çıktısına ekle:

| Etiket | Anlam |
|---|---|
| `[HIGH]` | Açık, doğrulanabilir bilgiye dayalı. Farklı analist aynı sonuca varır. |
| `[MED]` | Çıkarım veya varsayım var. Farklı analist bazı noktalarda farklı sonuca varabilir. |
| `[LOW]` | Büyük ölçüde çıkarımsal. Sonuç değil, başlangıç noktası olarak kullan. |

---

## Sistem Başarısızlık Modları

| ID | Mod | Belirti |
|---|---|---|
| F1 | Input kalitesi düşük | Belirsiz tanımlar yapılandırılmış ama boş çıktı üretir |
| F2 | Kullanıcı zaten sonuca ulaşmış | Onay arıyor, evaluation değil — input yanlı çerçevelenmiş |
| F3 | Regime coverage imkânsız | Varlık çok yeni, 3 rejim verisi yok |
| F4 | Tamamlamadan aşırı güven | Tüm modüller dolduruldu ≠ sistem çalışıyor |
| F5 | Formal grammar discretion'ı maskeler | "EMA50>EMA200" mekanik görünür ama bağlam yoruma açık kalabilir |

---

## Final Çıktı Şablonu

```
FINAL CLASSIFICATION : [sınıf — bkz. M6]
KEY RISKS            : [1] [2] [3]
DIFFICULTY           : Low / Medium / High
CONFIDENCE           : [HIGH/MED/LOW]
TRADER WARNING       : [M0 profiline göre spesifik uyarı]
BASELINE COMPARISON  : [Evet / Belirsiz / Hayır + tek cümle sebep]
NEXT STEPS           : [1] [2] [3]
```

---

## Referans

Bu modülü üreten zincir: Panel 1 Uzman 2 (automation bias) + Panel 1 Uzman 5 (güven etiketleme) + Panel 2 Uzman A (döngüsel bağımsızlık) → v3.0'da eklendi, tüm versiyonlarda korundu.
