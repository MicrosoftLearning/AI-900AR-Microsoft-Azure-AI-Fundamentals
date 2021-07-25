<div id="readme" class="Box-body readme blob js-code-block-container p-5 p-xl-6 gist-border-0" dir="rtl">
    <article class="markdown-body entry-content container-lg" itemprop="text"><h1><a id="user-content-تعرّف-بصري-على-الحروف" class="anchor" aria-hidden="true" href="#تعرّف-بصري-على-الحروف"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>تعرّف بصري على الحروف</h1>


![روبوت يقرأ جريدة](./images/ocr.jpg)

يتمثل أحد التحديات الشائعة في الرؤية الخاصة بالكمبيوتر في اكتشاف النص في صورة ما وتفسيره. غالبًا ما يشار إلى هذا النوع من المعالجة* بالتعرف على الأحرف* (OCR).

## استخدم خدمة الرؤية الخاصة بالكمبيوتر للبحث عن نصٍ في الصورة

توفر خدمة **الرؤية الحاسوبية المعرفية** دعمًا لمهام التعرف على الحروف، بما في ذلك:

- واجهة برمجة تطبيقات **OCR** التي يمكنك استخدامها لقراءة النص بلغات متعددة. يمكن استخدام واجهة برمجة التطبيقات هذه بشكل متزامن، وتعمل بشكل جيد عندما تحتاج إلى اكتشاف وقراءة جزء صغير من النص في صورة.
- واجهة برمجة تطبيقات **للقراءة **مُحسَّنة لقراءة المستندات الأكبر حجمًا. يتم استخدام واجهة برمجة التطبيقات هذه بشكل غير متزامن، ويمكن استخدامها لكل من النصوص المطبوعة والمكتوبة بخط اليد.

يمكنك استخدام هذه الخدمة عن طريق إنشاء إما مورد **رؤية حاسوبية** أو مورد **خدمات معرفية.**

إذا لم تكن قد قمت بذلك من قبل، قم بإنشاء مورد **خدمات معرفية** ضمن اشتراك Azure الخاص بك.

> **ملاحظة**: إذا كان لديك بالفعل مورد خدمات معرفية، فقط افتح صفحة **البدء السريع** الخاصة به في منصة Azure وانسخ مفتاحه ونقطة النهاية إلى الخلية أدناه. خلاف ذلك، اتبع الخطوات أدناه لإنشاء واحدة.

1. في علامة تبويب مستعرض أخرى، افتح مدخل Azure على https://portal.azure.com، وقم بتسجيل الدخول باستخدام حساب Microsoft الخاص بك.

2. انقر فوق** زر إنشاء **&#65291; *مورد 65291، وابحث عن *خدمات معرفية**، وأنشئ مورد **خدمات معرفية بالإعدادات التالية:
    - **الاشتراك**: *اشتراكك في Azure.*
    - **مجموعة الموارد**: *حدد أو أنشئ مجموعة موارد باسم فريد*.
    - **المنطقة**. *اختر أي منطقة متوفرة*:
    - **الاسم**: *أدخل اسمًا فريدًا*.
    - **مستوى الأسعار**: S0
    - **أؤكد أنني قد قرأت وفهمت الإخطارات**: تم الاختيار.
3. انتظر حتى اكتمال النشر. ثم انتقل إلى مورد الخدمات المعرفية الخاص بك، وفي صفحة **نظرة عامة**، انقر على رابط لإدارة مفاتيح الخدمة. ستحتاج إلى نقطة النهاية والمفاتيح للاتصال بمورد الخدمات المعرفية من تطبيقات العميل.

### احصل على المفتاح ونقطة النهاية لمورد الخدمات المعرفية

لاستخدام موارد الخدمات المعرفية، تحتاج تطبيقات العميل إلى نقطة النهاية ومفتاح المصادقة:

