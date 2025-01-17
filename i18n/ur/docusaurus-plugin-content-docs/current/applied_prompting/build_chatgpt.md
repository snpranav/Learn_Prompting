---
sidebar_position: 4
---

# 🟢 GPT-3 سے ChatGPT بنائیں

## تعارف

[ChatGPT](https://chat.openai.com/chat) نے پچھلے مہینے میں دھوم مچا دی ہے، صرف ایک ہفتے میں ایک ملین صارفین حاصل کر لیے ہیں۔ حیرت انگیز طور پر، بنیادی ماڈل، GPT-3 2020 میں ڈیبیو ہوا اور اسے عوامی رسائی کے لیے جاری کیا گیا <a href="https://openai.com/blog/api-no-waitlist/">ایک سال پہلے!</a>

ان لوگوں کے لیے جو نہیں جانتے، ChatGPT OpenAI کا ایک نیا زبان کا ماڈل ہے جسے GPT-3 سے بات چیت کے لیے بہتر بنایا گیا تھا (@chatgpt2022)۔ اس میں صارف دوست چیٹ انٹرفیس ہے، جہاں آپ ان پٹ دے سکتے ہیں اور AI اسسٹنٹ سے جواب حاصل کر سکتے ہیں۔ اسے [chat.openai.com](https://chat.openai.com/chat) پر دیکھیں۔

اگرچہ GPT-3 کے ابتدائی ورژن موجودہ GPT-3.5 سیریز کی طرح ترقی یافتہ نہیں تھے، پھر بھی وہ متاثر کن تھے۔ یہ ماڈل ایک API اور ایک <a href="https://beta.openai.com/playground">پلے گراؤنڈ ویب UI انٹرفیس</a> کے ذریعے دستیاب ہیں جو آپ کو کنفیگریشن کے کچھ ہائپر پیرامیٹر اور ٹیسٹ پرامپٹس کو ٹیون کرنے دیتا ہے۔ GPT-3 نے اہم کرشن حاصل کیا، لیکن یہ ChatGPT کی وائرلیت تک نہیں پہنچا۔

GPT-3 کے مقابلے میں ChatGPT کو جو چیز اتنی کامیاب بناتی ہے، وہ یہ ہے کہ اوسط فرد کے لیے ڈیٹا سائنس، لینگویج ماڈلز، یا AI کے بارے میں ان کے علم سے قطع نظر، ایک سیدھا سادہ AI اسسٹنٹ کے طور پر اس کی رسائی ہے۔

اس مضمون میں، میں جائزہ لیتا ہوں کہ ChatGPT جیسے چیٹ بوٹس کو GPT-3 جیسے بڑے لینگویج ماڈل کا استعمال کرتے ہوئے کیسے لاگو کیا جا سکتا ہے۔

## محرک
یہ مضمون جزوی طور پر <a href="https://twitter.com/goodside">Riley Goodside</a> کی ایک ٹویٹ کی وجہ سے لکھا گیا تھا، جس میں یہ نوٹ کیا گیا تھا کہ ChatGPT کو کیسے نافذ کیا جا سکتا تھا۔

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">GPT‑3 (text‑davinci‑003) کا استعمال کرتے ہوئے اپنا ناک آف چیٹ جی پی ٹی کیسے بنائیں — جہاں آپ قواعد کو اپنی مرضی کے مطابق بنا سکتے ہیں۔ اپنی ضروریات کے مطابق، اور ایک API پر نتیجے میں چیٹ بوٹ تک رسائی حاصل کریں۔ <a href="https://t.co/9jHrs91VHW">pic.twitter.com/9jHrs91VHW</a></p>&mdash; Riley Goodside (@goodside) <a href="https://twitter.com/goodside/status/1607487283782995968?ref_src=twsrc%5Etfw">26 دسمبر 2022</a></blockquote> <script async src=" https://platform.twitter.com/widgets.js" charset="utf-8"></script>

GPT-3.5 سیریز کے دیگر ماڈلز کی طرح، ChatGPT کو [RLHF](https://huggingface.co/blog/rlhf) کا استعمال کرتے ہوئے تربیت دی گئی تھی، لیکن اس کی زیادہ تر تاثیر **اچھے پرامپٹ** کے استعمال سے آتی ہے۔

## پرامپٹ

<a href="https://learnprompting.org/docs/basics/prompting">پرامپٹنگ AI کو کچھ کرنے کی ہدایت دینے کا عمل ہے۔ </a> جیسا کہ آپ نے شاید آن لائن ChatGPT کی مثالوں میں دیکھا ہوگا، آپ اسے کچھ بھی کرنے کے لیے کہہ سکتے ہیں۔ عام استعمال کے معاملات میں ٹیکسٹ کا خلاصہ کرنا، تفصیل پر مبنی مواد لکھنا، یا نظمیں، ترکیبیں اور بہت کچھ جیسی چیزیں بنانا شامل ہیں۔

<p></p>

چیٹ جی پی ٹی زبان کا ماڈل اور یوزر انٹرفیس دونوں ہے۔ صارف کی طرف سے انٹرفیس میں پرامپٹ ان پٹ دراصل ایک بڑے پرامپٹ میں ڈالا جاتا ہے جس میں صارف اور ChatGPT کے درمیان ہونے والی پوری گفتگو ہوتی ہے۔ یہ بنیادی زبان کے ماڈل کو گفتگو کے سیاق و سباق کو سمجھنے اور مناسب جواب دینے کی اجازت دیتا ہے۔

لینگویج ماڈل یہ پتہ لگا کر پرامپٹ کو مکمل کرتا ہے کہ اس کے بعد کون سے الفاظ آتے ہیں ان امکانات کی بنیاد پر جو اس نے پری ٹریننگ (@jurafsky2009) کے دوران سیکھے۔

<p></p>

GPT-3 ایک سادہ ہدایات یا پرامپٹ میں دی گئی چند مثالوں سے 'سیکھنے' کے قابل ہے۔ مؤخر الذکر کو چند شاٹ کہا جاتا ہے، یا سیاق و سباق سیکھنے میں (@brown2020language)۔ اوپر دیے گئے چیٹ بوٹ پرامپٹ میں، میں Skippy کے نام سے ایک فرضی چیٹ بوٹ بناتا ہوں، اور اسے صارفین کو جوابات فراہم کرنے کی ہدایت کرتا ہوں۔ GPT-3 آگے اور پیچھے کی شکل میں، `USER: {user input}` اور `SKIPPY: {skippy response}` پر اٹھتا ہے۔ GPT-3 سمجھتا ہے کہ Skippy ایک چیٹ بوٹ ہے اور پچھلے تبادلے ایک بات چیت ہیں، تاکہ جب ہم اگلا صارف ان پٹ فراہم کریں تو "Skippy" جواب دے گا۔

### حفظ

سکپی اور صارف کے درمیان ماضی کے تبادلے اگلے پرامپٹ میں شامل ہو جاتے ہیں۔ ہر بار جب ہم زیادہ صارف ان پٹ دیتے ہیں اور مزید چیٹ بوٹ آؤٹ پٹ حاصل کرتے ہیں، اس نئے تبادلے کو شامل کرنے کے لیے پرامپٹ پھیلتا ہے۔ اس طرح اسکپی اور چیٹ جی پی ٹی جیسے چیٹ بوٹس **پچھلے ان پٹس کو یاد رکھ سکتے ہیں۔** تاہم، ایک حد ہے کہ ایک GPT-3 چیٹ بوٹ کتنا یاد رکھ سکتا ہے۔

متعدد تبادلوں کے بعد پرامپٹس بڑے پیمانے پر حاصل کر سکتے ہیں، خاص طور پر اگر ہم بلاگ پوسٹس جیسے طویل جوابات پیدا کرنے کے لیے چیٹ بوٹ کا استعمال کر رہے ہیں۔ GPT-3 کو بھیجے گئے پرامپٹ ٹوکنز میں تبدیل ہو جاتے ہیں، جو انفرادی الفاظ یا ان کے حصے ہوتے ہیں۔ <a href="https://help.openai.com/en/articles/4936856-what-are-tokens-and-how-to-count-them">4097 ٹوکنز کی ایک حد ہے (تقریباً 3000 الفاظ) </a> ChatGPT سمیت GPT-3 ماڈلز کے لیے مشترکہ پرامپٹ اور تیار کردہ جواب کے لیے۔

### چند مثالیں۔

چیٹ بوٹ پرامپٹس کے استعمال کے بہت سے مختلف کیسز ہیں جو پچھلی گفتگو کو محفوظ کرتے ہیں۔ ChatGPT کا مقصد ایک ہمہ مقصد جنرل اسسٹنٹ ہونا ہے اور میرے تجربے میں، یہ شاذ و نادر ہی فالو اپ پوچھتا ہے۔

#### تھراپی چیٹ بوٹ جو آپ کے دن کے بارے میں پوچھتا ہے۔

چیٹ بوٹ کا ہونا مددگار ثابت ہو سکتا ہے جو فعال طور پر سوالات پوچھتا ہے اور صارف سے رائے لیتا ہے۔ ذیل میں ایک مثال تھیراپی چیٹ بوٹ پرامپٹ ہے جو سوال پوچھے گا اور صارف کو اپنے دن کے بارے میں سوچنے میں مدد کرے گا۔


#### پرانے جریدے کے اندراجات کا استعمال کرتے ہوئے اپنے چھوٹے سے بات کریں۔

<a href="https://twitter.com/michellehuang42">Michelle Huang</a> نے اپنے چھوٹے کے ساتھ بات چیت کرنے کے لیے GPT-3 کا استعمال کیا۔ پرامپٹ کچھ سیاق و سباق کا استعمال کرتا ہے، اس معاملے میں پرانے جریدے کے اندراجات، چیٹ بوٹ اسٹائل کے ساتھ آگے پیچھے کی شکل کے ساتھ جوڑ دی جاتی ہے۔ GPT-3 ان اندراجات کی بنیاد پر کسی شخصیت کی نقل کرنے کے قابل ہے۔

<p></p>

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">i trained an ai chatbot on my childhood journal entries - so that i could engage in real-time dialogue with my &quot;inner child&quot;<br/><br/>some reflections below:</p>&mdash; michelle huang (@michellehuang42) <a href="https://twitter.com/michellehuang42/status/1597005489413713921?ref_src=twsrc%5Etfw">November 27, 2022</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 

ٹویٹ سے اشارہ:
```markdown
ذیل میں پریزنٹ مشیل (عمر [رییکٹڈ]) اور ینگ مشیل (عمر 14) کے ساتھ گفتگو ہے۔

ینگ مشیل نے جریدے کے درج ذیل اندراجات لکھے ہیں:
[ڈائری اندراجات یہاں]

مشیل کو پیش کریں: [اپنے سوالات یہاں ٹائپ کریں]
```

مصنف نوٹ کرتا ہے کہ ڈائری کے اندراجات ٹوکن کی حد تک پہنچ سکتے ہیں۔ اس صورت میں آپ چند اندراجات کو منتخب کر سکتے ہیں یا کئی اندراجات کا خلاصہ کرنے کی کوشش کر سکتے ہیں۔

## نفاذ

میں Python میں ایک سادہ GPT-3 سے چلنے والی چیٹ بوٹ کوڈنگ کے ذریعے چلوں گا۔ آپ جو ایپ بنا رہے ہیں اس میں GPT-3 کو شامل کرنا OpenAI API کا استعمال کرتے ہوئے ناقابل یقین حد تک آسان ہے۔ آپ کو OpenAI پر ایک اکاؤنٹ بنانے اور ایک API کلید حاصل کرنے کی ضرورت ہوگی۔ ان کی دستاویزات <a href="https://beta.openai.com/docs/introduction">یہاں</a> دیکھیں۔

ہمیں کیا کرنے کی ضرورت ہے اس کا جائزہ:

1. صارف کے ان پٹ کو GPT-3 کے لیے چیٹ بوٹ پرامپٹ میں فارمیٹ کریں۔
2. GPT-3 سے تکمیل کے طور پر چیٹ بوٹ کا جواب حاصل کریں۔
3. صارف کے ان پٹ اور چیٹ بوٹ کے جواب دونوں کے ساتھ پرامپٹ کو اپ ڈیٹ کریں۔
4. لوپ

یہ پرامپٹ ہے جو میں استعمال کروں گا۔ ہم python کو <conversation history\> اور <user input\> کو ان کی اصل قدروں سے بدلنے کے لیے استعمال کر سکتے ہیں۔

```python
chatbot_prompt = """
    As an advanced chatbot, your primary goal is to assist users to the best of your ability. This may involve answering questions, providing helpful information, or completing tasks based on user input. In order to effectively assist users, it is important to be detailed and thorough in your responses. Use examples and evidence to support your points and justify your recommendations or solutions.

    <conversation history>

    User: <user input>
    Chatbot:"""
```

میں اگلے صارف کے ان پٹ اور پچھلی گفتگو دونوں پر نظر رکھتا ہوں۔ چیٹ بوٹ اور صارف کے درمیان نیا ان پٹ/آؤٹ پٹ ہر لوپ کو جوڑ دیا جاتا ہے۔
```python
import openai

openai.api_key = "YOUR API KEY HERE"
model_engine = "text-davinci-003"
chatbot_prompt = """
As an advanced chatbot, your primary goal is to assist users to the best of your ability. This may involve answering questions, providing helpful information, or completing tasks based on user input. In order to effectively assist users, it is important to be detailed and thorough in your responses. Use examples and evidence to support your points and justify your recommendations or solutions.

<conversation history>

User: <user input>
Chatbot:"""


def get_response(conversation_history, user_input):
    prompt = chatbot_prompt.replace(
        "<conversation history>", conversation_history).replace("<user input>", user_input)

    # Get the response from GPT-3
    response = openai.Completion.create(
        engine=model_engine, prompt=prompt, max_tokens=2048, n=1, stop=None, temperature=0.5)

    # Extract the response from the response object
    response_text = response["choices"][0]["text"]

    chatbot_response = response_text.strip()

    return chatbot_response


def main():
    conversation_history = ""

    while True:
        user_input = input("> ")
        if user_input == "exit":
            break
        chatbot_response = get_response(conversation_history, user_input)
        print(f"Chatbot: {chatbot_response}")
        conversation_history += f"User: {user_input}\nChatbot: {chatbot_response}\n"

main()
```


ایک سادہ چیٹ بوٹ کے مکمل کوڈ کا <a href="https://gist.github.com/jayo78/79d8834e6e31bf942c7b604e1611b68d">یہاں ایک لنک ہے</a>۔

<p></p>

اب صرف ایک اچھا فرنٹ اینڈ بنانا باقی ہے جس کے ساتھ صارفین بات چیت کر سکیں!

[jayo78](https://twitter.com/jayo782) کی تحریر کردہ۔