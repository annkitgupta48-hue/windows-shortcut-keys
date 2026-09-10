# Git और GitHub Learning Notes

यह file इस project को local computer से GitHub पर publish करने की पूरी प्रक्रिया का reference है।

Repository: https://github.com/annkitgupta48-hue/windows-shortcut-keys

## 0. Git और GitHub क्या है?

- Git: local machine पर file versions और history maintain करने वाला version control system है।
- GitHub: Internet पर Git repositories को store और share करने वाला platform है।
- Local repository: आपका computer में `.git` के साथ folder।
- Remote repository: GitHub पर बना repository।
- Branch: project की अलग अलग version line।
- Commit: एक snapshot/save point।

## 1. Project folder में जाना

```powershell
cd "C:\Users\Ankit\Desktop\3rd live working\shortcut keys"
```

**क्या करता है:** PowerShell का current folder project folder में बदलता है।

**क्यों इस्तेमाल करते हैं:** Git commands सही project पर चलें, इसके लिए पहले उसी folder में होना ज़रूरी है।

---

## 2. Repository initialize करना

```powershell
git init
```

**क्या करता है:** Current folder को Git repository बनाता है और hidden `.git` folder बनाता है।

**क्यों इस्तेमाल करते हैं:** Git इसी `.git` folder में commit history, branches और tracking information रखता है।

**Important point:** यह command local repository शुरू करता है, GitHub से connection नहीं बनाता।

---

## 3. Files की current status देखना

```powershell
git status
```

**क्या करता है:** बताता है कि कौन-सी files new हैं, modified हैं, staged हैं या untracked हैं।

**क्यों इस्तेमाल करते हैं:** Commit करने से पहले kita verify करते हैं कि सही files include हो रही हैं।

**Example output का meaning:**
- `?? file-name`: file Git tracking में नहीं है।
- `M file-name`: file modified है।
- `A file-name`: file staged है।

---

## 4. Git identity configure करना

```powershell
git config --global user.name "Ankit"
git config --global user.email "your-github-email@example.com"
```

**क्या करता है:** Git commit के author name और email set करता है।

**क्यों इस्तेमाल करते हैं:** Commit records में पता चलता है कि commit किसने किया।

**Check करने के लिए:**

```powershell
git config --global user.name
git config --global user.email
```

**Important:** अगर identity not set होती है, तो commit fail हो सकता है या commit author missing दिख सकता है।

---

## 5. Files को staging area में रखना

```powershell
git add .
```

**क्या करता है:** Current folder की सभी new/modified files को staging area में डालता है।

**क्यों इस्तेमाल करते हैं:** Git commit से पहले files को stage करके तैयार करता है।

**Concept:**
- Working directory = file edit करना
- Staging area = commit करने के लिए ready files
- Commit = final save point

**Single file add करने का example:**

```powershell
git add Windows_Shortcut_Keys.html
```

**अगर सिर्फ certain file add करना हो:**

```powershell
git add Git_Learning_Notes.md
```

---

## 6. Local commit बनाना

```powershell
git commit -m "Add Windows shortcut keys reference"
```

**क्या करता है:** Staged files का एक snapshot/local save point बनाता है।

**क्यों इस्तेमाल करते हैं:** project की history बनती है और किसी point पर वापस लौट सकते हैं।

**Important:**
- `-m` commit message देता है
- commit message clear और short होना चाहिए
- commit एक specific change snapshot है

**Good examples:**

```powershell
git commit -m "Initial project setup"
git commit -m "Add shortcut dashboard UI"
git commit -m "Update git notes"
```

---

## 7. Remote repository को local project से connect करना

```powershell
git remote add origin https://github.com/annkitgupta48-hue/windows-shortcut-keys.git
```

**क्या करता है:** GitHub repository का address `origin` नाम से local Git में save करता है।

**क्यों इस्तेमाल करते हैं:** Local commits को सही remote repo पर push करने के लिए।

**Check करने के लिए:**

```powershell
git remote -v
```

**Meaning:**
- `origin` = remote repository का short name
- `fetch` = GitHub से pull/later download
- `push` = local to GitHub upload

---

## 8. Branch rename करना: master से main

```powershell
git branch -M main
```

**क्या करता है:** Current branch का नाम `master` से `main` में बदल देता है।

**क्यों इस्तेमाल करते हैं:** आधुनिक Git/GitHub default convention `main` है।

**Why this matters:**
- Old Git versions default branch `master` नाम से बनता था
- कई repositories में main का use modern standard है
- यह command local branch name को rename करता है, safe way से

**Branch check करने के लिए:**

```powershell
git branch
```

**Branch meaning:**
- `main` = current main branch
- `master` = old conventional name

---

## 9. GitHub पर first push करना

