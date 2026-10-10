# ARTI303 Assignment 1 — Pandas vs. Polars

حل تجريبي مكتمل التشغيل لبيانات nycflights13. يحتوي على الكود، نتائج القياس، فحص اتفاق النتائج، ومناقشة إنجليزية مبنية على التشغيل. راجع الإجابات واكتب الانطباعات الشخصية بصياغة مجموعتكم.

## الملفات
- `ARTI303_Assignment1_PandasVsPolars_v3.ipynb`: الحل مع المخرجات.
- `data/flights.csv`: البيانات العامة الأصلية، 336,776 صفًا، حوالي 31.67 MiB، دون تكرار أو تصنيع صفوف.
- `results/benchmark.csv`: أزمنة العمليات السبع.
- `results/environment.json`: مواصفات البيئة، الإصدارات، بصمة البيانات، وطريقة القياس.
- `requirements.txt`: المكتبات.
- `Submission_Draft.docx`: مسودة وفق ترتيب التسليم؛ انقل المحتوى إلى قالب الدكتور الرسمي إذا أرسله لكم.

## التشغيل على الماك
داخل مجلد المشروع في Terminal:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
python -m jupyterlab
```

افتح Notebook، ثم Restart Kernel and Run All. شُغلت النسخة المرفقة في عملية IPython جديدة داخل بيئة المساعد؛ تتغير الأرقام على جهازك. حد Polars مضبوط افتراضيًا على 4 workers ومذكور في النتائج. بعد إعادة التشغيل حدّث الأرقام في ملاحظات Markdown وتحليل Part 6 لتطابق جدولك الجديد. ملف CSV مرفق؛ يُنزَّل من المصدر تلقائيًا إذا كان مفقودًا، خارج القياس.

## GitHub والتسليم
1. أنشئ Fork لمستودع المادة ثم اجعله Public وأضف بقية أعضاء المجموعة Collaborators. تأكد من انضمام 5 أو 6 أعضاء للمجموعة في Blackboard.
2. داخل النسخة المحلية الصحيحة من المستودع نفذ `git pull origin main` قبل استبدال ملف التكليف بالحل. خذ صورة للشاشة كاملة تظهر Terminal والأمر والنتيجة الفعلية.
3. انقل ملفات هذا المشروع إلى المستودع بعد حفظ نسخة من ملف التكليف، ثم شغّل الحل في بيئة المادة واملأ أسماء جميع الأعضاء وأرقامهم والشعبة وتاريخ التسليم الفعلي.
4. افحص ما سيرفع باستخدام `git status`، ثم نفذ الأوامر المناسبة من جذر المستودع:

```bash
git add ARTI303_Assignment1_PandasVsPolars_v3.ipynb requirements.txt README.md .gitignore data/flights.csv results
git commit -m "Complete Pandas vs Polars assignment"
git push origin main
```

إذا كان اسم الفرع مختلفًا، استخدم اسم الفرع الصحيح. صوّر الشاشة كاملة بعد push بحيث يظهر الأمر والنتيجة. هذه الخطوات لم تُنفّذ على حساب مجموعتكم، ولم تُنشأ صور إثبات بديلة.
5. أضف أسماء المجموعة، صورة pull، رابط البيانات، رابط مستودعكم العام، ثم صورة push إلى Word بنفس هذا الترتيب. ارفع ملف Word واحدًا للمجموعة في Blackboard. لا تعتبر المسودة جاهزة للتسليم قبل استكمال هذه الحقول والأدلة.

## المصادر
- تعريف البيانات والوحدات: https://nycflights13.tidyverse.org/reference/flights.html
- مصدر CSV: https://raw.githubusercontent.com/vincentarelbundock/Rdatasets/master/csv/nycflights13/flights.csv
- Polars lazy execution: https://docs.pola.rs/user-guide/lazy/execution/
- Polars sorting: https://docs.pola.rs/api/python/stable/reference/dataframe/api/polars.DataFrame.sort.html
- DuckDB Python: https://duckdb.org/docs/stable/clients/python/overview

قراءات CSV تستخدم cache دافئًا؛ خمس إعادات مع median بعد warm-up، وثلاث للسلسلة. اختلاف dtypes الطبيعي بين المكتبتين مسجل. فحوصات الصحة خارج القياس وتشمل الفرز مع nulls last واستقرار ties، والمقارنة بعد محاذاة مفاتيح المجموعة وصفوف join.
