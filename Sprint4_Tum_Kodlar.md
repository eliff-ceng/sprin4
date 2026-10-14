# Sprint 4 - Tüm Kodlar

Bu dosya Sprint 4 teslimindeki tüm metin tabanlı kaynak/config dosyalarını tek yerde toplar.


## `README.md`

```markdown
Canlı site: BURAYA-VERCEL-LINKINI-YAZ

# Sprint 4 - Vite, TypeScript ve React

Bu teslimde Sprint 3 uygulaması React + TypeScript yapısına taşınmıştır. `sprint3` klasörüne dokunulmaz; yeni uygulama repository kökündeki `frontend/` klasöründedir.

## Çalıştırma

```bash
cd frontend
npm install
npm run dev
```

Vite geliştirme adresi varsayılan olarak `http://localhost:5173` olur. Bu sprintte Live Server kullanılmaz.

## Adım 2 - Dosyaların görevleri

- `frontend/package.json`: Proje adı, `dev/build/preview` komutları ve paket listesini tutar.
- `frontend/package-lock.json`: `npm install` sonrasında kurulan paket sürümlerini kilitler.
- `frontend/node_modules/`: İndirilen bağımlılıklar burada oluşur; `.gitignore` nedeniyle GitHub'a gönderilmez.
- `frontend/tsconfig*.json`: TypeScript derleme ve tip kontrolü ayarlarını içerir.
- `frontend/vite.config.ts`: Vite ve React eklentisi yapılandırmasıdır.
- `frontend/index.html`: Uygulamanın tek HTML dosyasıdır ve `div#root` içerir.
- `frontend/src/main.tsx`: React uygulamasını başlatıp `App` bileşenini `root` içine çizer.
- `frontend/src/App.tsx`: Beş sayfayı, state ile sayfa geçişini, filtrelemeyi, detayı ve formları içerir.
- `frontend/src/App.css`: Sprint 3 görünümünün React uygulamasındaki stilleridir.
- `frontend/src/index.css`: Sprint 4 yönergesine uygun olarak boştur.
- `frontend/public/`: Vite'ın olduğu gibi servis ettiği dosyaları içerir; `afis.svg` burada bulunur.
- `frontend/src/types/campus-event.ts`: `Category` union type ve `CampusEvent` interface tanımlarını içerir.
- `frontend/src/data/events.ts`: Tiplenmiş 6 etkinlik verisini içerir.
- `frontend/src/utils/filter-events.ts`: DOM'a dokunmayan `searchEvents`, `filterByCategory`, `findEventById` saf fonksiyonlarını içerir.

## Kontrol listesi

- Ana sayfa: yaklaşan 2 etkinlik.
- Etkinlikler: toplam 6 etkinlik.
- Aramaya `atölye` yazınca 2 kart.
- Kategori `Atölye` seçilince 2 kart.
- `xyz` aramasında bulunamadı mesajı.
- Event-1 detayında afiş solda, künye sağda.
- Afişi olmayan etkinliklerin detayında boş afiş kutusu yok.
- Detaydaki `Bu etkinliği güncelle` düğmesi Güncelle sayfasını açar.
- Ekle ve Güncelle aynı boş formu farklı başlıkla gösterir.
- Kaydet düğmesi sayfayı yenilemez; bu sprintte kayıt/güncelleme mantığı yoktur.
- Menü geçişlerinde adres çubuğu aynı kalır; React state kullanılır.
- Sekme başlığı `useEffect` ile değişir.

## Build

```bash
cd frontend
npm run build
npm run preview
```

`npm run build` hatasız bitmeden teslim etmeyin.

## Vercel

- Root Directory: `frontend`
- Framework Preset: `Vite`

## Git teslimi

Repository kökünde:

```bash
git add .
git commit -m "Complete sprint 4"
git tag sprint-04
git push
git push --tags
```

