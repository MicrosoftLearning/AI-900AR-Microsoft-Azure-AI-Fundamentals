<div id="readme" class="Box-body readme blob js-code-block-container p-5 p-xl-6 gist-border-0" dir="rtl">
    <article class="markdown-body entry-content container-lg" itemprop="text"><h1><a id="user-content-الترجمة" class="anchor" aria-hidden="true" href="#الترجمة"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>الترجمة</h1>


إحدى القوى الدافعة التي مكّنت الحضارة الإنسانية من التطور هي القدرة على التواصل مع بعضها البعض. في معظم المساعي البشرية، التواصل هو المفتاح.

![روبوت متعدد اللغات!](./images/translation.jpg)

يمكن للذكاء الاصطناعي (AI) المساعدة في تبسيط الاتصال عن طريق ترجمة النص أو الكلام بين اللغات، مما يساعد على إزالة الحواجز أمام التواصل عبر البلدان والثقافات.

## إنشاء مورد خدمات معرفية

في Azure، يمكنك استخدام الخدمات المعرفية للتحويل بين لغات متعددة.

إذا لم يكن لديك واحد بالفعل، فاستخدم الخطوات التالية لإنشاء مورد **خدمات معرفية**في اشتراكك في Azure:

> **ملاحظة**: إذا كان لديك بالفعل مورد خدمات معرفية، فقط افتح صفحة** البدء السريع** الخاصة به في مدخل Azure وانسخ مفتاحه ونقطة النهاية إلى الخانة أدناه. خلاف ذلك، اتبع الخطوات أدناه لإنشاء واحدة.

1. في علامة تبويب مستعرض أخرى، افتح مدخل Azure على https://portal.azure.com، وقم بتسجيل الدخول باستخدام حساب Microsoft الخاص بك.
2. انقر فوق** زر إنشاء **&#65291; *مورد 65291، وابحث عن *خدمات معرفية**، وأنشئ مورد **خدمات معرفية بالإعدادات التالية:
    - **الاشتراك**: *اشتراكك في Azure.*.
    - **مجموعة الموارد**: *حدد أو أنشئ مجموعة موارد باسم فريد*.
    - **المنطقة**: *اختر أي منطقة متوفرة*:
    - **الاسم**: *أدخل اسمًا فريدًا*.
    - **مستوى الأسعار**: S0
    - **أؤكد أنني قد قرأت وفهمت الإخطارات**: تم الاختيار.
3. انتظر حتى اكتمال النشر. ثم انتقل إلى مورد الخدمات المعرفية الخاص بك، وفي صفحة **نظرة عامة**، انقر على رابط لإدارة مفاتيح الخدمة. ستحتاج إلى نقطة النهاية والمفاتيح للاتصال بمورد الخدمات المعرفية من تطبيقات العميل.

### احصل على المفتاح والموقع لمورد الخدمات المعرفية

لاستخدام مورد الخدمات المعرفية، تحتاج تطبيقات العميل إلى مفتاح المصادقة والموقع:

