# autohenc.nl

Onafhankelijk informatieplatform over auto importeren uit Duitsland.
Statische site, gegenereerd met een klein Python-script. Geen build-stap nodig
om live te gaan: de map `public/` is de complete, deploybare website.

## Structuur

```
build.py     Generator: config, CSS, templates, header/footer
content.py   Alle inhoud: pagina's en artikelen (pas hier teksten aan)
public/      Gegenereerde site (dit is wat live gaat)
```

## Aanpassen en opnieuw genereren

Teksten en artikelen staan in `content.py`. Een nieuw artikel toevoegen: voeg
een dict toe aan de lijst `ARTICLES`. Daarna opnieuw bouwen:

```bash
python3 build.py
```

De map `public/` wordt dan opnieuw aangemaakt.

## Live zetten via GitHub + Cloudflare Pages

1. Maak een GitHub-repo en push deze map (inclusief `public/`).
2. Cloudflare dashboard, Workers & Pages, Create application, Pages, Connect to Git.
3. Kies de repo en stel in:
   - **Framework preset:** None
   - **Build command:** leeg laten
   - **Build output directory:** `public`
4. Deploy. Cloudflare serveert de inhoud van `public/` rechtstreeks.
5. Bij Custom domains: voeg `autohenc.nl` (en `www.autohenc.nl`) toe en volg de
   DNS-stappen. HTTPS regelt Cloudflare automatisch.

Cloudflare Pages serveert `/over.html` ook op `/over`. De interne links in de
site gebruiken die nette URL's zonder `.html`.

## Wat erin zit

- Home, Over, Nieuws (overzicht), 6 artikelen, Partners, Contact
- Veelgestelde vragen, Privacybeleid, Cookiebeleid, 404-pagina
- `sitemap.xml`, `robots.txt`, `favicon.svg`
- `_headers` met basis security-headers en caching
- JSON-LD structured data (Organization, WebSite, Article, BreadcrumbList, FAQPage)

Contact loopt via een mailto naar `info@autohenc.nl`. Er is bewust geen
contactformulier.
