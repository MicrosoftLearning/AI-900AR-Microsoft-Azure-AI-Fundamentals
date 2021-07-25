 <div id="readme" class="Box-body readme blob js-code-block-container p-5 p-xl-6 gist-border-0" dir="rtl">
    <article class="markdown-body entry-content container-lg" itemprop="text"><h2><a id="user-content-التنمية-المحلية" class="anchor" aria-hidden="true" href="#التنمية-المحلية"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>التنمية المحلية</h2>

       
إذا كنت تعمل على جهاز الكمبيوتر المحلي الخاص بك، يمكنك اتباع هذه الخطوات لتكوين بيئتك للعمل مع الأنشطة المعملية.  

### حزمة C++ Redistributable 
1. قم بتنزيل وتثبيت [Visual C++ Redistributable (x64)](https://aka.ms/vs/16/release/vc_redist.x64.exe) 

### Python والحزم المطلوبة 
1. قم بتثبيت [Python 3.6.1](https://www.python.org/downloads/release/python-361/)  
   - **هام**: حدد الخيارات لإضافة Python إلى متغير PATH والتسجيل كبيئة Python افتراضية 
2. بعد التثبيت، افتح *موجه الأوامر* وأدخل الأمر التالي لتثبيت الحزم الضرورية: 

> pip install ipython jupyter matplotlib pillow requests azure-cognitiveservices-vision-computervision azure-cognitiveservices-vision-customvision azure-cognitiveservices-vision-face azure-cognitiveservices-language-textanalytics azure.cognitiveservices.speech azure_ai_formrecognizer 

### تعليمة Visual Studio برمجية 
1. إذا لم يكن لديك تعليمة Visual Studio برمجية بالفعل، يرجى [تنزيلها من هنا](https://code.visualstudio.com/Download). بعد التثبيت، ابدأ تشغيل تعليمة Visual Studio البرمجية ومن علامة تبويب الملحقات (CTRL + SHIFT + X)، ابحث عن ملحق **Python** من Microsoft وقم بتثبيته.

2. في تعليمة Visual Studio البرمجية، افتح وحدة طرفية جديدة، واكتب **git clone https://github.com/MicrosoftLearning/AI-900AR-Microsoft-Azure-AI-Fundamentals** وحدد *إدخال*. 