1. في مدخل Azure، في صفحة **المفاتيح ونقطة النهاية** لمورد الخدمة المعرفية، انسخ **Key1** لموردك وقم بلصقه في الرمز أدناه، مع استبدال **YOUR_COG_KEY**.
2. انسخ **الموقع** لموردك والصقه في الرمز أدناه، مع استبدال**YOUR_COG_LOCATION**.
**ملاحظة**: ابق في صفحة **المفاتيح ونقطة النهاية** وانسخ **الموقع** من هذه الصفحة (مثال: _westus_). يرجى عدم إضافة مسافات بين الكلمات في حقل الموقع. 
3. قم بتشغيل الرمز أدناه عن طريق النقر فوق زر **تشغيل الخلية** (&#9655;) الموجود على يسار الخلية.


```python
cog_key = 'YOUR_COG_KEY'
cog_location = 'YOUR_COG_LOCATION'

print('Ready to use cognitive services in {} using key {}'.format(cog_location, cog_key))
```

## ترجمة النص

كما يوحي اسمها، تتيح لك خدمة **ترجمة النصوص** تحويل النص من لغة إلى أخرى.

لا توجد Python SDK لهذه الخدمة، ولكن يمكنك استخدام واجهة REST لإرسال الطلبات إلى نقطة نهاية عبر HTTP، وهو أمر سهل نسبيًا في Python باستخدام مكتبة **الطلبات**. يتم تبادل المعلومات حول النص المراد ترجمته والنص المترجم الناتج بتنسيق JSON.

قم بتشغيل الخلية التالية لإنشاء وظيفة تقوم بذلك، ثم اختبر الوظيفة بترجمة بسيطة من الإنجليزية إلى الفرنسية.


```python
# قم بإنشاء وظيفة تقدم طلب REST إلى خدمة الترجمة النصية
def translate_text(cog_location, cog_key, text, to_lang='fr', from_lang='en'):
    import requests, uuid, json

    # Create the URL for the Text Translator service REST request
    path = 'https://api.cognitive.microsofttranslator.com/translate?api-version=3.0'
    params = '&from={}&to={}'.format(from_lang, to_lang)
    constructed_url = path + params

    # Prepare the request headers with Cognitive Services resource key and region
    headers = {
        'Ocp-Apim-Subscription-Key': cog_key,
        'Ocp-Apim-Subscription-Region':cog_location,
        'Content-type': 'application/json',
        'X-ClientTraceId': str(uuid.uuid4())
    }

    # Add the text to be translated to the body
    body = [{
        'text': text
    }]

    # Get the translation
    request = requests.post(constructed_url, headers=headers, json=body)
    response = request.json()
    return response[0]["translations"][0]["text"]


# اختبار التطبيقات
text_to_translate = "Hello"

translation = translate_text(cog_location, cog_key, text_to_translate, to_lang='fr', from_lang='en')
print('{} -> {}'.format(text_to_translate,translation))
```

يجب أن تكون الخدمة قد ترجمت النص الإنجليزي "Hello" إلى "Bonjour" الفرنسية.

لاحظ أن اللغات محددة باستخدام نظام معياري لاختصارات اللغة، مع* en* للغة الإنجليزية و*fr* للفرنسية. يمكنك أيضًا استخدام الاختصارات التي تتضمن ثقافات معينة، وهو أمر مفيد عند استخدام نفس اللغة في مناطق جغرافية مختلفة - غالبًا باستخدام تهجئات مختلفة. على سبيل المثال ، تشير* *en-US إلى اللغة الإنجليزية في الولايات المتحدة، بينما تشير *en-GB *إلى اللغة الإنجليزية في المملكة المتحدة.

قم بتشغيل الخانة التالية للترجمة بين الإنجليزية البريطانية والإيطالية.


```python
text_to_translate = "Hello"

translation = translate_text(cog_location, cog_key, text_to_translate, to_lang='it-IT', from_lang='en-GB')
print('{} -> {}'.format(text_to_translate,translation))
```

لنجرب ترجمة أخرى - هذه المرة من الإنجليزية الأمريكية إلى الصينية.


```python
text_to_translate = "Hello"

translation = translate_text(cog_location, cog_key, text_to_translate, to_lang='zh-CN', from_lang='en-US')
print('{} -> {}'.format(text_to_translate,translation))
```

## ترجمة الكلام

يمكنك استخدام خدمة **الكلام **لترجمة اللغة المنطوقة.

يمكنك الآن تشغيل الخانة التالية لإنشاء واختبار وظيفة تستخدم Speech SDK لتحويل الكلام المسموع.

> **ملاحظة**: ستحتاج إلى مكبرات صوت لتثبيت الصوت.


```python
from playsound import playsound 

# قم بإنشاء وظيفة لتحويل الصوت من لغة إلى نص بلغة أخرى
def translate_speech(cog_location, cog_key, audio_file=None, to_lang='fr-FR', from_lang='en-US'):
    from azure.cognitiveservices.speech import SpeechConfig, AudioConfig, ResultReason
    from azure.cognitiveservices.speech.translation import SpeechTranslationConfig, TranslationRecognizer

    # Configure the speech translation service
    translation_config = SpeechTranslationConfig(subscription=cog_key, region=cog_location)
    translation_config.speech_recognition_language = from_lang
    translation_config.add_target_language(to_lang)

    # Configure audio input
    if audio_file is None:
        audio_config = AudioConfig() # Use default input (microphone)
    else:
        audio_config = AudioConfig(filename=audio_file) # Use file input

    # Create a translation recognizer and use it to translate speech input
    recognizer = TranslationRecognizer(translation_config, audio_config)
    result = recognizer.recognize_once()

    # Did we get it?
    translation = ''
    speech_text = ''
    if result.reason == ResultReason.TranslatedSpeech:
        speech_text = result.text
        translation =  result.translations[to_lang]
    elif result.reason == ResultReason.RecognizedSpeech:
        speech_text = result.text
        translation =  'Unable to translate speech'
    else:
        translation = 'Unknown'
        speech_text = 'Unknown'

    # rturn the translation
    return speech_text, translation
    

# اختبار التطبيقات
import os

file_name = 'english.wav'
file_path = os.path.join('data', 'translation', file_name)
speech, translated_speech = translate_speech(cog_location, cog_key, file_path, to_lang='es', from_lang='en-US')
result = '{} -> {}'.format(speech, translated_speech)

# تشغيل الصوت وإظهار النص المترجم
playsound(file_path)
print(result)
```

لاحظ أنه يجب تحديد اللغة "إلى" باستخدام رمز لغة مكون من حرفين (على سبيل المثال *en)،* بينما يجب أن تتضمن اللغة "من" مؤشر الثقافة (على سبيل المثال *en-US*).

دعنا نحاول الترجمة من الفرنسية إلى الإنجليزية.


```python
from playsound import playsound
import os

file_name = 'french.wav'
file_path = os.path.join('data', 'translation', file_name)
speech, translated_speech = translate_speech(cog_location, cog_key, file_path, to_lang='en', from_lang='fr-FR')
result = '{} -> {}'.format(speech, translated_speech)

# تشغيل الصوت وإظهار النص المترجم
playsound(file_path)
print(result)
```

## معرفة المزيد

يمكنك معرفة المزيد حول [النص المترجم](https://docs.microsoft.com/azure/cognitive-services/translator/) والترجمة باستخدام [خدمة الكلام في مستند الخدمة](https://docs.microsoft.com/azure/cognitive-services/speech-service/index-speech-translation).
