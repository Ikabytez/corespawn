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

Repozytorium: [github.com/Ikabytez/corespawn](https://github.com/Ikabytez/corespawn).

W przyszłości nowe zmiany wypchniesz z katalogu projektu:

```bash
git add -A
git commit -m "Opis zmian"
git push
```

Do pierwszego klonowania i wdrożenia na VPS przejdź do [instrukcji wdrożenia](./deploy/README.md).

## Wdrożenie na VPS

Instrukcja instalacji na Ubuntu/Debian z Nginx i SSL Let's Encrypt znajduje się w [deploy/README.md](./deploy/README.md). Konfiguracja Nginx jest w [deploy/nginx/corespawn.pl.conf](./deploy/nginx/corespawn.pl.conf).