```

## `frontend/package.json`

```json
{
  "name": "kampus-etkinlikleri-frontend",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "tsc -b && vite build",
    "lint": "eslint .",
    "preview": "vite preview"
  },
  "dependencies": {
    "react": "^19.1.1",
    "react-dom": "^19.1.1"
  },
  "devDependencies": {
    "@eslint/js": "^9.36.0",
    "@types/node": "^24.5.2",
    "@types/react": "^19.1.16",
    "@types/react-dom": "^19.1.9",
    "@vitejs/plugin-react": "^5.0.4",
    "eslint": "^9.36.0",
    "eslint-plugin-react-hooks": "^5.2.0",
    "eslint-plugin-react-refresh": "^0.4.22",
    "globals": "^16.4.0",
    "typescript": "~5.9.3",
    "typescript-eslint": "^8.45.0",
    "vite": "^7.1.7"
  }
}

```

## `frontend/package-lock.json`

```json
{
  "name": "kampus-etkinlikleri-frontend",
  "version": "0.0.0",
  "lockfileVersion": 3,
  "requires": true,
  "packages": {
    "": {
      "name": "kampus-etkinlikleri-frontend",
      "version": "0.0.0",
      "dependencies": {
        "react": "^19.1.1",
        "react-dom": "^19.1.1"
      },
      "devDependencies": {
        "@eslint/js": "^9.36.0",
        "@types/node": "^24.5.2",
        "@types/react": "^19.1.16",
        "@types/react-dom": "^19.1.9",
        "@vitejs/plugin-react": "^5.0.4",
        "eslint": "^9.36.0",
        "eslint-plugin-react-hooks": "^5.2.0",
        "eslint-plugin-react-refresh": "^0.4.22",
        "globals": "^16.4.0",
        "typescript": "~5.9.3",
        "typescript-eslint": "^8.45.0",
        "vite": "^7.1.7"
      }
    }
  }
}

```

## `frontend/.gitignore`

```text
# Logs
logs
*.log
npm-debug.log*
yarn-debug.log*
yarn-error.log*
pnpm-debug.log*
lerna-debug.log*

node_modules
dist
dist-ssr
*.local

# Editor directories and files
.vscode/*
!.vscode/extensions.json
.idea
.DS_Store
*.suo
*.ntvs*
*.njsproj
*.sln
*.sw?

```

## `frontend/index.html`

```html
<!doctype html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta name="description" content="Kampüs Etkinlikleri - Sprint 4 React ve TypeScript uygulaması" />
    <title>Kampüs Etkinlikleri</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.tsx"></script>
  </body>
</html>

```

## `frontend/vite.config.ts`

```typescript
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";

export default defineConfig({
  plugins: [react()],
});

```

## `frontend/tsconfig.json`

```json
{
  "files": [],
  "references": [
    { "path": "./tsconfig.app.json" },
    { "path": "./tsconfig.node.json" }
  ]
}

```

## `frontend/tsconfig.app.json`

```json
{
  "compilerOptions": {
    "tsBuildInfoFile": "./node_modules/.tmp/tsconfig.app.tsbuildinfo",
    "target": "ES2022",
    "useDefineForClassFields": true,
    "lib": ["ES2022", "DOM", "DOM.Iterable"],
    "module": "ESNext",
    "skipLibCheck": true,
    "moduleResolution": "Bundler",
    "allowImportingTsExtensions": true,
    "verbatimModuleSyntax": true,
    "moduleDetection": "force",
    "noEmit": true,
    "jsx": "react-jsx",
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "erasableSyntaxOnly": true
  },
  "include": ["src"]
}

```

## `frontend/tsconfig.node.json`

```json
{
  "compilerOptions": {
    "tsBuildInfoFile": "./node_modules/.tmp/tsconfig.node.tsbuildinfo",
    "target": "ES2023",
    "lib": ["ES2023"],
    "module": "ESNext",
    "types": ["node"],
    "skipLibCheck": true,
    "moduleResolution": "Bundler",
    "allowImportingTsExtensions": true,
    "verbatimModuleSyntax": true,
    "moduleDetection": "force",
    "noEmit": true,
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "erasableSyntaxOnly": true
  },
  "include": ["vite.config.ts"]
}

```

## `frontend/eslint.config.js`

```javascript
import js from "@eslint/js";
import globals from "globals";
import reactHooks from "eslint-plugin-react-hooks";
import reactRefresh from "eslint-plugin-react-refresh";
import tseslint from "typescript-eslint";
import { defineConfig, globalIgnores } from "eslint/config";

export default defineConfig([
  globalIgnores(["dist"]),
  {
    files: ["**/*.{ts,tsx}"],
    extends: [
      js.configs.recommended,
      tseslint.configs.recommended,
      reactHooks.configs["recommended-latest"],
      reactRefresh.configs.vite,
    ],
    languageOptions: {
      ecmaVersion: 2020,
      globals: globals.browser,
    },
  },
]);

