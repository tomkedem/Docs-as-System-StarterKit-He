<div dir="rtl" style="text-align: right;">

> ⚙️ **הערת תבנית:**  
> קובץ זה הוא תבנית רשמית של **Docs-as-System**.  
> אין לערוך אותו ישירות בתוך המאגר הראשי.  
> בעת הקמת פרויקט חדש, הסוכן מעתיק אותו אל התיקייה `docs/automation/`  
> בשם `VALIDATION_PIPELINE.md` ומעדכן בו את הבדיקות והשלבים הרלוונטיים לפרויקט בפועל.

# 🧪 תבנית Pipeline ולידציה — Validation Pipeline Template

**מסמך בפרויקט בפועל:** `docs/automation/VALIDATION_PIPELINE.md`  
**תבנית בתיקיית התבניות:** `templates/automation/VALIDATION_PIPELINE_TEMPLATE.md`  
**יוצר:** סוכן (בהנחיה אנושית)  
**מאשר:** אדם (ארכיטקט / מנהל איכות / Tech Lead)  
**מטרה:** להגדיר את רצף הבדיקות האוטומטיות שמבטיחות את תקינות המערכת, התיעוד והתאימות למחזור הנוכחי (BY_CYCLE).

---

## 🎯 מטרת המסמך

לתאר את ה־Pipeline שמוודא שכל שכבות המערכת — קוד, תיעוד ו־Logs —  
נמצאות בעקיבות מלאה זו עם זו.  
הוא מהווה את שלב ה־**Validation Layer** בשיטת Docs-as-System,  
ומוודא שהסוכן, הקוד והמסמכים מתואמים ומאושרים לפני סגירת מחזור.

---

## 🧩 עקרונות הליבה

1. **בדיקה אוטומטית לפני סגירה:**  
   כל מחזור (`BY_CYCLE`) מסתיים בהפעלה מלאה של ה־Validation Pipeline.  
2. **שקיפות:**  
   כל תוצאה נרשמת ב־`VALIDATION_REPORT.md` ונשמרת בלוג.  
3. **Self-Check:**  
   הסוכן מבצע בדיקות מקדימות על עצמו ומזהה חוסר עקביות.  
4. **אין מחיקה:**  
   אין לשכתב או למחוק דוחות עבר — רק להוסיף רשומות חדשות.  
5. **אישור אנושי:**  
   סגירת מחזור תתבצע רק לאחר Review ואישור של אדם מוסמך.

---

## 🧱 שלבי ה־Pipeline

| שלב | שם הבדיקה | מטרה | סוג בדיקה | מופעל על ידי |
|------|-------------|---------|--------------|----------------|
| 1 | **Schema Validation** | בדיקת מבנה מסמכי Markdown/YAML | Static | סוכן |
| 2 | **Log Consistency** | אימות שכל פעולה מופיעה בלוג ומקושרת למחזור | Logical | סוכן |
| 3 | **Agent Self-Verification** | בדיקת פעולות שבוצעו לעומת מה שתועד | Behavioral | סוכן |
| 4 | **Security Review** | חיפוש טוקנים, סיסמאות ומפתחות גישה | Static | סוכן |
| 5 | **Documentation Diff Check** | השוואת שינויי קבצים מול תיעוד רשמי | Semantic | סוכן |
| 6 | **Human Review Required** | שליחת סיכום חריגות לבדיקה אנושית | Manual | אדם |

---

## ⚙️ דוגמת זרימת Pipeline

[Schema Validation] → [Log Consistency] → [Self-Verification]
↓
[Security Review] → [Documentation Diff] → [Human Approval]


> הסוכן מריץ את השלבים האוטומטיים בלבד.  
> שלב האישור האנושי נסגר רק לאחר Review אנושי וחתימה על `VALIDATION_REPORT.md`.

---

## 🧾 דוגמה לתוצאת Pipeline (מתועדת אוטומטית)

