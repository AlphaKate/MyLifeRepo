# סדר יום: הקמה

אתר סטטי שמתחבר ל-Google Calendar בהרשאת קריאה בלבד ונוסף למסך הבית. אין שרת, והאירועים לא נשמרים בשום מקום מלבד הדפדפן שלך.

## הסדר

### 1. אירוח (מקבלים כתובת)
העלה את כל הקבצים בתיקייה הזו לאחסון סטטי חינמי עם HTTPS:
- Netlify: app.netlify.com/drop, גרור את התיקייה (אחרי פתיחת ה-zip).
- Cloudflare Pages: Create project, Direct Upload.
- GitHub Pages: מעלים את הקבצים לריפו ומפעילים Pages.

רשום את הכתובת, למשל `https://xxxx.netlify.app`. בלי `/` בסוף ובלי נתיב.

### 2. פרויקט ב-Google Cloud
ב-console.cloud.google.com:
1. צור פרויקט חדש.
2. APIs & Services ← Library ← Google Calendar API ← Enable.
3. Google Auth Platform (או OAuth consent screen): User type = External. מצב Testing.
4. Audience / Test users: הוסף את כתובת הג'ימייל שלך.
5. Data Access (Scopes): הוסף `https://www.googleapis.com/auth/calendar.readonly`.
6. Clients ← Create client ← Web application.
7. ב-Authorized JavaScript origins הדבק את הכתובת משלב 1. Create.
8. העתק את ה-Client ID (נגמר ב-`.apps.googleusercontent.com`).

שמות המסכים של Google משתנים מדי פעם, אבל הרכיבים זהים.

### 3. הדבקת ה-Client ID
פתח את `config.js`, החלף את `YOUR_CLIENT_ID.apps.googleusercontent.com` ב-Client ID שלך, והעלה מחדש את הקובץ לאותו אתר.

### 4. מסך הבית
- אייפון: פתח את הכתובת ב-Safari ← שיתוף ← הוסף למסך הבית.
- אנדרואיד: פתח ב-Chrome ← שלוש נקודות ← הוסף למסך הבית (או התקן אפליקציה).

## בפתיחה הראשונה
לחץ "התחבר עם Google". בגלל מצב Testing תראה "Google hasn't verified this app": לחץ Advanced ← Continue. זה צפוי כי האפליקציה שלך בלבד.

## מה לצפות
- ההתחברות תקפה בערך שעה. אחרי זה לוחצים שוב על "התחבר עם Google".
- אם חלון ההתחברות לא נפתח מתוך האפליקציה שבמסך הבית באייפון, פתח את האתר ב-Safari והתחבר שם, או בקש התחברות בדף מלא.
- אם מופיעה שגיאה 403: ודא ש-Calendar API מופעל ושהמייל שלך ברשימת Test users.
- שינוי בקבצים נקלט מיד בכל פתיחה עם חיבור לאינטרנט. בלי חיבור נטען עותק שמור.