```

## `frontend/src/types/campus-event.ts`

```typescript
export type Category = "Seminer" | "Atölye" | "Söyleşi" | "Yarışma";

export interface CampusEvent {
  id: string;
  title: string;
  category: Category;
  capacity: number;
  date: string;
  time: string;
  location: string;
  description: string;
  image?: string;
}

```

## `frontend/src/data/events.ts`

```typescript
import type { CampusEvent } from "../types/campus-event";

export const events: CampusEvent[] = [
  {
    id: "event-1",
    title: "Kariyer Günleri 2026",
    category: "Seminer",
    date: "12-10-2026",
    time: "14:00",
    location: "A Blok Konferans Salonu",
    description: "Mezunlarla kariyer yolculukları ve sektör deneyimleri üzerine söyleşiler.",
    capacity: 120,
    image: "/afis.svg",
  },
  {
    id: "event-2",
    title: "Robotik Atölyesi",
    category: "Atölye",
    date: "15-10-2026",
    time: "10:00",
    location: "Mühendislik Fakültesi Lab-2",
    description: "Temel sensörler, motor kontrolü ve küçük bir robot uygulaması yapılacak.",
    capacity: 30,
  },
  {
    id: "event-3",
    title: "Siber Güvenlik Söyleşisi",
    category: "Söyleşi",
    date: "21-10-2026",
    time: "13:30",
    location: "B Blok Amfi 1",
    description: "Saldırı yüzeyleri, güvenli yazılım geliştirme ve güncel siber tehditler konuşulacak.",
    capacity: 90,
  },
  {
    id: "event-4",
    title: "Web Tasarım Atölyesi",
    category: "Atölye",
    date: "25-10-2026",
    time: "15:00",
    location: "Bilgisayar Laboratuvarı 3",
    description: "HTML, CSS ve responsive tasarım ile küçük bir arayüz geliştirilecek.",
    capacity: 35,
  },
  {
    id: "event-5",
    title: "Yapay Zeka Semineri",
    category: "Seminer",
    date: "02-11-2026",
    time: "11:00",
    location: "A Blok Konferans Salonu",
    description: "Yapay zekanın eğitimde, yazılımda ve günlük hayatta kullanım alanları ele alınacak.",
    capacity: 150,
  },
  {
    id: "event-6",
    title: "Girişimcilik ve Proje Yarışması",
    category: "Yarışma",
    date: "08-11-2026",
    time: "16:00",
    location: "Teknokent Toplantı Salonu",
    description: "Öğrenci projeleri, ekip kurma ve girişim fikrini geliştirme üzerine bir proje yarışması.",
    capacity: 80,
  },
];

```

## `frontend/src/utils/filter-events.ts`

```typescript
import type { CampusEvent, Category } from "../types/campus-event";

