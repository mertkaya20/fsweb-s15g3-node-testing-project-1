# 🧪 JavaScript Unit Testing with Jest

A focused exercise repository demonstrating core JavaScript concepts — object manipulation, constructor functions, and asynchronous programming — paired with a comprehensive **Jest** unit test suite written using the Arrange-Act-Assert pattern.

_A focused exercise repository demonstrating core JavaScript concepts | Kapsamlı bir Jest birim test paketi_

---

## 🇬🇧 English

### 📖 Overview

This project is a deliberate, test-driven exploration of fundamental JavaScript patterns that show up constantly in real-world applications: trimming and transforming object data, building reusable object factories with constructor functions, and handling asynchronous operations with Promises.

Rather than just writing the implementation, the primary goal of this repository was to **practice writing meaningful unit tests** with Jest — covering edge cases, asynchronous assertions, and using `beforeEach` to keep tests isolated and predictable.

### 🎯 What Was Built

#### Utility Functions (`index.js`)

| Function                    | Purpose                                                                                                                                                                                                                          |
| --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `nesneyiTrimle(obj)`        | Trims whitespace from **every** string property of an object, returning a new object (no mutation).                                                                                                                              |
| `verileniTrimle(obj, prop)` | Trims whitespace from a **single, specified** property only, leaving the rest of the object untouched.                                                                                                                           |
| `enBuyukTamsayiyiBul(arr)`  | Finds the largest integer within an array of objects, each shaped like `{ tamsayi: number }`.                                                                                                                                    |
| `Sayici(ilkSayi)`           | A constructor function that builds a countdown counter object. Calling `.asagiSay()` returns the current value, then decrements — and never drops below zero.                                                                    |
| `Mevsimler()`               | A constructor function modeling a cyclical season tracker. Calling `.sonraki()` advances through `yaz → sonbahar → kış → ilkbahar` and loops infinitely.                                                                         |
| `Araba(isim, depo, kml)`    | A constructor function simulating a car with a fuel tank. `.sur(km)` drives the car, consuming fuel proportionally and capping distance when the tank runs dry. `.benzinal(litre)` refuels the tank, capped at maximum capacity. |
| `asenkronCiftSayi(sayi)`    | Returns a `Promise` that resolves to `true`/`false` depending on whether the given number is even — used to practice testing asynchronous code.                                                                                  |

#### Test Suite (`index.test.js`)

Each function above is covered by a dedicated `describe` block containing multiple `test` cases, including:

- **Happy path** scenarios (expected, typical inputs)
- **Boundary conditions** (e.g., counter hitting zero, fuel tank running empty, season cycle wrapping around)
- **State isolation** via `beforeEach`, ensuring every test starts from a clean, predictable object instance
- **Asynchronous assertions** using `async/await` to properly resolve and test Promise-based functions

### 🛠️ Tech Stack

| Technology | Purpose                         |
| ---------- | ------------------------------- |
| Node.js    | Runtime environment             |
| Jest       | Test runner & assertion library |

### ⚙️ Getting Started

```bash
# Clone the repository
git clone https://github.com/mertkaya20/fsweb-s15g3-node-testing-project-1.git
cd fsweb-s15g3-node-testing-project-1

# Install dependencies
npm install

# Run the test suite
npx jest
```

### 📁 Project Structure

```
.
├── index.js          # Utility function & constructor implementations
├── index.test.js      # Jest test suite
├── jest.config.js     # Jest configuration
├── package.json
└── README.md
```

### 💡 Key Learnings & Design Notes

- **Constructor functions vs. plain objects** — `Sayici`, `Mevsimler`, and `Araba` all demonstrate the value of building reusable object "factories" with `this` and `new`, instead of duplicating object literals by hand.
- **Immutability** — `nesneyiTrimle` and `verileniTrimle` both return _new_ objects via the spread operator rather than mutating the input, a habit that prevents subtle bugs in larger applications.
- **Testing async code properly** — rather than asserting directly on a Promise object, tests use `async/await` to unwrap the resolved value before making assertions.
- **Test isolation** — `beforeEach` recreates a fresh instance before every test, preventing state from one test leaking into another (a classic source of flaky tests).

---

## 🇹🇷 Türkçe

### 📖 Genel Bakış

Bu proje, gerçek dünya uygulamalarında sürekli karşımıza çıkan temel JavaScript kalıplarının test odaklı bir şekilde incelenmesidir: nesne verilerini trimleme ve dönüştürme, constructor fonksiyonlarıyla yeniden kullanılabilir nesne fabrikaları oluşturma ve Promise'lerle asenkron işlemleri yönetme.

Bu repodaki asıl amaç sadece fonksiyonları yazmak değil, **Jest ile anlamlı unit testler yazmayı pratik etmekti** — sınır durumlarını (edge case), asenkron assertion'ları kapsamak ve `beforeEach` kullanarak testleri birbirinden izole ve öngörülebilir tutmak.

