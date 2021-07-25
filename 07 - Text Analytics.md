<div id="readme" class="Box-body readme blob js-code-block-container p-5 p-xl-6 gist-border-0" dir="rtl">
    <article class="markdown-body entry-content container-lg" itemprop="text"><h1><a id="user-content-تحليلات-النص" class="anchor" aria-hidden="true" href="#تحليلات-النص"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>تحليلات النص</h1>


معالجة النصوص الطبيعية (NLP) هي فرع من فروع الذكاء الاصطناعي (AI) التي تتعامل مع اللغة المكتوبة والمنطوقة. يمكنك استخدام NLP لبناء برامج تستخرج المعنى الدلالي من النص أو الكلام، أو تصوغ إجابات ذات معنى في اللغة الطبيعية.

تتضمن *الخدمات المعرفية* في Microsoft Azure لخدمة *تحليلات النصوص*، التي توفر بعض إمكانيات NLP خارج الصندوق، بما في ذلك تحديد العبارات الأساسية في النص، وتصنيف النص بناءً على المشاعر.

![روبوت يقرأ دفتر ملاحظات](./images/NLP.jpg)

على سبيل المثال، لنفترض أن منظمة* Margie's Travel* الخيالية تشجع العملاء على إرسال مراجعات للإقامات الفندقية. يمكنك استخدام خدمة تحليلات النصوص لتلخيص المراجعات عن طريق استخراج العبارات الأساسية، وتحديد المراجعات الإيجابية والسلبية، أو تحليل نص المراجعة للإشارة إلى الأشياء المعروفة مثل المواقع أو الأشخاص.

## عرض مستندات المراجعات

لنبدأ بإلقاء نظرة على بعض مراجعات وتقييمات الفنادق التي تركها العملاء.

