# Lokalūs paleidimo žingsniai (LT)

## 0) Viena komanda (rekomenduojama)

```bash
make setup-local
```

Komanda automatiškai pasirenka Docker (jei yra) arba native režimą.

Galite paleisti konkrečiu režimu:

```bash
bin/setup-local --mode docker
bin/setup-local --mode native
```

## 1) Paleidimas per Docker (rekomenduojama)

```bash
cp compose.override.dist.yml compose.override.yml
cp .env .env.local
make init
```

Atidarykite:
- Parduotuvė: http://localhost
- Administravimas: http://localhost/admin
- El. laiškų peržiūra (MailHog): http://localhost:8025

Naudingos komandos:

```bash
make up
make down
make clean
make doctor
make setup-local
```

> Jei `80` portas užimtas, pakeiskite `compose.override.yml` Nginx port mapinimą (pvz. į `8080:80`) ir atidarykite `http://localhost:8080`.

## 2) Paleidimas be Docker

Reikia: PHP 8.2+, Composer, Node.js 18+, Yarn, MySQL/MariaDB, Symfony CLI.

```bash
cp .env .env.local
composer install
yarn install
yarn build
php bin/console sylius:install -s default -n
symfony server:start -d
```

Tada atidarykite: http://127.0.0.1:8000

## 3) Greitas patikrinimas

```bash
make doctor
make setup-local
```

Ši komanda parodo, ar turite pagrindinius įrankius (`php`, `composer`, `yarn`, `docker`, `symfony`) ir ar sugeneruoti reikalingi failai (`vendor/`, `public/build/manifest.json`).

Jei norite tik pamatyti ką darys setup komanda (be vykdymo), naudokite `bin/setup-local --dry-run`.

## 4) Dažniausios problemos

- Jei nepasileidžia `bin/console`, dažniausiai trūksta `vendor/` priklausomybių (`composer install`).
- Jei neįvyksta migracijos/instaliacija, patikrinkite DB prisijungimą `.env.local` faile.
- Jei nėra stilių/JS, paleiskite `yarn build` dar kartą.