export function searchEvents(
  list: CampusEvent[],
  text: string,
): CampusEvent[] {
  const q = text.trim().toLocaleLowerCase("tr-TR");

  if (q === "") return list;

  return list.filter((event) => {
    const title = event.title.toLocaleLowerCase("tr-TR");
    const description = event.description.toLocaleLowerCase("tr-TR");

    return title.includes(q) || description.includes(q);
  });
}

export function filterByCategory(
  list: CampusEvent[],
  category: Category | "",
): CampusEvent[] {
  if (category === "") return list;

  return list.filter((event) => event.category === category);
}

export function findEventById(
  list: CampusEvent[],
  id: string,
): CampusEvent | undefined {
  return list.find((event) => event.id === id);
}

```

## `frontend/src/main.tsx`

```tsx
import { StrictMode } from "react";
import { createRoot } from "react-dom/client";
import "./index.css";
import App from "./App";

createRoot(document.getElementById("root")!).render(
  <StrictMode>
    <App />
  </StrictMode>,
);

```

## `frontend/src/index.css`

```css

```

## `frontend/src/App.tsx`

```tsx
import { useEffect, useState } from "react";
import "./App.css";
import { events } from "./data/events";
import type { CampusEvent, Category } from "./types/campus-event";
import {
  filterByCategory,
  findEventById,
  searchEvents,
} from "./utils/filter-events";

type PageName = "home" | "events" | "detail" | "add" | "update";

const menuItems: { label: string; page: PageName }[] = [
  { label: "Ana Sayfa", page: "home" },
  { label: "Etkinlikler", page: "events" },
  { label: "Ekle", page: "add" },
];

function formatDate(dateText: string): string {
  const [day, month, year] = dateText.split("-").map(Number);
  const date = new Date(year, month - 1, day);

  return date.toLocaleDateString("tr-TR", {
    day: "numeric",
    month: "long",
    year: "numeric",
  });
}

function dateKey(dateText: string): string {
  const [day, month, year] = dateText.split("-");
  return `${year}-${month}-${day}`;
}

