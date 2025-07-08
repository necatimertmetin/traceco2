# 🌍 TraceCO2

**TraceCO2**, Avrupa’daki tüketicilerin ve markaların ürün bazlı karbon ayak izini şeffaf şekilde takip etmelerini sağlayan bir platformdur.

---

## 🚀 Proje Hakkında

- **Amaç:** Ürünlerin ham maddeden mağazaya kadar tüm tedarik zinciri boyunca karbon ayak izini izlemek.
- **Teknoloji Yığını:**
  - **Monorepo:** [Nx](https://nx.dev)
  - **Frontend:** React (Vite)
  - **Backend:** NestJS
  - **Auth:** Keycloak (opsiyonel)
  - **Database:** PostgreSQL

---

## 📁 Monorepo Yapısı

```
traceco2/
 ├── apps/
 │   ├── frontend/   # React + Vite uygulaması
 │   └── backend/    # NestJS API
 ├── libs/           # Ortak paylaşılan kütüphaneler (opsiyonel)
 ├── nx.json
 ├── tsconfig.base.json
 ├── workspace.json
 └── README.md
```

---

## ⚙️ Başlangıç

### 1️⃣ Bağımlılıkları Kur

```bash
npm install
```

---

### 2️⃣ Uygulamaları Çalıştır

**Frontend:**
```bash
nx serve frontend
```

**Backend:**
```bash
nx serve backend
```

Her ikisi de kendi portlarında ayağa kalkar.

---

## 🗃️ Çevre Değişkenleri

Aşağıdaki örnek `.env` dosyasını `apps/backend/` veya proje kök dizinine ekle:

```env
DATABASE_URL=postgres://<username>:<password>@localhost:5432/traceco2
JWT_SECRET=your_jwt_secret_key
```

Keycloak kullanacaksan `.env` içine Keycloak endpoint ve client ayarlarını da ekle.

## 🐳 Docker

Projeyi yerel makinanda tek komutla ayağa kaldırmak için **Docker** kullanabilirsin.  
Bu setup şunları içerir:
- PostgreSQL veritabanı
- NestJS Backend API
- React + Vite Frontend
- Keycloak Kimlik Yönetimi

---

### Çalıştırmak için

```bash
docker compose up --build
```

İlk çalıştırmada backend, frontend ve Keycloak için **Dockerfile** üzerinden build işlemi yapılır.  
Sonraki başlatmalarda sadece:

```bash
docker compose up
```

kullanman yeterli olur.

---

### 🗂️ Servisler

| Servis         | Açıklama        | URL                                                               |
| -------------- | --------------- | ----------------------------------------------------------------- |
| **Frontend**   | React + Vite    | [http://localhost:3000](http://localhost:3000)                    |
| **Backend**    | NestJS API      | [http://localhost:3333](http://localhost:3333)                    |
| **PostgreSQL** | Veritabanı      | `localhost:5432` (user/pass: `traceco2`)                          |
| **Keycloak**   | Kimlik Yönetimi | [http://localhost:8080](http://localhost:8080) <br> admin / admin |

---

### ⚙️ Ortam Değişkenleri

Backend için örnek `.env`:
```env
DATABASE_URL=postgres://traceco2:traceco2@postgres:5432/traceco2
KEYCLOAK_URL=http://keycloak:8080
JWT_SECRET=your_secret_key_here
```

---

### 🔑 Keycloak Yapılandırması

İlk kez çalıştırdığında:
1. [http://localhost:8080](http://localhost:8080) adresinden Keycloak admin paneline `admin/admin` ile giriş yap.
2. Realm oluştur, client tanımla, roller ve kullanıcıları yapılandır.
3. Backend Keycloak ayarlarını bu URL üzerinden yönet.

---

### 🗃️ Komutlar

İlk kurulum:
```bash
docker compose up --build
```

Durdurmak için:
```bash
docker compose down
```

Veri kaybını engellemek için PostgreSQL `volumes` tanımı kullanılır.

---

Hazır! 🚀

----

## ✅ Komutlar

| Amaç                    | Komut                    |
| ----------------------- | ------------------------ |
| Tüm projeleri listele   | `nx show projects`       |
| Tek projeyi detaylı gör | `nx show project <name>` |
| Bağımlılık grafiği      | `nx graph`               |
| Build Frontend          | `nx build frontend`      |
| Build Backend           | `nx build backend`       |
| Test Frontend           | `nx test frontend`       |
| Test Backend            | `nx test backend`        |

---

## ✨ Yol Haritası

- [x] Nx monorepo kurulumu
- [x] Frontend: React + Vite
- [x] Backend: NestJS API
- [ ] Auth: Keycloak entegrasyonu
- [ ] PostgreSQL üretim veritabanı bağlantısı
- [ ] CI/CD pipeline
- [ ] Production Docker config
- [ ] Avrupa pilot işbirlikleri

---

## 🤝 Katkıda Bulun

Pull request’ler, issue’lar ve öneriler memnuniyetle karşılanır!

---

## 📜 Lisans

MIT License © [TraceCO2 Team]
