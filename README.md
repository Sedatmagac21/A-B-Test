#  A/B Testi

## 📌 Giriş

A/B testleri, veri odaklı karar alma süreçlerinin temel taşlarından biridir. Özellikle ürün geliştirme, kullanıcı deneyimi (UX), pazarlama ve makine öğrenmesi değerlendirmelerinde; iki farklı grubun  istatistiksel olarak anlamlı biçimde farklı olup olmadığını belirlemek kritik öneme sahiptir.

Bu projede, **varyansların eşit olduğu varsayımına ihtiyaç duymayan Welch t-testi** kullanılarak, iki bağımsız örneklem arasındaki ortalama farkı test eden **uçtan uca bir A/B test altyapısı** geliştirilmiştir. Amaç yalnızca bir p-değeri hesaplamak değil; sürecin tamamını **istatistiksel olarak doğru, sayısal olarak kararlı ve test edilebilir** bir biçimde uygulamaktır.

Bu bağlamda proje, hem istatistik temellerini öğrenmek isteyenler hem de A/B testlerini kod seviyesinde doğru şekilde uygulamak isteyenler için öğretici bir referans niteliğindedir.

---

## 🎯 Projenin Amacı

Bu çalışmanın temel amaçları:

* İki bağımsız grubun ortalamalarını karşılaştırmak
* Varyansların eşit olmadığı durumlarda doğru istatistiksel test uygulamak
* Welch–Satterthwaite yaklaşımı ile serbestlik derecesini hesaplamak
* Test istatistiği ve p-değerini manuel olarak elde etmek
* Anlamlılık düzeyi (α) üzerinden **hipotez kararı** vermek
* Tüm süreci **unit testler** ile doğrulamak

---

## 🧪 İstatistiksel Arka Plan

Test edilen sıfır hipotezi:

> **H₀:** Kontrol grubu ile varyant grubunun ortalamaları eşittir.

Welch t-testi, klasik Student t-testine kıyasla şu durumlarda tercih edilir:

* Grup varyansları farklıysa
* Örneklem büyüklükleri eşit değilse

Bu özellikleri sayesinde gerçek dünya A/B testlerinde daha güvenilir sonuçlar üretir.

---

## 🔁 Test Akışı

A/B test süreci aşağıdaki adımlardan oluşur:

1. **Tanımlayıcı İstatistiklerin Hesaplanması**

   * Örneklem sayısı (n)
   * Aritmetik ortalama (x̄)
   * Örneklem standart sapması (s, ddof=1)

2. **Serbestlik Derecesi (Welch–Satterthwaite)**

3. **t-istatistiğinin Hesaplanması**

4. **İki yönlü p-değerinin Bulunması**

5. **Hipotez Kararı**

   * H₀ reddedilir / reddedilmez

---

## 🧩 Gerçeklenen Fonksiyonlar

| Fonksiyon                                | Açıklama                                    |
| ---------------------------------------- | ------------------------------------------- |
| `get_stats(X)`                           | Verilen diziden (n, ortalama, std) hesaplar |
| `degrees_of_freedom(n_v, s_v, n_c, s_c)` | Welch–Satterthwaite serbestlik derecesi     |
| `t_value(...)`                           | Welch t-istatistiğini hesaplar              |
| `p_value(d, t_value)`                    | İki yönlü p-değeri döndürür                 |
| `make_decision(X_v, X_c, alpha)`         | Nihai hipotez kararını verir                |

---

## ✅ Unit Testler

Projede yer alan tüm fonksiyonlar, önceden tanımlanmış **sayısal doğruluk testleri** ile kontrol edilmiştir. Testler şunları garanti eder:

* Hesaplanan değerlerin teorik sonuçlarla uyumu
* Serbestlik derecesinin doğru hesaplanması
* p-değeri ve karar mekanizmasının tutarlılığı

Bu yaklaşım, istatistiksel kodların güvenilirliğini artırır.

---

## 📂 Proje Yapısı

```text
.
├── C3W4_Assignment.ipynb      # Tüm hesaplamaların yer aldığı notebook
├── w4_unittest.py            # Unit testler
├── background_color_experiment.csv
└── README.md
```

---

## 🚀 Çalıştırma

Gerekli kütüphaneler:

```bash
pip install numpy scipy
```

Unit testleri çalıştırmak için:

```bash
python w4_unittest.py
```

Alternatif olarak, tüm süreci adım adım incelemek için Jupyter Notebook kullanılabilir.

---



## 📚 Kaynakça

* Welch, B. L. (1947). *The generalization of Student's problem when several different population variances are involved.*
* SciPy Statistics Dokümantasyonu

---

> Bu proje; istatistik, veri bilimi ve makine öğrenmesi değerlendirme süreçlerinde A/B testlerinin doğru şekilde nasıl uygulanacağını göstermek amacıyla hazırlanmıştır.