function App() {
  const [page, setPage] = useState<PageName>("home");
  const [selectedId, setSelectedId] = useState<string | null>(null);
  const [searchText, setSearchText] = useState("");
  const [category, setCategory] = useState<Category | "">("");

  function go(next: PageName, id: string | null = null): void {
    setPage(next);
    setSelectedId(id);
    window.scrollTo({ top: 0, behavior: "smooth" });
  }

  const selected = selectedId
    ? findEventById(events, selectedId)
    : undefined;

  const categories = [...new Set(events.map((event) => event.category))];

  const filtered = filterByCategory(
    searchEvents(events, searchText),
    category,
  );

  const upcoming = [...events]
    .sort((a, b) => dateKey(a.date).localeCompare(dateKey(b.date)))
    .slice(0, 2);

  const title =
    page === "home"
      ? "Ana Sayfa"
      : page === "events"
        ? "Tüm Etkinlikler"
        : page === "add"
          ? "Etkinlik Ekle"
          : page === "update"
            ? "Etkinlik Güncelle"
            : selected?.title ?? "Etkinlik Bulunamadı";

  const headerTitle = page === "home" ? "Kampüs Etkinlikleri" : title;

  useEffect(() => {
    document.title = `Kampüs Etkinlikleri — ${title}`;
  }, [title]);

  function renderCard(event: CampusEvent) {
    return (
      <article className="kart" key={event.id}>
        <h2>{event.title}</h2>
        <p className="kategori-etiketi">{event.category}</p>

        <dl className="kart-kunye">
          <div>
            <dt>Tarih</dt>
            <dd>{formatDate(event.date)}</dd>
          </div>
          <div>
            <dt>Saat</dt>
            <dd>{event.time}</dd>
          </div>
          <div>
            <dt>Yer</dt>
            <dd>{event.location}</dd>
          </div>
          <div>
            <dt>Kontenjan</dt>
            <dd>{event.capacity}</dd>
          </div>
        </dl>

        <p>{event.description}</p>

        <a
          className="buton"
          href={`#${event.id}`}
          onClick={(clickEvent) => {
            clickEvent.preventDefault();
            go("detail", event.id);
          }}
        >
          Detayları gör
        </a>
      </article>
    );
  }

  return (
    <>
      <header className="site-header">
        <div className="header-icerik">
          <h1>{headerTitle}</h1>

          <nav className="site-nav" aria-label="Ana menü">
            {menuItems.map((item) => (
              <a
                key={item.page}
                href={`#${item.page}`}
                aria-current={page === item.page ? "page" : undefined}
                onClick={(clickEvent) => {
                  clickEvent.preventDefault();
                  go(item.page);
                }}
              >
                {item.label}
              </a>
            ))}
          </nav>
        </div>
      </header>

      <main>
        {page === "home" && (
          <>
            <section className="intro">
              <h2>Yaklaşan Etkinlikler</h2>
              <p>
                Tarihi en yakın iki kampüs etkinliğini aşağıda
                görebilirsiniz.
              </p>
            </section>

            <section className="etkinlik-listesi">
              {upcoming.map(renderCard)}
            </section>
          </>
        )}

        {page === "events" && (
          <>
            <form
              className="filtre"
              onSubmit={(submitEvent) => submitEvent.preventDefault()}
            >
              <div className="alan-grubu">
                <label htmlFor="arama">Etkinlik ara</label>
                <input
                  type="search"
                  id="arama"
                  placeholder="atölye, kariyer, yapay..."
                  value={searchText}
                  onChange={(changeEvent) =>
                    setSearchText(changeEvent.target.value)
                  }
                />
              </div>

              <div className="alan-grubu">
                <label htmlFor="kategori-filtre">Kategori</label>
                <select
                  id="kategori-filtre"
                  value={category}
                  onChange={(changeEvent) =>
                    setCategory(changeEvent.target.value as Category | "")
                  }
                >
                  <option value="">Tümü</option>
                  {categories.map((item) => (
                    <option key={item} value={item}>
                      {item}
                    </option>
                  ))}
                </select>
              </div>
            </form>

            <p id="sonuc" role="status" aria-live="polite">
              {filtered.length === 0
                ? "Aramanıza uygun etkinlik bulunamadı."
                : `${filtered.length} etkinlik listeleniyor.`}
            </p>

            <section className="etkinlik-listesi">
              {filtered.length > 0 ? (
                filtered.map(renderCard)
              ) : (
                <p className="bos-sonuc">
                  Aramanıza uygun etkinlik bulunamadı.
                </p>
              )}
            </section>
          </>
        )}

        {page === "detail" && !selected && (
          <section className="mesaj hata-kutusu">
            <h2>Etkinlik bulunamadı</h2>
            <p>Seçilen etkinlik bulunamadı veya etkinlik seçilmedi.</p>
            <a
              className="buton"
              href="#events"
              onClick={(clickEvent) => {
                clickEvent.preventDefault();
                go("events");
              }}
            >
              Listeye dön
            </a>
          </section>
        )}

        {page === "detail" && selected && (
          <article
            className={`detay-karti${selected.image ? "" : " detay-afissiz"}`}
          >
            {selected.image && (
              <figure className="afis-figure">
                <img
                  className="afis-gorsel"
                  src={selected.image}
                  alt={`${selected.title} afişi`}
                />
                <figcaption>{selected.title} afişi</figcaption>
              </figure>
            )}

            <div className="detay-icerik">
              <section className="kunye-karti">
                <h2>Etkinlik Künyesi</h2>
                <dl>
                  <div>
                    <dt>Tarih</dt>
                    <dd>{formatDate(selected.date)}</dd>
                  </div>
                  <div>
                    <dt>Saat</dt>
                    <dd>{selected.time}</dd>
                  </div>
                  <div>
                    <dt>Yer</dt>
                    <dd>{selected.location}</dd>
                  </div>
                  <div>
                    <dt>Kategori</dt>
                    <dd>{selected.category}</dd>
                  </div>
                  <div>
                    <dt>Kontenjan</dt>
                    <dd>{selected.capacity} kişi</dd>
                  </div>
                </dl>
              </section>

              <section className="aciklama">
                <h2>Açıklama</h2>
                <p>{selected.description}</p>
              </section>

              <div className="detay-butonlari">
                <a
                  className="buton ikincil"
                  href="#events"
                  onClick={(clickEvent) => {
                    clickEvent.preventDefault();
                    go("events");
                  }}
                >
                  Listeye dön
                </a>
                <a
                  className="buton"
                  href="#update"
                  onClick={(clickEvent) => {
                    clickEvent.preventDefault();
                    go("update", selected.id);
                  }}
                >
                  Bu etkinliği güncelle
                </a>
              </div>
            </div>
          </article>
        )}

        {(page === "add" || page === "update") && (
          <>
            <p className="form-aciklama">
              {page === "add"
                ? "Yeni etkinlik bilgilerini girin. Bu sprintte form yalnızca görünüm amaçlıdır."
                : "Etkinlik bilgilerini düzenleyin. Bu sprintte form doldurulmaz ve veri kaydedilmez."}
            </p>

            <form
              className="form-karti"
              onSubmit={(submitEvent) => submitEvent.preventDefault()}
            >
              <div className="form-alan">
                <label htmlFor="title">Etkinlik Adı *</label>
                <input
                  type="text"
                  id="title"
                  name="title"
                  maxLength={80}
                  placeholder="Örn. Kariyer Günleri 2026"
                />
              </div>

              <div className="form-alan">
                <label htmlFor="category">Kategori *</label>
                <select id="category" name="category" defaultValue="">
                  <option value="" disabled>
                    Seçiniz
                  </option>
                  <option value="Seminer">Seminer</option>
                  <option value="Atölye">Atölye</option>
                  <option value="Söyleşi">Söyleşi</option>
                  <option value="Yarışma">Yarışma</option>
                </select>
              </div>

              <div className="form-alan">
                <label htmlFor="date">Tarih *</label>
                <input type="date" id="date" name="date" />
              </div>

              <div className="form-alan">
                <label htmlFor="time">Saat *</label>
                <input type="time" id="time" name="time" />
              </div>

              <div className="form-alan">
                <label htmlFor="location">Yer *</label>
                <input
                  type="text"
                  id="location"
                  name="location"
                  placeholder="Örn. A Blok Konferans Salonu"
                />
              </div>

              <div className="form-alan">
                <label htmlFor="capacity">Kontenjan</label>
                <input
                  type="number"
                  id="capacity"
                  name="capacity"
                  min={1}
                  max={1000}
                />
              </div>

              <div className="form-alan">
                <label htmlFor="description">Açıklama</label>
                <textarea
                  id="description"
                  name="description"
                  rows={5}
                />
              </div>

              <button className="buton" type="submit">
                Kaydet
              </button>
            </form>
          </>
        )}
      </main>

      <footer className="site-footer">
        <div className="footer-icerik">
          2416501039 - Muhammed Kerim Şahin - 2026
        </div>
      </footer>
    </>
  );
}