### 🎯 Neler Geliştirildi

#### Yardımcı Fonksiyonlar (`index.js`)

| Fonksiyon                   | Amacı                                                                                                                                                                                                           |
| --------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `nesneyiTrimle(obj)`        | Bir nesnenin **tüm** string proplarındaki boşlukları temizler, orijinal nesneyi değiştirmeden yeni bir nesne döndürür.                                                                                          |
| `verileniTrimle(obj, prop)` | Sadece **belirtilen tek bir** propu trimler, geri kalan proplara dokunmaz.                                                                                                                                      |
| `enBuyukTamsayiyiBul(arr)`  | `{ tamsayi: number }` şeklindeki nesnelerden oluşan bir dizide en büyük tamsayıyı bulur.                                                                                                                        |
| `Sayici(ilkSayi)`           | Geriye doğru sayan bir sayaç nesnesi oluşturan constructor fonksiyon. `.asagiSay()` mevcut değeri döndürür, sonra azaltır — asla sıfırın altına inmez.                                                          |
| `Mevsimler()`               | Döngüsel bir mevsim takipçisi modelleyen constructor fonksiyon. `.sonraki()` çağrıldıkça `yaz → sonbahar → kış → ilkbahar` sırasıyla ilerler ve sonsuz döngüde devam eder.                                      |
| `Araba(isim, depo, kml)`    | Yakıt deposu olan bir araba simüle eden constructor fonksiyon. `.sur(km)` aracı sürer, orantılı yakıt tüketir ve depo bitince mesafeyi sınırlar. `.benzinal(litre)` depoyu doldurur, maksimum kapasiteyi aşmaz. |
| `asenkronCiftSayi(sayi)`    | Verilen sayının çift olup olmadığına göre `true`/`false` ile çözümlenen bir `Promise` döndürür — asenkron kod test etme pratiği için kullanılır.                                                                |

#### Test Paketi (`index.test.js`)

Yukarıdaki her fonksiyon, birden fazla `test` senaryosu içeren ayrı bir `describe` bloğu ile kapsanmıştır:

- **Beklenen senaryolar** (tipik, normal girdiler)
- **Sınır durumları** (sayacın sıfıra ulaşması, depo benzininin bitmesi, mevsim döngüsünün başa sarması gibi)
- **State izolasyonu** — `beforeEach` ile her testin temiz ve öngörülebilir bir nesne örneğiyle başlaması sağlanır
- **Asenkron assertion'lar** — Promise tabanlı fonksiyonları doğru şekilde çözümlemek ve test etmek için `async/await` kullanılır

### 🛠️ Teknoloji Yığını

| Teknoloji | Amacı                                     |
| --------- | ----------------------------------------- |
| Node.js   | Çalışma zamanı ortamı                     |
| Jest      | Test çalıştırıcı ve assertion kütüphanesi |

### ⚙️ Kurulum

```bash
# Repoyu klonlayın
git clone https://github.com/mertkaya20/fsweb-s15g3-node-testing-project-1.git
cd fsweb-s15g3-node-testing-project-1

# Bağımlılıkları yükleyin
npm install

# Test paketini çalıştırın
npx jest
```

### 📁 Proje Yapısı

```
.
├── index.js          # Yardımcı fonksiyon & constructor implementasyonları
├── index.test.js      # Jest test paketi
├── jest.config.js     # Jest konfigürasyonu
├── package.json
└── README.md
```

### 💡 Öne Çıkan Öğrenimler ve Tasarım Notları

- **Constructor fonksiyonlar vs. düz nesneler** — `Sayici`, `Mevsimler` ve `Araba`, nesne literallerini elle tekrar tekrar yazmak yerine `this` ve `new` ile yeniden kullanılabilir nesne "fabrikaları" oluşturmanın değerini gösteriyor.
- **Immutability (değişmezlik)** — `nesneyiTrimle` ve `verileniTrimle`, girdiyi değiştirmek yerine spread operatörü ile _yeni_ nesneler döndürüyor; bu, büyük uygulamalarda gizli hataları önleyen bir alışkanlık.
- **Asenkron kodu doğru test etmek** — Promise objesini doğrudan kontrol etmek yerine, testler çözümlenen değeri almak için `async/await` kullanıyor.
- **Test izolasyonu** — `beforeEach`, her testten önce taze bir örnek oluşturarak bir testin state'inin diğerine sızmasını engelliyor (kararsız/flaky testlerin klasik bir kaynağı).

---

## 📬 Contact / İletişim

**Mert Kaya**

[![GitHub](https://img.shields.io/badge/GitHub-mertkaya20-181717?style=flat&logo=github)](https://github.com/mertkaya20)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-merttkaya20-0A66C2?style=flat&logo=linkedin)](https://www.linkedin.com/in/merttkaya20/)

---

_Built as part of a Full Stack Bootcamp — WorkInTech_
