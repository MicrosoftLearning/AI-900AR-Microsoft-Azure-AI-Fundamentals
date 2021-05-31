## التنمية المحلية 

إذا كنت تعمل على جهاز الكمبيوتر المحلي الخاص بك، يمكنك اتباع هذه الخطوات لتكوين بيئتك للعمل مع الأنشطة المعملية.  

### حزمة C++ Redistributable 
1. قم بتنزيل وتثبيت [Visual C++ Redistributable (x64)](https://aka.ms/vs/16/release/vc_redist.x64.exe) 

### Python والحزم المطلوبة 
1. قم بتثبيت [Python 3.6.1](https://www.python.org/downloads/release/python-361/)  
   - **هام**: حدد الخيارات لإضافة Python إلى متغير PATH والتسجيل كبيئة Python افتراضية 
2. بعد التثبيت، افتح *موجه الأوامر* وأدخل الأمر التالي لتثبيت الحزم الضرورية: 

> pip install ipython jupyter matplotlib pillow requests azure-cognitiveservices-vision-computervision azure-cognitiveservices-vision-customvision azure-cognitiveservices-vision-face azure-cognitiveservices-language-textanalytics azure.cognitiveservices.speech azure_ai_formrecognizer 

### تعليمة Visual Studio برمجية 
1. إذا لم يكن لديك تعليمة Visual Studio برمجية بالفعل، يرجى [تنزيلها من هنا]](https://code.visualstudio.com/Download). بعد التثبيت، ابدأ تشغيل تعليمة Visual Studio البرمجية ومن علامة تبويب الملحقات (CTRL + SHIFT + X)، ابحث عن ملحق **Python** من Microsoft وقم بتثبيته.

2. في تعليمة Visual Studio البرمجية، افتح وحدة طرفية جديدة، واكتب **git clone https://github.com/MicrosoftLearning/mslearn-ai900** وحدد *إدخال*. 

