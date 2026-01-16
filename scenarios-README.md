# SEO Senaryoları - PageSpeed Test Dosyaları

Bu klasör, PageSpeed Insights ve Lighthouse ile test edilebilecek SEO senaryolarını içerir. Her senaryo için **kötü (bad)** ve **iyi (good)** olmak üzere iki versiyon bulunmaktadır.

## 📁 Dosya Yapısı

```
scenarios/
├── index.html              # Ana sayfa (tüm senaryolar)
├── scenario-1-bad.html     # Meta etiketler - KÖTÜ
├── scenario-1-good.html    # Meta etiketler - İYİ
├── scenario-2-bad.html     # Görsel optimizasyonu - KÖTÜ
├── scenario-2-good.html    # Görsel optimizasyonu - İYİ
├── scenario-3-bad.html     # İçerik & erişilebilirlik - KÖTÜ
├── scenario-3-good.html    # İçerik & erişilebilirlik - İYİ
├── scenario-4-bad.html     # Core Web Vitals - KÖTÜ
├── scenario-4-good.html    # Core Web Vitals - İYİ
└── README.md               # Bu dosya
```

## 🎯 Senaryolar

### Senaryo 1: Meta Etiketler & Semantic HTML
| Kötü (Bad) | İyi (Good) |
|------------|------------|
| ❌ Lang attribute eksik | ✅ Proper lang="tr" |
| ❌ Viewport meta yok | ✅ Responsive viewport |
| ❌ Birden fazla H1 | ✅ Tek H1, proper hierarchy |
| ❌ Keyword stuffing | ✅ Natural content |
| ❌ Hidden text (spam) | ✅ Structured Data (JSON-LD) |
| ❌ Render-blocking JS | ✅ Deferred scripts |

### Senaryo 2: Görsel Optimizasyonu
| Kötü (Bad) | İyi (Good) |
|------------|------------|
| ❌ Büyük PNG (~8MB) | ✅ WebP format (~100KB) |
| ❌ Width/height tanımsız | ✅ Explicit dimensions |
| ❌ Lazy loading yok | ✅ Native lazy loading |
| ❌ Alt text eksik | ✅ Descriptive alt text |
| ❌ Eager load all | ✅ Picture element + fallback |

### Senaryo 3: İçerik & Erişilebilirlik
| Kötü (Bad) | İyi (Good) |
|------------|------------|
| ❌ Thin content | ✅ Zengin, değerli içerik |
| ❌ "Click here" linkleri | ✅ Descriptive link text |
| ❌ Form labels eksik | ✅ Accessible forms (ARIA) |
| ❌ JavaScript navigation | ✅ Crawlable links |
| ❌ No breadcrumbs | ✅ Breadcrumb + Schema.org |

### Senaryo 4: Core Web Vitals (LCP, CLS, INP)
| Kötü (Bad) | İyi (Good) |
|------------|------------|
| ❌ LCP: Büyük hero, no preload | ✅ LCP: Preloaded WebP |
| ❌ CLS: Boyutsuz görseller | ✅ CLS: Aspect-ratio containers |
| ❌ CLS: Geç yüklenen içerik | ✅ CLS: Reserved space for ads |
| ❌ INP: Ağır event handlers | ✅ INP: Lightweight + delegation |
| ❌ Blocking head scripts | ✅ Deferred + async scripts |

## 🧪 Nasıl Test Edilir?

### Yerel Test (Live Server ile)
1. VS Code'da Live Server eklentisini kurun
2. `scenarios/index.html` dosyasını açın
3. Sağ tık > "Open with Live Server"
4. Tarayıcıda açılan URL'yi PageSpeed'e yapıştırın

### GitHub Pages ile Test
1. Projeyi GitHub'a push edin
2. Settings > Pages > Deploy from branch (main)
3. URL: `https://[username].github.io/seo_practice/scenarios/`
4. Bu URL'yi PageSpeed Insights'a girin

### PageSpeed Insights
1. https://pagespeed.web.dev/ adresine gidin
2. URL'yi yapıştırın (örn: `https://ysfdursun.github.io/seo_practice/scenarios/scenario-1-bad.html`)
3. "Analyze" butonuna tıklayın
4. Bad ve Good versiyonlarını karşılaştırın!

## 📊 Beklenen Sonuçlar

| Senaryo | Bad Score | Good Score | Ana Fark |
|---------|-----------|------------|----------|
| 1 - Meta/HTML | ~50-60 | ~90-100 | SEO metrikleri |
| 2 - Görseller | ~20-40 | ~85-95 | Performans (LCP) |
| 3 - İçerik | ~60-70 | ~95-100 | Accessibility |
| 4 - CWV | ~30-50 | ~90-100 | Core Web Vitals |

## 🔧 Önemli Notlar

1. **Görsel Dosyaları**: `seo_banner.png` (~8MB) ve `SEO-BANNER.webp` (~100KB) ana klasörde bulunmalıdır. Bad versiyonlar PNG, Good versiyonlar WebP kullanır.

2. **PageSpeed Gereksinimleri**: Gerçek skorlar almak için sayfaların internette erişilebilir olması gerekir (localhost test edilemez, yalnızca Lighthouse CLI ile).

3. **Lighthouse CLI ile Yerel Test**:
   ```bash
   npx lighthouse http://localhost:5500/scenarios/scenario-1-bad.html --view
   ```

4. **Simülasyon Notu**: Bad versiyonlardaki JavaScript kasıtlı olarak ağır işlemler yapar. Bu, INP metriklerini olumsuz etkilemek için tasarlanmıştır.

## 📚 Kaynaklar

- [PageSpeed Insights](https://pagespeed.web.dev/)
- [Web Vitals](https://web.dev/vitals/)
- [Lighthouse](https://developer.chrome.com/docs/lighthouse/)
- [Schema.org](https://schema.org/)
