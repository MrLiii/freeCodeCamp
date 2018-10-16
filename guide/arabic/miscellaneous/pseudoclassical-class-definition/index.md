---
title: Pseudoclassical Class Definition
localeTitle: الطبقة الطبقية الكاذبة
---
يحدث تعريف الفئة pseudoclassical في 2 كتل رمز بدلا من واحد ، والذي يحدث في لغات أخرى مثل Python و PHP.

يسمى الكتلة الأولى "دالة منشئ" حيث يتم تعريف سمات الفئة. هذه هي جوانب الفصل الفريدة لكل مثيل جديد. مثال مع السيارات هو أن العلامة التجارية واللون والمكان يمكن أن تختلف. في الكتلة الثانية من التعليمات البرمجية التي تقوم بتعريف الطرق التي سيتم مشاركتها بواسطة كل مثيل للفئة. من الأمثلة على ذلك الأشياء التي يمكن أن تقوم بها السيارة ، القيادة إلى الأمام ، التوقف ، فتح الباب.

## مثال

 `var Car = function(brand, color, location) { 
 this.brand = brand; 
 this.color = color; 
 this.location = location 
 }; 
 
 Car.prototype = { 
 move: function() { this.location++; }, 
 stop: function() { this.location = 0; }, 
 }; 
` 

## تفسير

السبب في تعريف الفئة بالكامل في كتل 2 هو حفظ على الذاكرة عند بدء تشغيل مثيلات الفئة. إذا كان تعريف الفئة نمطًا "وظيفيًا" ، فهناك نسخة جديدة من الطريقة (الطرق) التي تم إجراؤها **لكل** مثيل. من خلال التصريح عن نمط "Pseudoclassical" للفئة يتم تخزين نسخة _واحدة_ فقط من الأساليب في الذاكرة.

عندما يحاول مثيل الطبقة الوصول إلى طريقة:

 `var x_car = new Car('lexus', 'white', 0); 
 x_car.move(); 
` 

في الواقع يفشل المترجم _أولاً_ في العثور على الأسلوب المدعو في الكائن نفسه حيث إنه مصنوع من دالة منشئ السيارة. كما ترى أعلاه لا يوجد أي إشارة إلى أي من الطرق في وظيفة منشئ السيارة. من هناك ، يبحث المترجم إلى `Car.prototype` والذي تتم مشاركته الآن بين جميع الحالات. هناك يجد المترجم الطريقة التي كانت تسمى!

### قراءة متعمقة:

[مدونة ناتاك](https://natacseanc.wordpress.com/2015/08/04/javascript-object-create-and-classes/)

[فئات MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Introduction_to_Object-Oriented_JavaScript)