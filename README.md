# 🚀 Student Onboarding - Programmering 1

👋 Välkommen till GitHub på JENSEN komvux!  
Den här guiden är för helt nybörjare på Windows (WSL) och macOS/Linux.

## 🚀 Vad är GitHub?

GitHub är en webbaserad plattform för versionshantering och samarbete kring kod. Det används av både nybörjare och professionella utvecklare över hela världen. Här är några viktiga aspekter:

- **En plats för att lagra kod och filer**  
  GitHub fungerar som ett säkert digitalt arkiv där du kan lagra alla dina projektfiler. Alla ändringar sparas historiskt, så du kan alltid gå tillbaka till tidigare versioner av din kod.

- **Versionskontroll med Git**  
  GitHub bygger på Git, ett system för versionshantering. Det innebär att du kan:
  - Spåra ändringar i filer över tid  
  - Arbeta med flera versioner av samma projekt samtidigt  
  - Sammanfoga ändringar från olika personer utan att tappa information

- **Samarbete med lärare och klasskamrater**  
  GitHub gör det möjligt att samarbeta i realtid. Du kan:
  - Dela kod med andra  
  - Granska och kommentera varandras arbete  
  - Arbeta i team med tydliga ansvarsområden genom “branches” och “pull requests”

- **GitHub Classroom: inlämning och automatiserad rättning**  
  Med GitHub Classroom får du en personlig arbetsyta för varje uppgift:
  - Läraren skapar uppgifter som automatiskt genererar repositories för varje student  
  - Du lämnar in kod via Git, och automaträttning kan kontrollera att koden fungerar som förväntat  
  - Du får direkt feedback och poäng, vilket gör det enklare att följa din egen utveckling  

- **Extra fördelar**  
  - Du kan visa upp dina projekt som en portfolio för framtida arbetsgivare  
  - GitHub stöder integrationer med många verktyg, t.ex. VS Code, CI/CD-pipelines, och projektplaneringsverktyg  

> 💡 Kort sagt: GitHub är både en plats för att lagra din kod och ett verktyg som lär dig professionella arbetsflöden för programmering och samarbete.

## 🧰 Vad du behöver
- Ett GitHub-konto — [Registrera dig](https://github.com/join)
- E-postadress
- Windows-användare: en PC med WSL installerat
- macOS/Linux-användare: Terminal (t.ex. iTerm2 eller standardskal)
- En SSH-nyckel för säkra Git-operationer

## ⚙️ Windows-installation: Installera WSL + Ubuntu

### 1. Öppna PowerShell som administratör
- Tryck på Windows-tangenten, skriv `PowerShell`
- Högerklicka på **Windows PowerShell**, välj **Kör som administratör**

### 2. Aktivera nödvändiga Windows-funktioner
```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

### 3. Starta om datorn
Kör om datorn manuellt innan du fortsätter.

### 4. Installera Ubuntu via WSL
```powershell
wsl --install -d Ubuntu
```

### 5. Skapa din UNIX-användare
När Ubuntu startar första gången, följ anvisningarna:
- Välj ett användarnamn (t.ex. `tomhanks1337`)
- Ange ett lösenord (det syns inte medan du skriver)

## 🔧 Ubuntu/WSL eller macOS/Linux: Installera Git & konfigurera SSH

### 1. Uppdatera systempaket
```bash
sudo apt update && sudo apt upgrade -y    # Ubuntu/WSL
# macOS: brew update
```

### 2. Installera Git
```bash
sudo apt install git -y                   # Ubuntu/WSL
# macOS: brew install git
```

### 3. Konfigurera Git
```bash
git config --global user.name "Ditt Namn"
git config --global user.email "din.email@exempel.com"
```

### 4. Skapa en SSH-nyckel
```bash
ssh-keygen -t rsa -b 4096 -f ~/.ssh/jensen
```

### 5. Starta SSH-agenten & lägg till nyckeln
```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/jensen
```

### 6. Kopiera din publika nyckel
```bash
cat ~/.ssh/jensen.pub
```

### 7. Lägg till SSH-nyckeln i GitHub
- I GitHub: **Settings → SSH and GPG keys → New SSH key**  
- Titel: `WSL Ubuntu eller macOS SSH`  
- Nyckel: klistra in den kopierade publika nyckeln  
- Klicka på **Add SSH key**

### 8. (Valfritt) Skapa en SSH-konfigfil
```bash
cat <<EOF >> ~/.ssh/config
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/jensen
EOF
```

### 9. Testa SSH-anslutningen
```bash
ssh -T git@github.com
```

## 📋 Inlämningsregler för GitHub Classroom

### ✅ Godkänt sätt att lämna in
- Acceptera uppgiften via GitHub Classroom-länken från läraren  
- Arbeta i ditt tilldelade personliga repository som skapas automatiskt  
- Använd de förberedda filerna i `assignments/`-mappen

### ❌ Ej godkänt sätt
- Skapa egna repositories manuellt  
- Skapa repositories i organisationer  
- Ändra repository-namn  
- Lämna in kod via email eller andra plattformar

### ⚠️ Viktigt att veta
- Endast kod som lämnas in via Classroom kommer att rättas automatiskt  
- Automaträttningen fungerar bara i Classroom-skapta repositories  
- Du ser dina poäng direkt efter varje inlämning i GitHub Classroom

## 📦 Kom igång: Klona & Lämna in

### 1. Gå med i ett Klassrum
- Läraren delar en inbjudningslänk  
- Klicka på länken, logga in och acceptera uppgiften

### 2. Klona ditt uppgiftsrepo
```bash
git clone git@github.com:<organisation>/<repository-namn>.git
```

### 3. Gör ditt arbete
```bash
cd programmering-1-dittanvändarnamn
# Redigera filer i assignments/ mappen...
git add .
git commit -m "Lösning på uppgift 1"
git push origin main
```

### 4. Kontrollera dina poäng
- Gå tillbaka till GitHub Classroom  
- Se dina poäng och vilka tester som passerat

## 🎯 Checklista för lyckad inlämning
- SSH-nyckel konfigurerad och testad  
- Git konfigurerat med namn och e-post  
- Uppgift accepterad via Classroom-länken  
- Arbetar i Classroom-skapat repository  
- Repository-namnet börjar med `<klassnamn>-<kurs>-ditt-<användarnamn>`, exempelvis: `nstd_aug_23-programmering-1-fa1c0nx`
- Fyller i koden i filerna under `assignments/`  
- Använder `git add`, `commit` och `push` regelbundet  
- Ser poäng i GitHub Classroom efter varje push

## 💡 Tips
- Committa och pusha ofta – hellre flera små commits än stora  
- Använd tydliga commit-meddelanden – beskriv vad du gjort  
- Öppna Issues vid frågor eller oklarheter  
- Testa din kod innan du lämnar in

## 📞 Support
- Tekniska problem med installation: Följ denna guide eller kontakta läraren  
- Problem med Classroom: Kontrollera att du använder rätt repository  
- Kodhjälp: Använd kommentarer i koden och fråga på lektionerna

Lycka till och ha kul med kodandet! 🎉

<sub>Senast uppdaterad: 2025.10.31 • Mohammed Mansourson @ JENSEN education</sub>
