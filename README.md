# DDD (Domain-Driven Design) ve Nest.js Giriş

DDD (Domain-Driven Design), yazılım projelerinde karmaşık iş gereksinimlerini daha iyi anlamak ve yönetmek için kullanılan bir mimari yaklaşımdır. Nest.js, TypeScript ile yazılmış bir Node.js framework'üdür ve DDD mimarisine uygun projeler geliştirmek için güçlü özellikler sunar.

---

## **1. DDD Nedir?**
DDD, yazılım geliştirme sürecinde iş mantığını merkezine alan bir yaklaşım olup, karmaşık alanları yönetilebilir parçalara böler. Temel bileşenleri:

- **Domain (Alan):** Uygulamanın temel iş mantığıdır.
- **Entities (Varlıklar):** Kimliği olan iş nesneleri.
- **Value Objects (Değer Nesneleri):** Kimliği olmayan, değerleriyle eşitliği belirlenen nesneler.
- **Aggregates (Kümeler):** İş mantığını korumak için gruplandırılmış varlıklar ve değer nesneleri.
- **Repositories (Depolar):** Veriye erişimi soyutlayan bileşenler.
- **Services (Hizmetler):** İş mantığını işleyen kurallar.

---

## **2. Nest.js ve DDD Mimarisine Giriş**
Nest.js, modüler ve ölçeklenebilir bir yapı sunarak DDD uygulamaları için ideal bir ortam sağlar. Temel öğeler şunlardır:

- **Modules (Modüller):** Uygulamanın yapı taşları.
- **Controllers (Denetleyiciler):** İstekleri işleyen bileşenler.
- **Providers (Sağlayıcılar):** İş mantığını temsil eden bileşenler.
- **Services (Servisler):** İş mantığını uygulayan sınıflar.
- **Repositories (Depolar):** Veritabanı işlemlerini soyutlayan sınıflar.

---

### **Başlangıç Proje Yapısı**
```
/src
  /application  --> Uygulama katmanı
  /domain       --> İş mantığı
  /infrastructure --> Veri erişimi ve altyapı
  /interfaces   --> API ve dış dünyayla etkileşim
  main.ts
```

---

Sıradaki konuya geçmek için **"sonrakine geç"** diyebilirsiniz.
