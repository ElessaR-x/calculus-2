# MEF Calculus-2 Midterm — Konu Bazlı Sınav Analiz Raporu

**Analiz edilen sınavlar:** Fall 22-23, Fall 23-24 (x2), Fall 24-25 (x2), Fall 25-26 (x2), Spring 22-23, Spring 23-24, Spring 24-25 (x2)
**Toplam: 11 midterm sınav**
**Rapor tarihi: 4 Nisan 2026**

---

## 1. KONU FREKANS TABLOSU

| Konu | Sınav Sayısı (11 üzerinden) | Öncelik |
|------|----------------------------|---------|
| Seri Yakınsaklık Testleri | 10/11 | KRİTİK |
| Power Series (Yarıçap & Aralık) | 9/11 | KRİTİK |
| Taylor / Maclaurin Serileri | 9/11 | KRİTİK |
| Konik Kesitler (Ellips/Hiperbol/Parabol) | 8/11 | KRİTİK |
| Polar Koordinatlar (Alan) | 7/11 | ÇOK ÖNEMLİ |
| 3D Vektörler & Düzlem/Doğru | 6/11 | ÇOK ÖNEMLİ |
| Dizilerin Limiti (Sequences) | 5/11 | ÖNEMLİ |
| Çok Değişkenli Fonksiyonlar | 4/11 | ÖNEMLİ |
| Parametrik Eğriler | 3/11 | ORTA |
| Polar Eğri Uzunluğu (Arc Length) | 3/11 | ORTA |

---

## 2. KRİTİK KONU DETAYLARI

---

### A) SERİ YAKINSAKHLIK TESTLERİ
*Her midterm'de 1-4 soru, toplam 15-30 puan*

**Kullanılan testler ve sıklığı:**

| Test | Kaç kez çıktı | Tipik soru |
|------|--------------|------------|
| p-serisi testi | 9 | `Σ 1/n^(5/2)` → p=5/2>1 → yakınsak |
| nth Term Test | 7 | Limit ≠ 0 ise ıraksar |
| Comparison / Limit Comparison | 7 | Büyütme/küçültme ile karşılaştırma |
| Integral Test | 6 | `Σ 1/(n(ln n)³)`, `Σ ln n/n²` |
| Geometric Series | 5 | `Σ (2/3)^n` → r<1 → sum = a/(1-r) |
| Alternating Series (Leibniz) | 5 | Endpoint kontrolünde çıkıyor |
| Ratio Test | 4 | Power series içinde |
| Absolute Convergence | 3 | `|sin n / n⁴|` ≤ `1/n⁴` |

**Sık çıkan soru tipleri:**

```
Q: Σ n/(n²√n + 2n + 1) → Limit Comparison ile 1/n^(3/2) ile karşılaştır
Q: Σ sin(n)/n⁴ → Mutlak yakınsaklık + Karşılaştırma
Q: Σ 1/(n(ln n + 1)²) → Integral Test, u = ln x + 1
Q: Σ (1 - 2/3n²)^n² → nth term test, limit = e^(-2/3) ≠ 0 → ıraksar
Q: Σ 1/(n²√n) → p-serisi, p = 5/2 > 1 → yakınsak
Q: Σ (2n²+n)/(3n³+4n+2) → Limit Comparison ile 1/n
```

**Önemli formüller:**

```
lim(n→∞) (1 + x/n)^n = e^x

Geometric: Σ r^n = 1/(1-r)  eğer |r| < 1

Integral Test: a_n = f(n), f azalan ve pozitif ise
              Σ a_n yakınsak ⟺ ∫f(x)dx yakınsak
```

---

### B) POWER SERIES — YAKINSAKLIK ARALIĞI
*Her midterm'in neredeyse tamamında, 14-25 puan*

**Standart prosedür (her seferinde aynı):**