```yaml
CycleId: CY-2025-Q4-A
StartedAt: 2025-11-10T08:30Z
FinishedAt: 2025-11-10T08:34Z
TriggeredBy: Agent-A01
ValidatedFiles:
  - docs/project/PROJECT_OVERVIEW.md
  - docs/architecture/ARCHITECTURE_BLUEPRINT.md
  - docs/logs/IMPLEMENTATION_LOG.md
Results:
  SchemaValidation: Passed
  LogConsistency: Passed
  SecurityReview: Passed
  SelfVerification: Passed
  HumanReview: Pending
Summary: |
  All automated checks passed successfully. Awaiting human approval.

```
## 🧮 הוראה לסוכן – יצירת קובץ הפלט

לאחר סיום כל הרצת Pipeline,  
הסוכן נדרש לשמור את תוצאות הבדיקות בקובץ נפרד בפורמט **YAML**  
בשם קבוע לפי המחזור הנוכחי.

**מיקום שמירה:**  
`docs/automation/results/VALIDATION_RESULT_<CycleId>.yaml`

**דוגמה מלאה:**  
`docs/automation/results/VALIDATION_RESULT_CY-2025-Q4-A.yaml`

---

### 🧩 כללים

1. אם התיקייה `docs/automation/results/` לא קיימת — יש ליצור אותה.  
2. הקובץ נשמר תמיד בפורמט קריא (**YAML**) ומכיל את השדות המדויקים מהפלט.  
3. אין לשכתב תוצאות של מחזורים קודמים — כל מחזור יוצר קובץ חדש.  
4. הקובץ נוסף אוטומטית ל־Commit הבא עם התג `VALIDATION_RESULT`.  
5. במקביל נרשמת ביומן (`IMPLEMENTATION_LOG.md`) רשומת פעולה מסוג `PIPELINE_EXECUTION`.

> כך מובטח שכל מחזור יקבל תיעוד עצמאי ובר־שחזור מלא  
> של תוצאות הבדיקות האוטומטיות.


## 🔍 טיפול בכשלים

| סוג כשל | תג בלוג | פעולה נדרשת | רמת סיכון |
|-----------|------------|----------------|--------------|
| **חסר קובץ קריטי** | `MISSING_DOC` | יצירה מחדש של המסמך על ידי הסוכן | בינונית |
| **אי־עקביות בין לוג למסמך** | `LOG_MISMATCH` | ניתוח אוטומטי + ביקורת אנושית | גבוהה |
| **מבנה YAML שגוי** | `SCHEMA_ERROR` | תיקון אוטומטי של הפורמט | נמוכה |
| **חריגה אבטחית** | `SECURITY_FLAG` | עצירה מיידית ואישור CISO | קריטית |

> כל כשל נוסף שמתגלה נרשם ב־`IMPLEMENTATION_LOG.md`  
> תחת קטגוריית `VALIDATION_EXCEPTION`.

---

## 🔁 אינטגרציה עם Guardrails

- ה־Validation Pipeline פועל **לאחר** מנגנוני ה־Guardrails.  
- Guardrails מגנים בזמן אמת; Validation Pipeline מאמת בסוף מחזור.  
- שילוב שניהם מבטיח שכל פעולה מתועדת, מאובטחת ומאושרת אנושית.  
- תוצאות ה־Pipeline משמשות בסיס להפקת דו"ח תקופתי (`VALIDATION_REPORT.md`).

---

## 🧭 סיכום

`VALIDATION_PIPELINE.md` הוא השלב שבו התיעוד, הקוד והאדם נפגשים.  
הוא מוודא שכל שינוי במערכת אכן תועד, נבדק ואושר לפני הפצה.  
זהו המנוע שמאפשר לשיטה לשמור על עקביות, אמינות ויכולת שיחזור מלאה —  
בלי לוותר על מהירות ויעילות בעבודה עם סוכני AI.

---

© 2025 תומר קדם. חלק ממערך התבניות הרשמי של **Docs-as-System**.

</div>