1. في مدخل Azure، في صفحة **المفاتيح ونقطة النهاية** لمورد الخدمة المعرفية، انسخ **Key1** لموردك وقم بلصقه في الرمز أدناه، مع استبدال **YOUR_COG_KEY**.
2. انسخ **نقطة النهاية** لموردك وألصقها في الرمز أدناه، لتحل محل **YOUR_COG_ENDPOINT**.
3. قم بتشغيل الكود في الخلية أدناه بالنقر فوق الزر **تشغيل الخانة** (&#9655;) (على يسار الخانة).


```python
cog_key = 'YOUR_COG_KEY'
cog_endpoint = 'YOUR_COG_ENDPOINT'

print('Ready to use cognitive services at {} using key {}'.format(cog_endpoint, cog_key))
```

الآن بعد أن قمت بإعداد المفتاح ونقطة النهاية، يمكنك استخدام مورد خدمة رؤية خاصةٍ بالكمبيوتر، وذلك لاستخراج نص من صورة.

لنبدأ بواجهة برمجة تطبيقات **التعرف على الحروف،** والتي تمكنك من تحليل صورة ما بشكل متزامن وقراءة أي نص تحتوي عليه. في هذه الحالة، لديك صورة إرشادية لشركة البيع بالتجزئة الخيالية Northwind Traders التي تتضمن بعض النصوص. قم بتشغيل الخلية أدناه لقراءتها.. 


```python
from azure.cognitiveservices.vision.computervision import ComputerVisionClient
from msrest.authentication import CognitiveServicesCredentials
import matplotlib.pyplot as plt
from PIL import Image, ImageDraw
import os
%matplotlib inline

# احصل على عميل لخدمة الرؤية الخاصة بالكمبيوتر
computervision_client = ComputerVisionClient(cog_endpoint, CognitiveServicesCredentials(cog_key))

# اقرأ ملف الصورة
image_path = os.path.join('data', 'ocr', 'advert.jpg')
image_stream = open(image_path, "rb")

# استخدم خدمة الرؤية الخاصة بالكمبيوتر للبحث عن نص في الصورة
read_results = computervision_client.recognize_printed_text_in_stream(image_stream)

# معالجة النص سطرًا بسطرٍ
for region in read_results.regions:
    for line in region.lines:

        # Read the words in the line of text
        line_text = ''
        for word in line.words:
            line_text += word.text + ' '
        print(line_text.rstrip())

# افتح الصورة لعرضها.
fig = plt.figure(figsize=(7, 7))
img = Image.open(image_path)
draw = ImageDraw.Draw(img)
plt.axis('off')
plt.imshow(img)
```

تم تنظيم النص الموجود في الصورة في هيكل هرمي للمناطق والخطوط والكلمات، ويقرأها الرمز لاسترداد النتائج.

في النتائج، اعرض النص الذي تمت قراءته أعلى الصورة. 

## عرض المربعات المحيطة

تتضمن النتائج أيضًا إحداثيات *المربع المحيط *لأسطر النص، والكلمات الفردية الموجودة في الصورة. قم بتشغيل الخلية أدناه لرؤية المربعات المحيطة لأسطر النص في صورة الإعلان التي قمت باستردادها أعلاه.


```python
# افتح الصورة لعرضها.
fig = plt.figure(figsize=(7, 7))
img = Image.open(image_path)
draw = ImageDraw.Draw(img)

# معالجة النص سطرًا بسطرٍ
for region in read_results.regions:
    for line in region.lines:

        # Show the position of the line of text
        l,t,w,h = list(map(int, line.bounding_box.split(',')))
        draw.rectangle(((l,t), (l+w, t+h)), outline='magenta', width=5)

        # Read the words in the line of text
        line_text = ''
        for word in line.words:
            line_text += word.text + ' '
        print(line_text.rstrip())

# اعرض الصورة مع تحديد مواقع النص
plt.axis('off')
plt.imshow(img)
```

في النتيجة، يظهر المربع المحيط لكل سطر من النص كمستطيل على الصورة.

## استخدم Read API

تعمل واجهة برمجة تطبيقات OCR التي استخدمتها سابقًا بشكل جيدٍ مع الصور التي تحتوي على كمية صغيرة من الكتابة النصية. عندما تحتاج إلى قراءة نصوص أكبر حجمًا، مثل المستندات الممسوحة ضوئيًا، يمكنك استخدام **واجهة برمجة التطبيقات للقراءة**. يتطلب هذا عملية متعددة الخطوات:

1. قم بإرسال صورة إلى خدمة الرؤية الخاصة بالكمبيوتر، لتتم قراءتها وتحليلها بشكل غير متزامن.
2. انتظر حتى تكتمل عملية التحليل.
3. استرجع نتائج التحليل.

قم بتشغيل الخانة التالية لاستخدام هذه العملية لقراءة النص في رسالة ممسوحة ضوئيًا إلى مدير متجر Northwind Traders.


```python
from azure.cognitiveservices.vision.computervision import ComputerVisionClient
from azure.cognitiveservices.vision.computervision.models import OperationStatusCodes
from msrest.authentication import CognitiveServicesCredentials
import matplotlib.pyplot as plt
from PIL import Image
import time
import os
%matplotlib inline

# اقرأ ملف الصورة
image_path = os.path.join('data', 'ocr', 'letter.jpg')
image_stream = open(image_path, "rb")

# احصل على عميل لخدمة الرؤية الخاصة بالكمبيوتر
computervision_client = ComputerVisionClient(cog_endpoint, CognitiveServicesCredentials(cog_key))

# أرسل طلبًا لقراءة النص المطبوع في الصورة والحصول على معرف العملية
read_operation = computervision_client.read_in_stream(image_stream,
                                                      raw=True)
operation_location = read_operation.headers["Operation-Location"]
operation_id = operation_location.split("/")[-1]

# انتظر حتى تكتمل العملية غير المتزامنة
while True:
    read_results = computervision_client.get_read_result(operation_id)
    if read_results.status not in [OperationStatusCodes.running]:
        break
    time.sleep(1)

# إذا كانت العملية ناجحة، قم بمعالجة النص سطراً بسطر
if read_results.status == OperationStatusCodes.succeeded:
    for result in read_results.analyze_result.read_results:
        for line in result.lines:
            print(line.text)

# افتح الصورة واعرضها.
print('\n')
fig = plt.figure(figsize=(12,12))
img = Image.open(image_path)
plt.axis('off')
plt.imshow(img)
```

معاينة النتائج يوجد نسخة كاملة للرسالة، والتي تتكون في الغالب من نصٍ مطبوعٍ بتوقيع خط اليد. تظهر الصورة الأصلية للحرف أسفل نتائج التعرف على الحروف (قد تحتاج إلى النزول أسفل الصفحة لرؤيتها).

## اقرأ النص المكتوب بخط اليد

في المثال السابق، حدد طلب تحليل الصورة وضع التعرف على النص الذي يعمل على تحسين عملية النص *المطبوع*. لاحظ أنه على الرغم من ذلك، فقد تمت قراءة التوقيع بخط اليد.

هذه القدرة على قراءة النص المكتوب بخط اليد مفيدة للغاية. على سبيل المثال، لنفترض أنك كتبت ملاحظة تحتوي على قائمة تسوق، وتريد استخدام تطبيق على هاتفك لقراءة الملاحظة وتدوين النص الذي تحتوي عليه.

قم بتشغيل الخلية أدناه لمشاهدة مثال لعملية القراءة لقائمة تسوق مكتوبة بخط اليد.


```python
from azure.cognitiveservices.vision.computervision import ComputerVisionClient
from azure.cognitiveservices.vision.computervision.models import OperationStatusCodes
from msrest.authentication import CognitiveServicesCredentials
import matplotlib.pyplot as plt
from PIL import Image
import time
import os
%matplotlib inline

# اقرأ ملف الصورة
image_path = os.path.join('data', 'ocr', 'note.jpg')
image_stream = open(image_path, "rb")

# احصل على عميل لخدمة الرؤية الخاصة بالكمبيوتر
computervision_client = ComputerVisionClient(cog_endpoint, CognitiveServicesCredentials(cog_key))

# أرسل طلبًا لقراءة النص المطبوع في الصورة والحصول على معرف العملية
read_operation = computervision_client.read_in_stream(image_stream,
                                                      raw=True)
operation_location = read_operation.headers["Operation-Location"]
operation_id = operation_location.split("/")[-1]

# انتظر حتى تكتمل العملية غير المتزامنة
while True:
    read_results = computervision_client.get_read_result(operation_id)
    if read_results.status not in [OperationStatusCodes.running]:
        break
    time.sleep(1)

# إذا كانت العملية ناجحة، قم بمعالجة النص سطرًا بسطر
if read_results.status == OperationStatusCodes.succeeded:
    for result in read_results.analyze_result.read_results:
        for line in result.lines:
            print(line.text)

# افتح الصورة واعرضها.
print('\n')
fig = plt.figure(figsize=(12,12))
img = Image.open(image_path)
plt.axis('off')
plt.imshow(img)
```

## المزيد من المعلومات

لمزيد من المعلومات حول استخدام خدمة الرؤية الخاصة بالكمبيوتر للتعرف على الحروف OCR، قم بمراجعة [مستندات الرؤية الحاسوبية](https://docs.microsoft.com/ar-sa/azure/cognitive-services/computer-vision/concept-recognizing-text)