1. Ratio Test uygula → `ρ = lim|a_{n+1}/a_n| = L·|x-a|`
2. `L·|x-a| < 1` → Mutlak yakınsaklık aralığı bul
3. Endpoint'leri kontrol et (x = sol ve sağ uç)
   - Alternating series testi ile mi yakınsıyor?
   - Harmonic series (`Σ 1/n`) → ıraksar
   - p-series ile kontrol
4. Yarıçap R ve interval `[a, b)` veya `(a, b]` vs. yaz

**Sık çıkan seriler:**

```
Σ (-1)^n (x-2)^n / (3^n √n ln n)   → R=3, aralık: (-1, 5]
Σ (x-2)^n / (n·5^n)                → R=5, aralık: [-3, 7)
Σ (-1)^n (x-1)^n / (n·3^n)         → R=3, aralık: (-2, 4]
Σ (x-5)^n / (2^n √n)               → R=2, aralık: [3, 7)
Σ (x-1)^n / √n                     → R=1, aralık: [0, 2)
Σ (-1)^(n+1) (x+7)^n / (n·7^n)     → R=7, aralık: (-14, 0]
```

**Endpoint analizi şablonu:**
- Sol uç genellikle: `(-1)^n · (-1)^n = 1` → harmonic → ıraksar
- Sağ uç genellikle: alternating series → yakınsak (koşullu)

---

### C) TAYLOR / MACLAURIN SERİSİ
*9/11 midterm'de çıktı, 10-30 puan*

**Tip 1: Belirli mertebede Taylor polinomu**

```
f(x) = ln(1 + sin x),  x=0'da 3. mertebe:
  f(0)=0, f'(0)=1, f''(0)=-1, f'''(0)=1
  P₃(x) = x - x²/2 + x³/6

g(x) = e^(x+sin x),  x=0'da 2. mertebe:
  g(0)=1, g'(0)=2, g''(0)=4
  P₂(x) = 1 + 2x + 2x²
```

**Tip 2: Tam Taylor serisi**

```
f(x) = 1/x² at x=3:
  f^(n)(x) = (-1)^n (n+1)! x^(-n-2)
  → Σ (-1)^n (n+1)(x-3)^n / 3^(n+2)

f(x) = 2/x³ at x=4:
  → Σ (-1)^n (n+2)(n+1)(x-4)^n / 4^(n+3)

f(x) = 1/x at x=-1:
  → Σ -(x+1)^n
```

**Tip 3: Bilinen seriden substitution ile**

```
ln(1+x) = Σ (-1)^(n+1) x^n/n,  |x| ≤ 1

x² ln(1+x³): x yerine x³ koy
  → Σ (-1)^(n+1) x^(3n+2)/n

g(x) = x³/(4+x²):
  = (x³/4) · 1/(1+x²/4)
  = Σ (-1)^n x^(2n+3)/4^(n+1)

1/(1-2x): x yerine 2x koy
  → Σ 2^n x^n
```

**Ezberlenecek temel seriler:**

```
1/(1-x) = Σ x^n                     |x| < 1
e^x      = Σ x^n/n!                  tüm x
sin x    = Σ (-1)^n x^(2n+1)/(2n+1)! tüm x
cos x    = Σ (-1)^n x^(2n)/(2n)!     tüm x
ln(1+x)  = Σ (-1)^(n+1) x^n/n       -1 < x ≤ 1
```

---

### D) KONİK KESİTLER
*8/11 midterm'de çıktı, 10-25 puan*

**Ellips:**

```
Standart form: (x-h)²/a² + (y-k)²/b² = 1  (a > b)
a² = b² + c²  (c = fokal uzaklık)
Odaklar:  (h ± c, k)
Köşeler:  (h ± a, k)

Tipik soru: 9x² + 108x + 16y² - 96y + 324 = 0 → kareyi tamamla
  → (x+6)²/16 + (y-3)²/9 = 1
  → Merkez: (-6,3), a=4, b=3, c=√7
  → Odaklar: (-6±√7, 3), Köşeler: (-10,3) ve (-2,3)
```

