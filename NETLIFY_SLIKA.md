# Kako dodati sliku na Netlify

## Problem
Slika se ne prikazuje na Netlify jer nije uploadovana na GitHub.

## Rješenje - Korak po korak:

### 1. Postavi Git konfiguraciju (ako već nisi)

Otvorite PowerShell u folderu projekta i izvršite:

```bash
git config --global user.name "Tvoje Ime"
git config --global user.email "tvoj@email.com"
```

**Napomena:** Koristi isti email koji koristiš za GitHub!

### 2. Provjeri da li je slika u folderu

Provjeri da li postoji fajl: `images/background.jpg.jpg`

### 3. Dodaj sve fajlove u Git

```bash
git add .
```

### 4. Kreiraj commit

```bash
git commit -m "Add website with background image"
```

### 5. Ako još nemaš GitHub repository:

#### 5a. Kreiraj GitHub Repository:
1. Idi na [github.com](https://github.com)
2. Klikni **"+"** → **"New repository"**
3. Unesi naziv (npr. `moj-sajt`)
4. Ostavi **Public**
5. **NE** kreiraj README, .gitignore ili license
6. Klikni **"Create repository"**

#### 5b. Poveži lokalni projekat sa GitHub-om:

```bash
# Zamijeni YOUR_USERNAME i YOUR_REPO_NAME sa svojim podacima
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
git branch -M main
git push -u origin main
```

### 6. Ako već imaš GitHub repository:

```bash
# Provjeri remote
git remote -v

# Ako nema remote, dodaj ga:
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git

# Push-uj sve na GitHub
git branch -M main
git push -u origin main
```

### 7. Na Netlify:

1. Idi na [app.netlify.com](https://app.netlify.com)
2. Ako već imaš sajt:
   - Klikni na svoj sajt
   - Idi na **"Deploys"** tab
   - Klikni **"Trigger deploy"** → **"Clear cache and deploy site"**
   
3. Ako nemaš sajt:
   - **"Add new site"** → **"Import an existing project"**
   - Izaberi **"Deploy with GitHub"**
   - Autorizuj Netlify
   - Izaberi svoj repozitorij
   - Klikni **"Deploy site"**

### 8. Provjeri da li radi:

- Otvori svoj Netlify URL
- Provjeri da li se slika prikazuje
- Ako ne, provjeri Console (F12) za greške

## Važno:

✅ **Slika MORA biti commit-ovana na GitHub** - Netlify uzima fajlove direktno sa GitHub-a
✅ **Provjeri da li je slika u folderu `images/` sa nazivom `background.jpg.jpg`**
✅ **Nakon svake izmjene, commit-uj i push-uj na GitHub**

## Troubleshooting:

**Problem: Slika se i dalje ne prikazuje**
- Provjeri da li je slika commit-ovana: `git log --all --full-history -- images/background.jpg.jpg`
- Provjeri da li je push-ovana: Idi na GitHub i provjeri da li vidiš `images/background.jpg.jpg` u repozitoriju
- Provjeri putanju u `index.html`: Treba biti `images/background.jpg.jpg` (bez `./`)

**Problem: Git push ne radi**
- Provjeri da li si pravilno postavio remote: `git remote -v`
- Provjeri da li imaš prava na repozitorij
- Možda treba autentifikacija (GitHub token ili SSH)