export default App;

```

## `frontend/src/App.css`

```css
:root {
  --ana-renk: #159447;
  --ana-koyu: #0d6f34;
  --zemin: #f4f8f5;
  --kart: #ffffff;
  --metin: #1d2b22;
  --soluk: #5e6f64;
  --kenar: #d7e3da;
  --hata: #b42318;
  --hata-zemin: #fff1f0;
  --basari: #16794b;
  --basari-zemin: #effaf3;
  --golge: 0 8px 20px rgba(20, 70, 40, 0.08);
}

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
  color: var(--metin);
  background: var(--zemin);
  line-height: 1.55;
}

.site-header {
  background: var(--ana-renk);
  color: #fff;
  padding: 1.4rem 1rem 1rem;
}

.header-icerik,
main,
.footer-icerik {
  width: min(1100px, calc(100% - 2rem));
  margin-inline: auto;
}

.site-header h1 {
  margin: 0 0 0.75rem;
  font-size: clamp(1.6rem, 4vw, 2.4rem);
}

.site-nav {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
}

.site-nav a {
  color: #fff;
  text-decoration: none;
  padding: 0.45rem 0.75rem;
  border-radius: 0.4rem;
}

.site-nav a:hover,
.site-nav a[aria-current="page"] {
  background: #fff;
  color: var(--ana-koyu);
}