**Hiperbol:**

```
x²/a² - y²/b² = 1  (yatay)  veya  y²/a² - x²/b² = 1  (dikey)
c² = a² + b²
Asimptotlar: y = ±(b/a)x  (yatay hiperbol için)

Tipik: x²/4 - y²/9 = 1
  → a=2, b=3, c=√13
  → Asimptot: y = ±(3/2)x
```

**Parabol:**

```
y² = -4px  (sola açılan) → Odak: (-p, 0), Doğrultman: x = p
x² = 4py   (yukarı)     → Odak: (0, p),  Doğrultman: y = -p

Tipik: -3x = 8y² → y² = -(3/8)x → 4p = 3/8 → p = 3/32
  → Odak: (-3/32, 0), Doğrultman: x = 3/32
```

---

### E) POLAR KOORDİNATLAR — ALAN
*7/11 midterm'de çıktı, 15-20 puan*

**Alan formülü:**

```
A = (1/2) ∫[α to β] r² dθ
```

**Sık çıkan sonuçlar:**

| Eğri | Aralık | Alan |
|------|--------|------|
| r = 2 + cos θ | 0 → 2π (tam) | 9π/2 |
| r = sin(3θ), bir yaprak | 0 → π/3 | π/12 |
| r = cos(5θ), bir yaprak | 0 → π/10 | π/20 |
| r = 3θ | 0 → π | 3π³/2 |

**Şablon çözüm (r = sin 3θ, π/6 ≤ θ ≤ π/3):**

```
A = (1/2)∫sin²(3θ)dθ
  = (1/4)∫(1 - cos 6θ)dθ
  = (1/4)[θ - sin(6θ)/6]
  = π/24
```

**Kimlik:** `sin²θ = (1 - cos 2θ)/2`  ve  `cos²θ = (1 + cos 2θ)/2`

**Arc Length:**

```
L = ∫√(r² + (dr/dθ)²) dθ

r = e^(2θ), 0 ≤ θ ≤ π/2:
  dr/dθ = 2e^(2θ)
  L = ∫√(e^(4θ) + 4e^(4θ)) dθ = √5 · (e^π - 1)/4
```

---

### F) 3D VEKTÖRLER & DOĞRU/DÜZLEM
*Midterm 2'lerde neredeyse garantili, 24-30 puan*

**Dot Product:**

```
u·v = u₁v₁ + u₂v₂ + u₃v₃
cos θ = (u·v) / (||u||·||v||)
Scalar projection: comp_v u = (u·v) / ||v||
Vector projection: proj_v u = (u·v / ||v||²) · v
```

**Cross Product:**

```
u × v = | i   j   k  |
        | u₁  u₂  u₃ |
        | v₁  v₂  v₃ |

||u × v|| = ||u||·||v||·sin θ
Alan_üçgen = (1/2) ||AB × AC||
```

**Düzlem denklemi:**

```
Normal n = <a,b,c>, nokta P₀ = (x₀,y₀,z₀):
  a(x-x₀) + b(y-y₀) + c(z-z₀) = 0

İki doğrunun kapsadığı düzlem:
  n = yön₁ × yön₂  (çarpım normaldir)

Küreye teğet düzlem → merkezden uzaklık = yarıçap kullan
```

**Parametrik doğru:**

```
Yön vektörü v = <a,b,c>, nokta P₀ = (x₀,y₀,z₀):
  x = x₀+at,  y = y₀+bt,  z = z₀+ct

İki doğrunun kesişimi: parametreleri (t ve k) denkleme yaz, çöz
```

**Küre:**

```
(x-h)² + (y-k)² + (z-l)² = R²
Merkez: (h,k,l),  Yarıçap: R

Küre-düzlem kesişim dairesi:
  d = merkezden düzleme uzaklık
  r_çember = √(R² - d²)
```

---

### G) DİZİLERİN LİMİTİ
*5/11 midterm'de çıktı*

