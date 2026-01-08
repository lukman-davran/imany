# Uputstvo za Deployment na GitHub i Netlify

## Korak 1: Postavi Git konfiguraciju

Otvorite PowerShell ili Command Prompt u folderu projekta i izvršite:

```bash
git config --global user.name "Tvoje Ime"
git config --global user.email "tvoj@email.com"
```

## Korak 2: Kreiraj GitHub Repository

1. Idite na [GitHub.com](https://github.com) i ulogujte se
2. Kliknite na **"+"** u gornjem desnom uglu i izaberite **"New repository"**
3. Unesite naziv repozitorija (npr. `moj-sajt` ili `posebna-poruka`)
4. Ostavite ga kao **Public** (ili Private ako želite)
5. **NE** kreirajte README, .gitignore ili license (već ih imamo)
6. Kliknite **"Create repository"**

## Korak 3: Poveži lokalni projekat sa GitHub-om

U PowerShell-u u folderu projekta izvršite:

```bash
# Dodaj sve fajlove
git add .

# Kreiraj prvi commit
git commit -m "Initial commit - Personalizovana web stranica"

# Dodaj GitHub remote (zamijenite YOUR_USERNAME i YOUR_REPO_NAME)
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git

# Promijeni naziv glavne grane u main (ako je potrebno)
git branch -M main

# Pošalji kod na GitHub
git push -u origin main
```

**Napomena:** Zamijenite `YOUR_USERNAME` i `YOUR_REPO_NAME` sa vašim GitHub korisničkim imenom i nazivom repozitorija.

## Korak 4: Postavi na Netlify

### Opcija A: Kroz Netlify Dashboard

1. Idite na [Netlify.com](https://www.netlify.com) i ulogujte se (možete se ulogovati sa GitHub account-om)
2. Kliknite na **"Add new site"** → **"Import an existing project"**
3. Izaberite **"Deploy with GitHub"**
4. Autorizujte Netlify da pristupa vašem GitHub account-u
5. Izaberite vaš repozitorij (`YOUR_REPO_NAME`)
6. Netlify će automatski detektovati postavke:
   - **Build command:** (ostavite prazno)
   - **Publish directory:** (ostavite prazno ili stavite `/`)
7. Kliknite **"Deploy site"**

### Opcija B: Drag & Drop

1. Idite na [Netlify.com](https://www.netlify.com)
2. Povucite i spustite folder `Moj_sajt` na Netlify dashboard
3. Sajt će se automatski deploy-ovati

## Korak 5: Provjeri da sve radi

1. Nakon deployment-a, Netlify će vam dati URL (npr. `https://random-name-123.netlify.app`)
2. Otvorite URL i provjerite da:
   - Stranica se učitava
   - Slika se prikazuje
   - Svi tekstovi su vidljivi
   - Dizajn izgleda dobro

## Korak 6: Custom Domain (Opciono)

Ako želite koristiti vlastiti domen:
1. U Netlify dashboard-u, idite na **"Site settings"** → **"Domain management"**
2. Kliknite **"Add custom domain"**
3. Unesite vaš domen i pratite uputstva

## Važne Napomene

- ✅ Sve putanje su već prilagođene za hosting (koriste relativne putanje)
- ✅ Slika mora biti u folderu `images/` sa nazivom `background.jpg.jpg`
- ✅ Svaki put kada promijenite kod, commit-ujte i push-ujte na GitHub, i Netlify će automatski redeploy-ovati sajt

## Troubleshooting

**Problem: Slika se ne prikazuje na Netlify**
- Provjerite da li je slika u folderu `images/` i da li je commit-ovana na GitHub
- Provjerite da li je naziv fajla tačan: `background.jpg.jpg`

**Problem: Stranica se ne učitava**
- Provjerite Console u Developer Tools (F12) za greške
- Provjerite da li je `index.html` u root folderu repozitorija

**Problem: Git push ne radi**
- Provjerite da li ste pravilno postavili remote URL
- Provjerite da li imate prava na repozitorij