main {
  min-height: 62vh;
  padding: 2rem 0 3rem;
}

.intro {
  margin-bottom: 1.5rem;
}

.intro h2,
.sayfa-baslik {
  margin-top: 0;
}

.etkinlik-listesi {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 1rem;
}

.kart,
.kunye-karti,
.form-karti,
.detay-karti,
.filtre {
  background: var(--kart);
  border: 1px solid var(--kenar);
  border-radius: 0.8rem;
  box-shadow: var(--golge);
}

.kart {
  padding: 1.1rem;
  border-top: 4px solid var(--ana-renk);
}

.kart h2 {
  margin: 0 0 0.25rem;
  font-size: 1.2rem;
}

.kategori-etiketi {
  display: inline-block;
  margin: 0 0 0.8rem;
  color: var(--ana-koyu);
  font-weight: 700;
}

.kart-kunye,
.kunye-karti dl {
  margin: 0;
}

.kart-kunye div,
.kunye-karti dl div {
  display: grid;
  grid-template-columns: 90px 1fr;
  gap: 0.5rem;
  padding: 0.25rem 0;
}

.kart-kunye dt,
.kunye-karti dt {
  font-weight: 700;
}

.kart-kunye dd,
.kunye-karti dd {
  margin: 0;
}

.buton {
  display: inline-block;
  border: 0;
  border-radius: 0.45rem;
  padding: 0.65rem 0.9rem;
  background: var(--ana-renk);
  color: #fff;
  text-decoration: none;
  font: inherit;
  cursor: pointer;
}

.buton:hover {
  background: var(--ana-koyu);
}

.buton.ikincil {
  background: #fff;
  color: var(--ana-koyu);
  border: 1px solid var(--ana-renk);
}

.filtre {
  display: grid;
  grid-template-columns: 1fr 220px;
  gap: 0.8rem 1rem;
  padding: 1rem;
  margin-bottom: 0.5rem;
}

.filtre .alan-grubu {
  display: grid;
  gap: 0.35rem;
}

.filtre label,
.form-karti label {
  font-weight: 700;
}

input,
select,
textarea {
  width: 100%;
  border: 1px solid #aebdb3;
  border-radius: 0.4rem;
  padding: 0.7rem;
  font: inherit;
  background: #fff;
  color: var(--metin);
}

input:focus,
select:focus,
textarea:focus {
  outline: 3px solid rgba(21, 148, 71, 0.18);
  border-color: var(--ana-renk);
}

#sonuc {
  margin: 0.6rem 0 1.2rem;
  color: var(--ana-koyu);
  font-weight: 700;
}

.bos-sonuc {
  grid-column: 1 / -1;
  background: #fff;
  border: 1px dashed var(--kenar);
  padding: 1rem;
  border-radius: 0.6rem;
}

.detay-karti {
  padding: 1rem;
  display: grid;
  grid-template-columns: minmax(230px, 0.8fr) minmax(300px, 1.2fr);
  gap: 1.2rem;
  align-items: start;
}

.detay-karti.detay-afissiz {
  grid-template-columns: 1fr;
}

.afis-figure {
  margin: 0;
}

.afis-gorsel {
  display: block;
  width: 100%;
  max-height: 420px;
  object-fit: cover;
  border: 4px solid #2f4a68;
  outline: 2px solid #d39b7f;
  background: #10233c;
}

