# Wdrożenie Corespawn na VPS (Nginx + Let's Encrypt)

Konfiguracja zakłada Ubuntu/Debian, domenę `corespawn.pl` oraz katalog `/var/www/corespawn`. Strona jest frontendem statycznym: na VPS-ie budujesz pliki Vue/Vite, a Nginx serwuje zawartość `dist/`. Nie jest potrzebny osobny Node.js server ani PHP/Inertia backend. Jeśli używasz innej domeny, zmień `server_name` i ścieżki certyfikatu w [konfiguracji Nginx](./nginx/corespawn.pl.conf).

## 1. Skieruj domenę na VPS

W DNS ustaw rekordy `A` dla `corespawn.pl` i `www.corespawn.pl` na publiczny adres IPv4 serwera. Jeśli dodajesz rekordy `AAAA`, muszą wskazywać działający adres IPv6 VPS-a. Upewnij się, że porty 80 i 443 są otwarte w firewallu VPS-a i u dostawcy.

## 2. Zainstaluj wymagane pakiety

```bash
sudo apt update
sudo apt install nginx certbot git
```

Zainstaluj Node.js 20 lub nowszy zgodnie z instrukcją dla swojej dystrybucji z [nodejs.org](https://nodejs.org/). Sprawdź wersje:

```bash
node --version
npm --version
```

## 3. Pobierz projekt i zbuduj stronę na VPS

```bash
sudo git clone ADRES_REPOZYTORIUM_GITHUB /var/www/corespawn
sudo chown -R "$USER":"$USER" /var/www/corespawn
cd /var/www/corespawn
npm ci
npm run build
```

Zastąp `ADRES_REPOZYTORIUM_GITHUB` adresem repozytorium, np. `https://github.com/TWOJ_LOGIN/corespawn.git`. Jeżeli repozytorium jest prywatne, skonfiguruj uwierzytelnienie Git na VPS-ie przed klonowaniem; nie umieszczaj tokenu w adresie repozytorium.

Po zbudowaniu ustaw właściciela plików dla Nginx:

```bash
sudo chown -R www-data:www-data /var/www/corespawn/dist
```

## 4. Włącz tymczasową konfigurację HTTP

Certyfikat trzeba uzyskać, zanim Nginx będzie mógł załadować konfigurację HTTPS. Utwórz tymczasowy plik:

```bash
sudo tee /etc/nginx/sites-available/corespawn >/dev/null <<'EOF'
server {
    listen 80;
    listen [::]:80;
    server_name corespawn.pl www.corespawn.pl;
    root /var/www/corespawn/dist;

    location ^~ /.well-known/acme-challenge/ {
        try_files $uri =404;
    }

    location / {
        try_files $uri $uri/ /index.html;
    }
}
EOF
```

Włącz stronę i przeładuj Nginx:

```bash
sudo ln -s /etc/nginx/sites-available/corespawn /etc/nginx/sites-enabled/corespawn
sudo nginx -t
sudo systemctl reload nginx
```

Jeśli symlink już istnieje, pomiń `ln -s`.

## 5. Uzyskaj certyfikat SSL

```bash
sudo certbot certonly --webroot \
  -w /var/www/corespawn/dist \
  -d corespawn.pl \
  -d www.corespawn.pl
```

Podczas uzyskiwania certyfikatu oba adresy DNS muszą już wskazywać na VPS, a port 80 musi być dostępny z internetu.

## 6. Włącz docelową konfigurację HTTPS

Skopiuj docelową konfigurację na miejsce:

```bash
sudo cp /var/www/corespawn/deploy/nginx/corespawn.pl.conf /etc/nginx/sites-available/corespawn
```

Sprawdź konfigurację i przeładuj Nginx:

```bash
sudo nginx -t
sudo systemctl reload nginx
```

Certbot zwykle instaluje zadanie automatycznego odnawiania certyfikatu. Sprawdź je poleceniem:

```bash
sudo certbot renew --dry-run
```

Po wdrożeniu strona powinna być dostępna pod `https://corespawn.pl`.

## Aktualizacja strony

Po wypchnięciu zmian do gałęzi `main` na VPS-ie wykonaj:

```bash
cd /var/www/corespawn
git pull --ff-only
npm ci
npm run build
sudo chown -R www-data:www-data /var/www/corespawn/dist
```

Nginx serwuje nowe pliki bez restartu usługi.
