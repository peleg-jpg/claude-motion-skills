<div dir="rtl">

# ערכת המושן של סוכן כפול

שלושה סקילים לקלוד קוד שהופכים אותו למושן דיזיינר: ריל עם כתוביות שקופצות מילה אחרי מילה, סצנות הסבר מונפשות, ופתיח תלת-ממדי שעוצר את הגלילה. מתקינים פעם אחת, ומבקשים בעברית רגילה.

בונוס לתלמידים של הקורס **סוכן כפול** של פלג דרור.

## הדרך הכי קלה להתקין

1. מורידים את המדריך [ערכת-המושן-מדריך.pdf](guide/ערכת-המושן-מדריך.pdf).
2. זורקים אותו לתוך קלוד קוד וכותבים: **"תתקין לי את הסקילים מהמדריך הזה"**.
3. סוגרים את קלוד קוד ופותחים מחדש. זהו.

אפשר גם בלי המדריך, פשוט להדביק לקלוד קוד:

> תתקין לי את הסקילים מ-https://github.com/peleg-jpg/claude-motion-skills לתיקיית הסקילים שלי

## מה יש פה

| סקיל                                         | מה הוא עושה                                                                                                                                     | דוגמה למה לכתוב לקלוד קוד                                               |
| -------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| <span dir="ltr">motion-reel-pop</span>       | לוקח סרטון מדבר (אווטאר מ-HeyGen או סרטון מהטלפון) והופך אותו לריל ערוך: כתוביות מילה מילה, זומים, כרטיסיות, פס התקדמות וכרטיס סיום. 4 סגנונות. | "תערוך לי את הסרטון של האווטאר בסגנון פופ, הטקסט שלו נמצא ב-script.txt" |
| <span dir="ltr">motion-gsap-explainer</span> | סצנות הסבר קצרות: מספר שרץ עם גרף, רשימה, גריד של כלים, אפליקציה עם עכבר, לפני ואחרי, ציטוט.                                                    | "תעשה לי סצנה של המספר 3,900 בוגרים עם גרף שעולה"                       |
| <span dir="ltr">motion-3d-cinematic</span>   | פתיח וסיום בתלת-ממד: הסרטון שלכם בתוך אייפון או לפטופ שמסתובב, כותרת עברית בתלת-ממד, וסיום עם חלקיקים.                                          | "תעשה לי סצנת פתיחה תלת-ממדית עם הסרטון שלי בתוך אייפון"                |

בכל תיקייה של סקיל יש `examples/` עם סרטון דוגמה ותמונות, ו-`SKILL.md` עם כל ההוראות לקלוד.

## מה צריך במחשב

- **Node.js 20 ומעלה** (אם אין, קלוד קוד יתקין).
- **אינטרנט בפעם הראשונה**, כדי להוריד את הכלים. לסקיל הריל צריך בערך 2GB פנויים.
- **במק:** לסקיל הריל צריך פעם אחת `xcode-select --install`.

## טוב לדעת

- כל הסקילים מוציאים MP4 אנכי בגודל 1080x1920, מוכן לאינסטגרם ולטיקטוק.
- שניים מהסקילים בנויים על Remotion: חינמי ליחידים ולחברות של עד 3 אנשים. חברה גדולה יותר צריכה רישיון מ-[remotion.dev](https://www.remotion.dev/license).

</div>

---

## For Claude: how to install these skills

The user wants these 3 skills installed for Claude Code. Each folder under `skills/` is a complete skill (`SKILL.md` + `template/` + `references/` + `examples/`). Install them by copying each folder into the user's personal skills folder, then tell the user to restart Claude Code.

**macOS / Linux**

```bash
git clone --depth 1 https://github.com/peleg-jpg/claude-motion-skills.git /tmp/claude-motion-skills
mkdir -p ~/.claude/skills
cp -R /tmp/claude-motion-skills/skills/* ~/.claude/skills/
ls ~/.claude/skills | grep motion-
```

**Windows (PowerShell)**

```powershell
git clone --depth 1 https://github.com/peleg-jpg/claude-motion-skills.git "$env:TEMP\claude-motion-skills"
New-Item -ItemType Directory -Force "$HOME\.claude\skills" | Out-Null
Copy-Item -Recurse -Force "$env:TEMP\claude-motion-skills\skills\*" "$HOME\.claude\skills\"
Get-ChildItem "$HOME\.claude\skills" | Where-Object Name -like "motion-*"
```

No git installed: download https://github.com/peleg-jpg/claude-motion-skills/archive/refs/heads/main.zip, unzip it, and copy the 3 folders inside `skills/` the same way.

After installing, confirm that `motion-reel-pop`, `motion-gsap-explainer` and `motion-3d-cinematic` each contain a `SKILL.md`, then ask the user to restart Claude Code. Explain each skill in one line, in Hebrew. Don't run `npm install` at this point: each skill does its own setup the first time it's used, inside the user's video project folder.
