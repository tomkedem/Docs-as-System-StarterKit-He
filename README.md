<div dir="rtl" style="text-align: right;">

# Docs-as-System StarterKit (Hebrew Edition)

**Docs-as-System StarterKit Hebrew** הוא CLI שמייצר פרויקט חדש לפי המתודולוגיה Docs-as-System.  
הכלי בונה שלד בסיסי, ממלא את תיקיית `docs` בתבניות עדכניות, ומכין אותך לעבודה עם סוכן ה־AI בתוך ה־IDE.

המטרה היא להתחיל כל פרויקט עם מבנה ברור, עקבי ומוכן לעבודה, בלי לבזבז זמן על יצירת קבצים ותיקיות.

---

## התקנה

### שימוש ללא התקנה גלובלית

```bash
npx docs-as-system-starterkit-he init my-project
```
## התקנה גלובלית

```bash
npm install -g docs-as-system-starterkit-he
das-he init my-project
```

## פקודות זמינות
יצירת פרויקט חדש
```bash
das-he init project-name
```

הפקודה יוצרת פרויקט חדש הכולל:

שלד פרויקט בסיסי מתוך starter-project

תיקיית docs מלאה בתבניות
(agent, planning, architecture, logs, automation, project)

קובץ AGENT_CONFIG.yaml למילוי פרטי הפרויקט

סקריפטי Git בתיקייה automation/git

קבצי תצורה חשובים:
.gitignore, .editorconfig, .gitattributes

README בסיסי לפרויקט החדש

---

## מבנה הפרויקט החדש

לאחר יצירת פרויקט, המבנה ייראה כך:
</div>

<div dir="ltr" style="text-align: left;">

```plaintext
📁 my-project/
├── 📄 .editorconfig
├── 📄 .gitattributes
├── 📄 .gitignore
├── 📄 README.md
├── 📁 src/
│ └── 📁 automation/
│     └─── 📁 git/
│           ├── 📄 CREATE_BRANCH.sh
│           ├── 📄 MERGE_AFTER_APPROVAL.sh
│           ├── 📄 OPEN_PULL_REQUEST.sh
│           ├── 📄 PUSH_BRANCH.sh
│           ├── 📄 STAGE_AND_COMMIT.sh
│           └── 📄 README.md
└── 📁 docs/
├── 📁 agent/
├── 📁 architecture/
├── 📁 planning/
├── 📁 automation/
├── 📁 project/
└── 📁 logs/
```

</div>
<div dir="rtl" style="text-align: right;">

## למה Docs-as-System?

‏Docs-as-System היא מתודולוגיה שמחברת בין:

- תיעוד  
- קוד  
- תהליכי פיתוח  
- סוכני AI  

בצורה שמייצרת מערכת חיה ומתועדת כל הזמן.  
המתודולוגיה מותאמת במיוחד לעבודה עם סוכני AI שפועלים מתוך ה־IDE.

---

## תורמים

החבילה נבנתה בשיתוף פעולה של אנשים מצוינים, וכל תרומה מוזכרת כאן כדי לשמור על שקיפות והערכה מקצועית.

### תורמים לפרויקט Docs as System StarterKit Hebrew

- **יובל ואנונו**  
  השתתפה בגיבוש הרעיונות הראשוניים וליוותה את בניית ה CLI.

- **יהונתן ממן**  
  תרם בבדיקות, הערות עומק ושיפור התבניות.

### איך מצטרפים לרשימת התורמים

אם תרמת קוד, שיפרת תבנית, תיקנת בעיה או עזרת לעצב את הכלי בדרכו הנוכחית  
אתה מוזמן לפתוח Pull Request, ובאישור יתווסף שמך כאן.

התיעוד הזה חי, ומתעדכן בכל תרומה משמעותית.

---

## 📄 רישיון

MIT License  
החבילה חופשית לשימוש, שינוי והטמעה בכל פרויקט.

---


ריפו ב GitHub    
https://github.com/tomkedem/Docs-as-System-StarterKit-He

---

>© 2025 תומר קדם. חלק ממערך התבניות הרשמי של **Docs-as-System**.

</div>