**Temel formüller:**

```
lim(1 + x/n)^n = e^x
lim(1 - 1/n²)^n² = e^(-1) = 1/e
lim(n²-1/n²)^(n²) = e^(-1)

L'Hopital: lim ln(n²+n)/√n → ∞/∞ → L'Hopital → 0

Tipik: lim((3n+1)/(3n-1))^n
  = e^(lim n·ln((3n+1)/(3n-1)))
  = e^(lim 2/(3-1/n))  [L'Hopital sonrası]
  = e^(2/3)
```

---

### H) ÇOK DEĞİŞKENLİ FONKSİYONLAR
*Son 2 yılda Midterm 2'de çıkıyor, 10-15 puan*

```
Tanım Bölgesi: İneşitliği çöz ve grafiğini çiz
  f(x,y) = ln(4-x²-y²) → x²+y² < 4  (açık disk)
  f(x,y) = 1/√(y-x)   → y > x       (doğrunun üstü, açık)

Level curves: f(x,y) = c sabit değer için eğriyi çiz

Limit — İki yol testi:
  lim x³y/(x⁶+y²): y = mx³ yolu ile m/(1+m²) → m'ye bağımlı → limit yok

Kısmi türev:
  ∂f/∂x: y sabit tut, x'e göre türev al
  ∂f/∂y: x sabit tut, y'ye göre türev al
```

---

## 3. SINAV FORMATINA GÖRE KONU DAĞILIMI

### Midterm 1 (Tipik)
| Konu | Puan |
|------|------|
| Konik Kesitler (Ellips + Hiperbol veya Parabol) | ~30-35 |
| Polar Koordinatlar (Alan + bazen arc length/symmetry) | ~25-35 |
| Diziler & Seriler (temel) | ~30-35 |
| **Toplam** | **100** |

### Midterm 2 (Tipik)
| Konu | Puan |
|------|------|
| Seri Yakınsaklık Testleri | ~20-28 |
| Power Series (Yakınsaklık Aralığı) | ~14-15 |
| Taylor/Maclaurin Serisi | ~14-15 |
| 3D Vektörler & Düzlem/Doğru | ~28-30 |
| Çok Değişkenli Fonksiyon | ~10-15 |
| **Toplam** | **100** |

---

## 4. SON 1 GÜN İÇİN ÖNERİLEN ÇALIŞMA PLANI

### Saat 1 (En kritik): Seri testleri
- p-serisi, nth term, comparison, integral test, geometric series ezberle
- 3-4 farklı tipten soru çöz

### Saat 2: Power Series
- Ratio test → aralık bul → endpoint kontrolü şablonunu ezberle
- Son 3 sınav sorusunu baştan yeniden çöz

### Saat 3: Taylor/Maclaurin
- Temel 5 seriyi ezberle (1/(1-x), e^x, sin, cos, ln(1+x))
- Türev yöntemi + substitution yöntemi pratik yap

### Saat 4: Konik Kesitler + Polar Alan
- Ellips/hiperbol/parabol formüllerini tekrar et
- A = (1/2)∫r²dθ ile 2 soru çöz

### Saat 5: 3D Vektörler (Midterm 2 ise)
- Dot product, cross product, düzlem denklemi prosedürünü tekrar et

---

## 5. EN ÇOK TEKRAR EDEN SORU TİPİ

**Power Series yakınsaklık aralığı + endpoint kontrolü** — 11 sınavdan 9'unda çıkmış.
Asla atlama. Ratio test → aralık → iki endpoint → alternating/harmonic kontrol → sonuç şablonu bilinçaltına kadar girmeli.

**r = 2 + cosθ etrafındaki alan** — Aynı soru kelimesi kelimesine 2 farklı midterm'de çıktı (Fall 23-24 M1 ve Fall 24-25 M2). Cevap: **9π/2**

**Hiperbol asimptot + sketch** — Her Spring midterm'inde en az bir kez çıkmış.
