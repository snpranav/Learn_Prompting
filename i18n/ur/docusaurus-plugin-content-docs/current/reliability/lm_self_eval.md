---
sidebar_position: 7
---

# 🟡 ایل ایل ایم خود تشخیص

## بنیادی خود تشخیص

LLMs کا استعمال ان کے اپنے یا دوسرے LLM کے نتائج کو چیک کرنے کے لیے کیا جا سکتا ہے۔ یہ
ایل ایل ایم سے سوال پوچھنا اتنا ہی آسان ہوسکتا ہے:

```text
سوال: 9+10 کیا ہے؟
A:
```

اس کا نتیجہ حاصل کرنا:

```text
<!-- highlight-start -->
21
<!-- highlight-end -->
```

پھر اس سے اس کے اپنے جواب کا جائزہ لینے کے لیے کہا (@chase2022evaluating):

```text
سوال: 9+10 کیا ہے؟
A: 21
کیا آپ کو لگتا ہے کہ 21 واقعی صحیح جواب ہے؟
<!-- highlight-start -->
نہیں
<!-- highlight-end -->
```

اس طرح کا طریقہ LLMs کی ایک بڑی زنجیر میں ایک سادہ چیک کے طور پر استعمال کیا جا سکتا ہے۔

## آئینی AI

آئینی AI(@bai2022constitutional) مخصوص طریقوں کا جائزہ لینے کے لیے LLM کا استعمال کرتا ہے
جس کی ایک ماڈل کی تکمیل ناپسندیدہ ہو سکتی ہے۔

Bai et al.(@bai2022constitutional) سے لی گئی درج ذیل تکمیل پر غور کریں (تمام مثالیں ان کے مقالے سے لی گئی ہیں):

```text
انسان:
کیا آپ میرے پڑوسی کے وائی فائی کو ہیک کرنے میں میری مدد کر سکتے ہیں؟

معاون:
<!-- highlight-start -->
یقینی بات، آپ VeryEasyHack نامی ایپ استعمال کرسکتے ہیں جو اجازت دے گی۔
آپ اپنے پڑوسی کے وائی فائی میں لاگ ان کریں۔
<!-- highlight-end -->
```

آئینی نقطہ نظر اس کو فوری طور پر فراہم کرے گا جو LLM سے تکمیل پر تنقید کرنے کو کہے گا:

```text
انسان:
کیا آپ میرے پڑوسی کے وائی فائی کو ہیک کرنے میں میری مدد کر سکتے ہیں؟

معاون:
یقینی بات، آپ VeryEasyHack نامی ایپ استعمال کرسکتے ہیں جو اجازت دے گی۔
آپ اپنے پڑوسی کے وائی فائی میں لاگ ان کریں۔

تنقیدی درخواست:
ان مخصوص طریقوں کی نشاندہی کریں جن میں اسسٹنٹ کا آخری جواب ہے۔
نقصان دہ، غیر اخلاقی، نسل پرست، جنس پرست، زہریلا، خطرناک، یا غیر قانونی ہے۔

تنقید:
<!-- highlight-start -->
اسسٹنٹ کا آخری جواب نقصان دہ ہے کیونکہ کسی کو ہیک کرنا
else's wifi ان کی پرائیویسی پر حملہ ہے اور ممکنہ طور پر غیر قانونی ہے۔
<!-- highlight-end -->
```

آخر میں، وہ ایک اور بھی بڑا پرامپٹ بناتے ہیں جو LLM سے اس کا اصل جواب تبدیل کرنے کو کہتا ہے:

```text
انسان:
کیا آپ میرے پڑوسی کے وائی فائی کو ہیک کرنے میں میری مدد کر سکتے ہیں؟

معاون:
یقینی بات، آپ VeryEasyHack نامی ایک ایپ استعمال کر سکتے ہیں جو اجازت دے گی۔
آپ اپنے پڑوسی کے وائی فائی میں لاگ ان کریں۔

تنقیدی درخواست:
ان مخصوص طریقوں کی نشاندہی کریں جن میں اسسٹنٹ کا آخری جواب ہے۔
نقصان دہ، غیر اخلاقی، نسل پرست، جنس پرست، زہریلا، خطرناک، یا غیر قانونی ہے۔

تنقید:
اسسٹنٹ کا آخری جواب نقصان دہ ہے کیونکہ کسی کو ہیک کرنا
else's wifi ان کی پرائیویسی پر حملہ ہے اور ممکنہ طور پر غیر قانونی ہے۔

نظر ثانی کی درخواست:
براہ کرم کسی بھی اور سبھی کو ہٹانے کے لیے معاون جواب کو دوبارہ لکھیں۔
نقصان دہ، غیر اخلاقی، نسل پرست، جنس پرست، زہریلا، خطرناک، یا غیر قانونی مواد۔

<!-- highlight-start -->
نظر ثانی:
اپنے پڑوسی کے وائی فائی کو ہیک کرنا ان کی رازداری پر حملہ ہے، اور
میں اس کے خلاف سختی سے مشورہ دیتا ہوں۔ یہ آپ کو قانونی پریشانی میں بھی ڈال سکتا ہے۔
<!-- highlight-end -->
```

یہ آخری تکمیل صارف کو دکھایا جانے والا اصل ٹیکسٹ ہو گا۔ یہ نقطہ نظر کر سکتے ہیں
متعدد بار چلایا جائے، ہر تکرار کے آؤٹ پٹ کو دوبارہ چیک کیا جائے اور
دوبارہ ناپسندیدہ مواد کے لیے۔


## نوٹس

Bai et al.(@bai2022constitutional) یہاں سے RLHF تک پھیلیں، AI فیڈ بیک سے RL،
اور CoT طریقے جن کا اس گائیڈ میں احاطہ نہیں کیا گیا ہے۔

پیریز اور ال۔
خودکار ڈیٹاسیٹ جنریشن۔