```powershell
git push -u origin main
```

**क्या करता है:** Local `main` branch के commits को GitHub repository पर upload करता है।

**`-u` का meaning:**
- `--set-upstream`
- local branch को remote branch से connect करता है
- अब आगे केवल `git push` भी काम करेगा

**Why important:**
- One-time setup for tracking
- future `git push` without writing branch name again

**After this, future push command:**

```powershell
git push
```

---

## 10. Full command sequence jo humne actual project ke liye chalaya

Ye sequence project setup और push workflow का actual flow है:

```powershell
cd "C:\Users\Ankit\Desktop\3rd live working\shortcut keys"
git init
git status
git config --global user.name "Ankit"
git config --global user.email "your-github-email@example.com"
git add .
git status
git commit -m "Add Windows shortcut keys reference"
git remote add origin https://github.com/annkitgupta48-hue/windows-shortcut-keys.git
git remote -v
git branch
git branch -M main
git push -u origin main
git status
```

### Each command ka quick meaning

- `cd ...`: project folder में enter
- `git init`: local repo create
- `git status`: check pending files
- `git config --global ...`: identity set
- `git add .`: files stage
- `git commit -m ...`: local save point
- `git remote add origin ...`: GitHub address connect
- `git branch -M main`: rename branch to main
- `git push -u origin main`: upload and set upstream
- `git status`: confirm repo clean/tracking

---

## 11. master aur main naming ki confusion samajhna

Ye important point hai ki local aur GitHub side par naming same nahi ho sakta.

### Example:

- Local machine: branch name `main`
- GitHub repo: default branch could still be `master` depending on repo settings or older repo history
- `git branch -M main` local ko rename karta hai, but remote branch default name ko automatically change नहीं करता

### Simple explanation:

- `git branch -M main` = local branch rename
- `git push -u origin main` = local `main` ko GitHub `origin` remote के `main` branch से link karna
- Agar GitHub par remote branch `master` default hai, to either you manually rename it on GitHub or push to new `main` branch

**Aage ka command example:**

```powershell
git checkout -b main
```

**If GitHub still uses old master branch:**

```powershell
git push -u origin HEAD:master
```

**But in this project we used:**

```powershell
git branch -M main
git push -u origin main
```

This means we made local branch `main` and linked it to remote `main` branch.

---

## 12. Future में changes publish करने का standard workflow

जब HTML, TXT, CSS, README, etc. में change hoga, toh ye sequence follow karna:

```powershell
git status
git add .
git commit -m "Describe your change"
git push
```

### हर command का short explanation

- `git status`: current changes check karta hai
- `git add .`: all modified files ready for commit
- `git commit -m "..."`: new snapshot create karta hai
- `git push`: GitHub par latest changes upload karta hai

---

## 13. Useful Git commands

### 1. Recent commit history check

```powershell
git log --oneline
```

**Kya karta hai:** recent commits ko compact form me show karta hai.

### 2. Last commit details dekhna

```powershell
git show
```

**Kya karta hai:** latest commit me kya change hua, show karta hai.

### 3. Difference check

```powershell
git diff
```

**Kya karta hai:** unstaged changes ko compare karta hai.

```powershell
git diff --staged
```

**Kya karta hai:** staged changes ka difference show karta hai.

### 4. Remote check

```powershell
git remote -v
```

**Kya karta hai:** GitHub remote URL show karta hai.

### 5. Current branch check

```powershell
git branch
```

**Kya karta hai:** current branch aur available branches show karta hai.

---

## 14. Important beginner tips

- `git add .` se pehle `git status` zarur check karna chahiye.
- Commit message short and clear rakho.
- Agar koi file Git me upload nahi karni, to `.gitignore` file use karo.
- `git push` ke baad GitHub repository open karke verify karo.
- Password ya token ko file/chat me save mat rakho.
- Git branch naming ko follow karo: `main` modern standard hai.

---

## 15. This project ke current files

- `Windows_Shortcut_Keys.html` - Search + category filters वाला visual shortcut dashboard
- `Windows_Shortcut_Keys.txt` - Plain text shortcut reference
- `Git_Learning_Notes.md` - Git/GitHub commands aur explanations

---

## 16. Final summary

Project ko GitHub par publish karne ke liye humne step by step ye process follow kiya:

1. `git init` - repo initialize
2. `git status` - check files
3. `git config ...` - author details set
4. `git add .` - stage files
5. `git commit -m ...` - local save point create
6. `git remote add origin ...` - GitHub link
7. `git branch -M main` - local branch rename
8. `git push -u origin main` - GitHub par upload
9. `git status` - verify final state

Ye sequence future me bhi kisi bhi project ke liye work karta hai, especially when you are learning Git and publishing your work online.

