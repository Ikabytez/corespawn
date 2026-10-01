# Corespawn.pl

Responsywna strona landing page Corespawn zbudowana w Vue 3, Inertia.js i Vite.

## Uruchomienie lokalne

Wymagany Node.js 20 lub nowszy.

```bash
npm ci
npm run dev
```

Otwórz adres pokazany przez Vite (zwykle `http://localhost:5173`).

## Build produkcyjny

```bash
npm run build
```

Gotowe pliki statyczne znajdują się w `dist/`.

## Publikacja na GitHub

Utwórz puste repozytorium `corespawn` na swoim koncie GitHub (bez automatycznie dodawanego README). W katalogu projektu ustaw autora pierwszego commita i wypchnij kod:

```bash
git config user.name "Twoje imię"
git config user.email "Adres e-mail powiązany z GitHub"
git commit -m "Initial Corespawn website"
git remote add origin https://github.com/TWOJ_LOGIN/corespawn.git
git push -u origin main
```

GitHub poprosi o autoryzację. Nie wpisuj tokenu jako części adresu repozytorium.

## Wdrożenie na VPS

Instrukcja instalacji na Ubuntu/Debian z Nginx i SSL Let's Encrypt znajduje się w [deploy/README.md](./deploy/README.md). Konfiguracja Nginx jest w [deploy/nginx/corespawn.pl.conf](./deploy/nginx/corespawn.pl.conf).
