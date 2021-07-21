<div id="readme" class="Box-body readme blob js-code-block-container p-5 p-xl-6 gist-border-0" dir="rtl">
    <article class="markdown-body entry-content container-lg" itemprop="text"><table>
  <thead>
  <tr>
  <th>title</th>
  <th>permalink</th>
  <th>layout</th>
  </tr>
  </thead>
  <tbody>
  <tr>
  <td><div>تعليمات مستضافة عبر الإنترنت</div></td>
  <td><div>index.html</div></td>
  <td><div>home</div></td>
  </tr>
  </tbody>
</table>

# تمارين أساسيات Azure في الذكاء الاصطناعي

يحتوي هذا المستودع على تمارين معملية عملية لدورة Microsoft التدريبية [AI-900 *الذكاء الاصطناعي Microsoft Azure*](https://docs.microsoft.com/ar-sa/learn/certifications/courses/ai-900t00) والوحدات النمطية الذاتية في Microsoft Learn: [ابدأ باستخدام الذكاء الاصطناعي على Azure،](https://docs.microsoft.com/learn/paths/get-started-with-artificial-intelligence-on-azure/) [ وأنشئ نماذج توقعية بدون تعليمات برمجية باستخدام التعلم الآلي من Azure، ](https://docs.microsoft.com/ar-sa/learn/paths/create-no-code-predictive-models-azure-machine-learning/) [واستكشف الرؤية الحاسوبية في Microsoft Azure،](https://docs.microsoft.com/learn/paths/explore-computer-vision-microsoft-azure/) [واستكشف معالجة اللغة الطبيعية،](https://docs.microsoft.com/learn/paths/explore-natural-language-processing/) و[استكشف الذكاء الاصطناعي التحادثي.](https://docs.microsoft.com/learn/paths/explore-conversational-ai/). تم تصميم التمارين لمرافقة المواد التعليمية وتمكينك من التدرب على استخدام التقنيات التي يصفونها. 

لإكمال هذه التمارين، ستحتاج إلى اشتراك Microsoft Azure. إذا لم يزودك مدربك بواحد، فيمكنك التسجيل للحصول على نسخة تجريبية مجانية على [https://azure.microsoft.com](https://azure.microsoft.com).

{% assign labs = site.pages | where_exp:"page", "page.url contains '/instructions'" %}
| تمارين |
| ------- | 
{% for activity in labs  %}| [{{ activity.lab.title }}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}
