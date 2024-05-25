#نموذج مُدرب لتصنيف إشارات المرور 

#ملخص النموذج - Model Summary

هذا نموذج يستخدم لتصنيف إشارات المرور إلى 91 فئة مختلفة. يعتمد النموذج على معمارية موبايل_نت نسخة 2 وتم تدريبه باستخدام مجموعة بيانات جيدة تتضمن صورًا لإشارات المرور المختلفة. تم تقييم النموذج باستخدام بيانات الاختبار وأظهرت النتائج دقة جيدة في تصنيف الإشارات.
يمكن لهذا النموذج التعرف على إشارات المرور العربية والفرنسية والإنجليزية، مثلا علامة تشوير "قف" يمكن أن تتضمن: كلمة قف بالعربية فقط، كما يمكنها أن تتضمن نفس الكلمة مع مقابلها بالإنجليزية أو هما معا، أو الثلاثة معا أو واحدة من البقية لوحدها.

Traffic Signs Classification 91C is a model used to classify traffic signs into 91 different categories. The model is based on the MobileNetV2 architecture and has been trained using a dataset containing images of various traffic signs. The model has been evaluated using test data and has shown good accuracy in classifying the signs.
This model can recognize Arabic, French, and English traffic signs. For example, the “Stop” sign can include: the word “قف” in Arabic only. It can also include the same word and its equivalent in English, or both of them together, or all three together, or one of the rest alone.

اختبار 1:

![](https://www.googleapis.com/download/storage/v1/b/kaggle-user-content/o/inbox%2F7109735%2F9063772ee2a2c905eb88dd0a8802f229%2FScreenshot%20from%202024-05-23%2011-06-02.png?generation=1716458788581939&alt=media)

اختبار 2:

![](https://www.googleapis.com/download/storage/v1/b/kaggle-user-content/o/inbox%2F7109735%2F4cc933237aa358fb5c8695fb1a67f0b0%2FScreenshot%20from%202024-05-23%2011-10-03.png?generation=1716459121241181&alt=media)

## الاستخدام Usage

يمكن استخدام هذا النموذج لتصنيف إشارات المرور من خلال تحميل النموذج المدرب وتطبيقه على الصور الجديدة. يمكن استخدام الكود التالي لتحميل النموذج:
This model can be used to classify traffic signs by loading the trained model and applying it to new images. The following code can be used to load the model:

```python
import tensorflow as tf

# Load the .h5 model
model = tf.keras.models.load_model('mobilenet_multilabel150epoch.h5')

# Load the .tflite model
interpreter = tf.lite.Interpreter('mobilenet_multilabel150epoch.tflite')
interpreter.allocate_tensors()
```

###الشكل المدخل للنموذج هو صورة بأبعاد (224, 224, 3) والناتج هو مصفوفة من الاحتمالات لكل فئة من الفئات الـ 91.


## النظام System

هذا النموذج هو نموذج مستقل يمكن استخدامه لتصنيف إشارات المرور. المدخلات المطلوبة هي صور إشارات المرور والنواتج هي الفئات المتوقعة لكل صورة. يمكن استخدام النموذج في تطبيقات تتطلب تصنيف إشارات المرور مثل السيارات الذاتية القيادة وأنظمة مراقبة المرور.
This model is a standalone model that can be used for classifying traffic signs. The required inputs are images of traffic signs and the outputs are the predicted categories for each image. The model can be used in applications that require traffic sign classification such as autonomous driving systems and traffic monitoring systems.


## متطلبات التنفيذ Implementation requirements

تم تدريب النموذج باستخدام وحدة معالجة الرسوميات وحزمة تنسورفلو. تتطلب عملية التدريب عدة ساعات على وحدة معالجة الرسوميات القوية. يمكن تنفيذ النموذج على أي جهاز يدعم تشغيل تنسورفلو أو تنسورفلو لايت.
The model was trained using a GPU and TensorFlow framework. The training process takes several hours on a powerful GPU. The model can be deployed on any device that supports TensorFlow or TensorFlow Lite.

#  خصائص النموذج
##تهيئة النموذج
تم تدريب النموذج من الصفر باستخدام معمارية موبايل_نت وتحسينه باستخدام مجموعة بيانات إشارات المرور.

##إحصائيات النموذج
حجم النموذج هو حوالي 14 ميجابايت (.h5) و 6 ميجابايت (.tflite). يحتوي النموذج على حوالي 2 مليون معلمة موزعة على عدة طبقات.

##تفاصيل أخرى
النموذج غير مقلم وغير كمي.


##Model Characteristics

#Model initialization
The model was trained from scratch using the MobileNetV2 architecture and fine-tuned using the traffic sign dataset.

#Model stats
The size of the model is approximately 14 MB (.h5) and 6 MB (.tflite). The model contains around 2 million parameters distributed across several layers.

#Other details
The model is not pruned and not quantized.

#نظرة عامة على البيانات
##بيانات التدريب

تم تدريب النموذج باستخدام مجموعة بيانات تتضمن صورًا لإشارات المرور المختلفة. تم جمع البيانات من مصادر مختلفة وتمت معالجتها مسبقًا لتكون مناسبة للتدريب.

##مجموعات سكانية

تتضمن البيانات صورًا لإشارات المرور من بيئات ومناطق جغرافية مختلفة.

##بيانات التقييم
تم تقسيم البيانات إلى مجموعات تدريب واختبار وتحقق بنسبة 80/10/10. لا توجد اختلافات كبيرة بين بيانات التدريب والاختبار.


#Data Overview

##Training data

The model was trained using a dataset that includes images of various traffic signs. The data was collected from different sources and pre-processed to be suitable for training.

##Demographic groups
The data includes images of traffic signs from different environments and geographical regions.


##Evaluation data
The data was split into training, testing, and validation sets with a ratio of 80/10/10. There are no significant differences between the training and testing data.


#نتائج التقييم

##ملخص
أظهرت نتائج التقييم دقة عالية في تصنيف إشارات المرور. تم تقييم النموذج باستخدام مجموعة بيانات اختبار منفصلة.

##نتائج تقييم الفئات الفرعية
لم يتم إجراء تحليل تفصيلي للفئات الفرعية.

##الإنصاف
لم يتم تحديد مقاييس أو خطوط أساسية للإنصاف في هذا النموذج.

##حدود الاستخدام
يمكن أن تتأثر دقة النموذج بالصور ذات الجودة المنخفضة أو الإشارات غير المعتادة. يجب استخدام النموذج في بيئات ذات جودة صور عالية للحصول على أفضل النتائج.

##الأخلاقيات
تم أخذ العوامل الأخلاقية في الاعتبار أثناء تطوير النموذج. لم يتم تحديد أي مخاطر كبيرة.


#Evaluation Results

##Summary
The evaluation results showed high accuracy in classifying traffic signs. The model was evaluated using a separate test dataset.

##Subgroup evaluation results
No detailed subgroup analysis was performed.

##Fairness
No fairness metrics or baselines were defined for this model.

##Usage limitations
The model's accuracy can be affected by low-quality images or unusual signs. It should be used in environments with high-quality images for the best results.

##Ethics
Ethical factors were considered during the development of the model. No significant risks were identified.
