# Git और GitHub Learning Notes

यह file इस project को local computer से GitHub पर publish करने की पूरी प्रक्रिया का reference है।

Repository: https://github.com/annkitgupta48-hue/windows-shortcut-keys

## 1. Project folder में जाना

```powershell
cd "C:\Users\Ankit\Desktop\3rd live working\shortcut keys"
```

**क्या करता है:** PowerShell का current folder project folder में बदलता है।

**क्यों इस्तेमाल करते हैं:** Git commands सही project पर चलें, इसके लिए पहले उसी folder में होना ज़रूरी है।

## 2. Local Git repository बनाना

```powershell
git init
```

**क्या करता है:** Current folder को Git repository बनाता है और hidden `.git` folder बनाता है।

**क्यों इस्तेमाल करते हैं:** Git इसी `.git` folder में commits और version history रखता है।

## 3. Files की स्थिति देखना

```powershell
git status
```

**क्या करता है:** बताता है कि कौन-सी files नई, बदली हुई, staged या committed हैं।

**क्यों इस्तेमाल करते हैं:** Commit करने से पहले verify करने के लिए कि सही files शामिल हो रही हैं।

## 4. Files को staging area में रखना

```powershell
git add .
```

**क्या करता है:** Current folder की नई और बदली हुई सभी files को अगले commit के लिए तैयार करता है।

**क्यों इस्तेमाल करते हैं:** Git पहले files को staging area में रखता है, फिर उनका commit बनता है।

**सिर्फ एक file add करने के लिए:**

```powershell
git add Windows_Shortcut_Keys.html
```

## 5. Local commit बनाना

```powershell
git commit -m "Add Windows shortcut keys reference"
```

**क्या करता है:** Staged files का एक local version snapshot बनाता है।

**क्यों इस्तेमाल करते हैं:** Commit एक save point होता है, जिससे बाद में history देख या पुराना version restore कर सकते हैं।

**अच्छा commit message:** छोटा, स्पष्ट और किए गए बदलाव को बताने वाला होना चाहिए।

## 6. Git author identity set करना

```powershell
git config --global user.name "Ankit"
git config --global user.email "your-github-email@example.com"
```

**क्या करता है:** Git commits में author का नाम और email set करता है।

**क्यों इस्तेमाल करते हैं:** Git को पता चलता है कि commit किसने बनाया है।

**अपनी identity check करने के लिए:**

```powershell
git config --global user.name
git config --global user.email
```

## 7. GitHub repository को local project से connect करना

```powershell
git remote add origin https://github.com/annkitgupta48-hue/windows-shortcut-keys.git
```

**क्या करता है:** GitHub repository का address `origin` नाम से save करता है।

**क्यों इस्तेमाल करते हैं:** Local commits को सही GitHub repository पर भेजने के लिए।

**Remote check करने के लिए:**

```powershell
git remote -v
```

## 8. Branch का नाम `main` करना

```powershell
git branch -M main
```

**क्या करता है:** Current branch का नाम `master` से `main` करता है।

**क्यों इस्तेमाल करते हैं:** GitHub की standard default branch आमतौर पर `main` होती है।

**Current branch check करने के लिए:**

```powershell
git branch
```

## 9. GitHub पर पहली बार push करना

```powershell
git push -u origin main
```

**क्या करता है:** Local `main` branch और उसका commit GitHub पर upload करता है।

**`-u` क्यों इस्तेमाल करते हैं:** Local `main` को remote `origin/main` से जोड़ता है। इसके बाद सामान्यतः सिर्फ `git push` चलाना काफी होता है।

## 10. Future में बदलाव publish करने का workflow

जब HTML या TXT file में कोई बदलाव करें, ये commands क्रम से चलाएँ:

```powershell
git status
git add .
git commit -m "Describe your changes"
git push
```

### हर command का छोटा अर्थ

- `git status`: बदलाव check करता है।
- `git add .`: बदलाव को अगली save point में शामिल करने के लिए तैयार करता है।
- `git commit -m "..."`: local history में नया save point बनाता है।
- `git push`: नया commit GitHub पर upload करता है।

## 11. Useful history commands

```powershell
git log --oneline
```

Recent commits की compact list दिखाता है।

```powershell
git show
```

Latest commit में क्या बदलाव हुआ, दिखाता है।

```powershell
git diff
```

Unstaged changes का फर्क दिखाता है।

```powershell
git diff --staged
```

Staged changes का फर्क दिखाता है।

```powershell
git remote -v
```

GitHub remote address दिखाता है।

## 12. ध्यान रखने वाली बातें

- Password या Personal Access Token को किसी file या chat में save न करें।
- `git add .` चलाने से पहले `git status` देखकर files check करें।
- Commit message में बदलाव का स्पष्ट नाम लिखें।
- `git push` के बाद GitHub repository खोलकर बदलाव verify करें।
- अगर कोई file Git में नहीं भेजनी हो, तो उसे `.gitignore` में लिखें।

## इस project की current files

- `Windows_Shortcut_Keys.html` - Search और category filters वाला visual shortcut reference।
- `Windows_Shortcut_Keys.txt` - Plain-text shortcut reference।
- `Git_Learning_Notes.md` - Git और GitHub सीखने के commands और explanations।