.afis-figure figcaption {
  margin-top: 0.55rem;
  color: var(--soluk);
  font-size: 0.9rem;
}

.detay-icerik h1 {
  margin-top: 0;
}

.kunye-karti {
  padding: 1rem;
}

.kunye-karti h2,
.aciklama h2 {
  margin-top: 0;
}

.aciklama {
  margin-top: 1.2rem;
}

.detay-butonlari {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
  margin-top: 1rem;
}

.form-aciklama {
  max-width: 760px;
}

.form-karti {
  padding: 1.2rem;
  max-width: 760px;
}

.form-alan {
  display: grid;
  gap: 0.35rem;
  margin-bottom: 1rem;
}

.mesaj {
  max-width: 760px;
  margin-top: 1rem;
  padding: 1rem;
  border-radius: 0.6rem;
}

.hata-kutusu {
  background: var(--hata-zemin);
  color: #7a1c14;
  border: 1px solid #e08f87;
}

.site-footer {
  border-top: 1px solid var(--kenar);
  padding: 1.5rem 0;
  color: var(--soluk);
  text-align: center;
}

@media (max-width: 850px) {
  .etkinlik-listesi {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }

  .detay-karti {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 620px) {
  .header-icerik,
  main,
  .footer-icerik {
    width: min(100% - 1rem, 1100px);
  }

  .etkinlik-listesi,
  .filtre {
    grid-template-columns: 1fr;
  }

  .site-nav {
    gap: 0.3rem;
  }

  .site-nav a {
    padding: 0.4rem 0.55rem;
    font-size: 0.95rem;
  }

  .detay-karti {
    padding: 0.7rem;
  }

  .afis-gorsel {
    max-height: 360px;
  }
}

```

## `frontend/public/afis.svg`

```xml
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 720 960" role="img" aria-labelledby="title desc">
  <title id="title">Kariyer Günleri 2026 afişi</title>
  <desc id="desc">Koyu lacivert zemin üzerinde Kariyer Günleri 2026 yazan kampüs etkinliği afişi.</desc>
  <rect width="720" height="960" fill="#10233c"/>
  <rect x="26" y="26" width="668" height="908" rx="14" fill="none" stroke="#d39b7f" stroke-width="5"/>
  <rect x="39" y="39" width="642" height="882" rx="10" fill="none" stroke="#2f4a68" stroke-width="9"/>
  <circle cx="360" cy="260" r="72" fill="#159447" opacity="0.95"/>
  <path d="M330 262l24 24 43-53" fill="none" stroke="#ffffff" stroke-width="16" stroke-linecap="round" stroke-linejoin="round"/>
  <text x="360" y="430" fill="#ffffff" text-anchor="middle" font-family="Arial, Helvetica, sans-serif" font-size="58" font-weight="700">Kariyer Günleri</text>
  <text x="360" y="505" fill="#d39b7f" text-anchor="middle" font-family="Arial, Helvetica, sans-serif" font-size="52" font-weight="700">2026</text>
  <line x1="170" y1="575" x2="550" y2="575" stroke="#159447" stroke-width="5"/>
  <text x="360" y="650" fill="#ffffff" text-anchor="middle" font-family="Arial, Helvetica, sans-serif" font-size="28">12 Ekim 2026 · 14:00</text>
  <text x="360" y="704" fill="#cbd7e4" text-anchor="middle" font-family="Arial, Helvetica, sans-serif" font-size="25">A Blok Konferans Salonu</text>
  <text x="360" y="840" fill="#8fa5bc" text-anchor="middle" font-family="Arial, Helvetica, sans-serif" font-size="20">KAMPÜS ETKİNLİKLERİ</text>
</svg>

```

## `frontend/README.md`

```markdown
# Kampüs Etkinlikleri - Sprint 4

Repository kökündeki `README.md` teslim ve çalıştırma yönergelerini içerir.

```bash
npm install
npm run dev
npm run build
npm run preview
```

```