التقييمات في ملفات نصية. لرؤيتها، ما عليك سوى تشغيل الرمز أدناه بالنقر فوق الزر **تشغيل الخانة** (&#9655;) على يسار الخانة.


```python
import os

# اقرأ المراجعات في مجلد / المراجعات / البيانات
reviews_folder = os.path.join('data', 'text', 'reviews')

# أنشئ مجموعة من المراجعات بخصائص المعرف (اسم الملف) والنص (المحتويات)
reviews = []
for file_name in os.listdir(reviews_folder):
    review_text = open(os.path.join(reviews_folder, file_name)).read()
    review = {"id": file_name, "text": review_text}
    reviews.append(review)

for review_num in range(len(reviews)):
    # print the review text
    print('{}\n{}\n'.format(reviews[review_num]['id'], reviews[review_num]['text']))
```

## إنشاء مورد خدمات معرفية

لتحليل النص في هذه المراجعات، يمكنك استخدام خدمة **تحليلات النص** المعرفية. لاستخدام هذا، تحتاج إلى توفير إما مورد خدمات **تحليل النصوص** أو** خدمات معرفية** في اشتراك Azure الخاص بك (استخدم مورد تحليل النصوص إذا كانت هذه هي الخدمة الوحيدة التي تخطط لاستخدامها أو إذا كنت تريد متابعة استخدامها بشكل منفصل؛ وإلا يمكنك استخدام مورد الخدمات المعرفية لدمج خدمة تحليل النصوص مع الخدمات المعرفية الأخرى - مما يتيح للمطورين استخدام نقطة نهاية واحدة ومفتاح للوصول إليها.)

إذا لم يكن لديك واحد بالفعل، فاستخدم الخطوات التالية لإنشاء مورد **خدمات معرفية**في اشتراكك في Azure:

> **ملاحظة**: إذا كان لديك بالفعل مورد خدمات معرفية، فقط افتح صفحة **البدء السريع** الخاصة به في مدخل Azure وانسخ مفتاحه ونقطة النهاية إلى الخانة أدناه. خلاف ذلك، اتبع الخطوات أدناه لإنشاء واحدة.

1. في مستعرض آخر، افتح مدخل Azure على https://portal.azure.com، وقم بتسجيل الدخول باستخدام حساب Microsoft الخاص بك.
2. انقر فوق** زر إنشاء **&#65291; *مورد 65291، وابحث عن *خدمات معرفية**، وأنشئ مورد **خدمات معرفية بالإعدادات التالية:
    - **الاشتراك**: *اشتراكك في Azure.*
    - **مجموعة الموارد**: *حدد أو أنشئ مجموعة موارد باسم فريد*.
    - **المنطقة**: *اختر أي منطقة متوفرة:*
    - **الاسم:** *أدخل اسمًا فريدًا*.
    - **مستوى الأسعار**: S0
    - **أؤكد أنني قد قرأت وفهمت الإخطارات**: تم الاختيار.
3. انتظر حتى اكتمال النشر. ثم انتقل إلى مورد الخدمات المعرفية الخاص بك، وفي صفحة **نظرة عامة**، انقر على رابط لإدارة مفاتيح الخدمة. ستحتاج إلى نقطة النهاية والمفاتيح للاتصال بمورد الخدمات المعرفية من تطبيقات العميل.

### احصل على المفتاح ونقطة النهاية لمورد الخدمات المعرفية

لاستخدام مورد الخدمات المعرفية، تحتاج تطبيقات العميل إلى نقطة النهاية ومفتاح المصادقة:

1. في مدخل Azure، في صفحة **المفاتيح ونقطة النهاية** لمورد الخدمة المعرفية، انسخ **Key1** لموردك وقم بلصقه في الرمز أدناه، مع استبدال **YOUR_COG_KEY**.
2. انسخ **نقطة النهاية** لموردك وألصقها في الرمز أدناه، لتحل محل **YOUR_COG_ENDPOINT**.
3. قم بتشغيل الرمز في الخلية أدناه بالنقر فوق الزر <span style="color:green">&#9655;</span> الأخضر.


```python
cog_key = 'YOUR_COG_KEY'
cog_endpoint = 'YOUR_COG_ENDPOINT'

print('Ready to use cognitive services at {} using key {}'.format(cog_endpoint, cog_key))
```

## تحديد اللغة
لنبدأ بتحديد اللغة التي كُتبت بها هذه المراجعات.


```python
import os
from azure.cognitiveservices.language.textanalytics import TextAnalyticsClient
from msrest.authentication import CognitiveServicesCredentials

# احصل على عميل لمورد خدمة تحليلات النص المعرفية
text_analytics_client = TextAnalyticsClient(endpoint=cog_endpoint,
                                            credentials=CognitiveServicesCredentials(cog_key))

# حلل المراجعات التي قرأتها من مجلد / البيانات / المراجعات سابقًا
language_analysis = text_analytics_client.detect_language(documents=reviews)

# طباعة تفاصيل اللغة المكتشفة لكل مراجعة
for review_num in range(len(reviews)):
    # print the review id
    print(reviews[review_num]['id'])

    # Get the language details for this review
    lang = language_analysis.documents[review_num].detected_languages[0]
    print(' - Language: {}\n - Code: {}\n - Score: {}\n'.format(lang.name, lang.iso6391_name, lang.score))

    # Add the detected language code to the collection of reviews (so we can do further analysis)
    reviews[review_num]["language"] = lang.iso6391_name
```

## استخراج العبارات الأساسية

يمكنك الآن تحليل النص في مراجعات العملاء لتحديد العبارات الأساسية التي تعطي بعض الإشارات إلى نقاط الحديث الرئيسية.


```python
# # استخدم العميل والمراجعات التي قمت بإنشائها في خلية الكود السابقة للحصول على العبارات الأساسية
key_phrase_analysis = text_analytics_client.key_phrases(documents=reviews)

# اطبع العبارات الأساسية لكل مراجعة
for review_num in range(len(reviews)):
    # print the review id
    print(reviews[review_num]['id'])

    # Get the key phrases in this review
    print('\nKey Phrases:')
    key_phrases = key_phrase_analysis.documents[review_num].key_phrases
    # Print each key phrase
    for key_phrase in key_phrases:
        print('\t', key_phrase)
    print('\n')
```

يمكن أن تساعدك العبارات الأساسية على فهم أهم نقاط الحديث في كل تقييم. على سبيل المثال، يمكن أن تعطيك المراجعات التي تحتوي على عبارة "فريق عمل مفيد" أو "خدمة سيئة" إشارة إلى بعض الاهتمامات الرئيسية للعميل الذي أضاف المراجع.

## توجيه المشاعر

قد يكون من المفيد تصنيف المراجعات على أنها *إيجابية* أو* سلبية* بناءً على *درجة المشاعر*. ‏‫ويمكنك استخدام خدمة تحليل النص ‏‫للقيام بذلك.‬


```python
# استخدم العميل والمراجعات التي قمت بإنشائها مسبقًا للحصول على درجات المشاعر
sentiment_analysis = text_analytics_client.sentiment(documents=reviews)

# اطبع نتائج كل مراجعة
for review_num in range(len(reviews)):

    # Get the sentiment score for this review
    sentiment_score = sentiment_analysis.documents[review_num].score

    # classifiy 'positive' if more than 0.5, 
    if sentiment_score < 0.5:
        sentiment = 'negative'
    else:
        sentiment = 'positive'

    # print file name and sentiment
    print('{} : {} ({})'.format(reviews[review_num]['id'], sentiment, sentiment_score))
```

## استخراج العناصر المعروفة

*العناصر* هي الأشياء التي قد يتم ذكرها في النص الذي يشير إلى نوع من العناصر المفهومة بشكل عام. على سبيل المثال، موقع أو شخص أو تاريخ. لنفترض أنك مهتم بالتواريخ والأماكن المذكورة في المراجعات - يمكنك استخدام الرمز التالي للعثور عليها.


```python
# استخدم العميل والمراجعات التي قمت بإنشائها مسبقًا للحصول على عناصر مسماة
entity_analysis = text_analytics_client.entities(documents=reviews)

# اطبع نتائج كل مراجعة
for review_num in range(len(reviews)):
    print(reviews[review_num]['id'])
    # Get the named entitites in this review
    entities = entity_analysis.documents[review_num].entities
    for entity in entities:
        # Only get location entitites
        if entity.type in ['DateTime','Location']:
            link = '(' + entity.wikipedia_url + ')' if entity.wikipedia_id is not None else ''
            print(' - {}: {} {}'.format(entity.type, entity.name, link))
```

لاحظ أن بعض العناصر معروفة جيدًا بامتلاكها لصفحة ويكيبيديا مرتبطة، وفي هذه الحالة تعرض خدمة تحليلات النص عنوان URL لتلك الصفحة.

## معرفة المزيد

لمزيد من المعلومات حول خدمة تحليل النصوص، راجع [مستندات خدمة تحليل النصوص](https://docs.microsoft.com/azure/cognitive-services/text-analytics/)
