---
source-hash: 7e75b5e052216e2fd2c8684ffc936212758b2d1c0efb985a5c0f8ef838440750
sidebar_position: 18
title:  البرامج المساعدة
---
import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';
import AndroidStore from '@site/src/components/buttons/AndroidStore.mdx';
import AppleStore from '@site/src/components/buttons/AppleStore.mdx';
import LinksTelegram from '@site/src/components/_linksTelegram.mdx';
import LinksSocial from '@site/src/components/_linksSocialNetworks.mdx';
import Translate from '@site/src/components/Translate.js';
import InfoIncompleteArticle from '@site/src/components/_infoIncompleteArticle.mdx';
import InfoAndroidOnly from '@site/src/components/_infoAndroidOnly.mdx';

## نظرة عامة {#overview}

تُوسِّع البرامج المساعدة وظائف OsmAnd بشكل كبير. صُمِّمَ كل منها لمعالجة مهمة محددة أو حالة استخدام، مثل تسجيل رحلة، أو الوصول إلى مقالات ويكيبيديا دون اتصال بالإنترنت، أو تصور بيانات التضاريس، أو توفير عرض على مستوى الشارع.

يمكن أن تكون البرامج المساعدة داخلية، يتم تنشيطها في تطبيق OsmAnd، أو خارجية، برامج مُثبّتة بشكل منفصل. تعمل البرامج المساعدة التابعة لجهات خارجية من خلال واجهة برمجة تطبيقات OsmAnd ويمكنها الوصول إلى بيانات OsmAnd.

## تكوين البرنامج المساعد {#configure-plugin}

للوصول إلى وظائف البرنامج المساعد، يجب أولاً [تمكينه](#enable--disable)، وتتطلب بعض البرامج المساعدة [شراءً](#purchase) قبل الاستخدام. ثم، في بعض الحالات، يجب تنشيط طبقة خريطة محددة، أو يجب [تكوين](#plugin-settings) ملف تعريف مستخدم.

### تمكين / تعطيل {#enable--disable}

<Tabs groupId="operating-systems" queryString="current-os">

<TabItem value="android" label="أندرويد">

انتقل إلى: *<Translate android="true" ids="shared_string_menu,plugin_settings"/> ← ⚙️ ← تمكين*

![تمكين البرامج المساعدة أندرويد](@site/static/img/settings/plugins_enable_android.png) ![مثال على برنامج مساعد أندرويد](@site/static/img/settings/plugin_example_android.png)

</TabItem>

<TabItem value="ios" label="iOS">

انتقل إلى: *<Translate ios="true" ids="shared_string_menu,plugins_menu_group"/> ← ✓*

![تمكين البرامج المساعدة iOS](@site/static/img/settings/plugins_enable_ios.png) ![مثال على برنامج مساعد iOS](@site/static/img/settings/plugin_example_ios.png)

</TabItem>

</Tabs>

### الشراء {#purchase}

معظم البرامج المساعدة متاحة مجانًا، فقط البرامج المساعدة في القائمة أدناه تتطلب شراء ترخيص [OsmAnd+ أو OsmAnd Pro](../purchases/index.md) للاستخدام:

- [التضاريس](../plugins/topography.md)
- [الإغاثة ثلاثية الأبعاد](../plugins/topography.md#3d-relief) (ميزة من برنامج التضاريس المساعد)
- [ويكيبيديا](../plugins/wikipedia.md)
- [عرض الخريطة البحرية](../plugins/nautical-charts.md)
- [الطقس](../plugins/weather.md)

يمكن العثور على معلومات مفصلة حول شراء التطبيق في قسم [الشراء](../purchases/).

### ميزات البرنامج المساعد {#plugin-features}

قد تُعزز برامج OsmAnd المساعدة مجموعات الميزات التالية: **الطبقات**، **الأدوات**، **إجراءات قائمة السياق**، **إجراءات الدرج**، **نمط الخريطة**، **مصدر الخريطة**، **الملف الشخصي**.

🤖 - *فقط لإصدار أندرويد من OsmAnd.*

| اسم البرنامج المساعد | الميزات |
|:------------|:-------|
| [ويكيبيديا](#wikipedia) | [طبقة الخريطة](../plugins/wikipedia.md#download-wikipedia-packages)، [قائمة السياق](../plugins/wikipedia.md#wikipedia-languages) |
| [الخرائط عبر الإنترنت](#online-maps) | [طبقة الخريطة](../plugins/online-map.md#configure-map-source) |
| [تسجيل الرحلة](#trip-recording) | [الأداة](../plugins/trip-recording.md#widgets)، [الملف الشخصي](../plugins/trip-recording.md#profile-settings) |
| [التضاريس](#topography) | [طبقة الخريطة](../plugins/topography.md#hillshade-slope-and-altitude-layers) |
| [الإغاثة ثلاثية الأبعاد](#topography) 🤖 | [طبقة الخريطة](../plugins/topography.md#3d-relief) |
| [الطقس](../plugins/weather.md) | [طبقة الخريطة](../plugins/weather.md#display-weather-on-the-map)، [الأداة](../plugins/weather#weather-widgets)، [الشاشة](../plugins/weather.md#configure-screen) |
| [عرض الخريطة البحرية](#nautical-map-view) | [نمط الخريطة](../plugins/nautical-charts.md#nautical-map-style)، [الملف الشخصي](../plugins/nautical-charts.md#nautical-options) |
| [عرض خريطة التزلج](#ski-map-view) | [نمط الخريطة](../plugins/ski-maps.md#set-winter-style)، [الملف الشخصي](../plugins/ski-maps.md#skiing-profile) |
| [ملاحظات الصوت/الفيديو](#audiovideo-notes) 🤖 | [طبقة الخريطة](../plugins/audio-video-notes.md#show-all-on-the-map)، [قائمة السياق](../plugins/audio-video-notes.md#create)، [الأداة](../plugins/audio-video-notes.md#recording-widget) |
| [تحرير OpenStreetMap](#openstreetmap-editing) | [طبقة الخريطة](../plugins/osm-editing.md#how-to-use) |
| [موقف السيارة](#parking-position) | [قائمة السياق](../plugins/parking.md#set-a-point)، [الأداة](../plugins/parking.md#parking-widget) |
| [مابيلاري](#mapillary) | [طبقة الخريطة](../plugins/mapillary.md#map-layer)، [قائمة السياق](../plugins/mapillary.md#map-context-menu)، [الأداة](../plugins/mapillary.md#mapillary-widget) |
| [المستشعرات الخارجية](#external-sensors) 🤖 | [الأداة](../plugins/external-sensors.md#widgets) |
| [إمكانية الوصول](#accessibility) 🤖 | [إعدادات مخصصة](../plugins/accessibility.md#plugin-settings) |
| [تطوير OsmAnd](#osmand-development) | [إعدادات مخصصة](../plugins/development.md#plugin-settings) |
| [متتبع OsmAnd](#osmand-tracker) 🤖 | [طبقة الخريطة](../plugins/osmand-tracker.md#active-marker-on-the-osmand-map)، [الأداة](../plugins/osmand-tracker.md#osmand-tracker-widget)، [قائمة السياق](../plugins/osmand-tracker.md#active-marker-on-the-osmand-map) |
| [متتبع سفن AIS](#ais-vessel-tracker) 🤖 | [إعدادات مخصصة](../plugins/ais-tracker.md#plugin-settings) |

### إعدادات البرنامج المساعد {#plugin-settings}

:::caution ملاحظة
يُغيّر برنامج تطوير OsmAnd المساعد وبرنامج تحرير OSM المساعد الإعدادات لجميع الملفات الشخصية فقط. تُكوّن البرامج المساعدة المتبقية لكل ملف شخصي على حدة.
:::

توفر معظم البرامج المساعدة إعدادات ملف شخصي أو إعدادات عامة محددة، والتي يمكن الوصول إليها عبر:

- *القائمة الرئيسية ← البرامج المساعدة ← اسم البرنامج المساعد ← الإعدادات (⚙️ لنظام iOS)* أو
- *القائمة الرئيسية ← الإعدادات ← الملف الشخصي ← [إعدادات البرنامج المساعد](../personal/profiles.md#plugin-settings)*.

<Tabs groupId="operating-systems" queryString="current-os">

<TabItem value="android" label="أندرويد">

![إعدادات البرنامج المساعد أندرويد 1](@site/static/img/plugins/development/access_plugin_settings_andr_2.png) ![إعدادات البرنامج المساعد أندرويد 2](@site/static/img/plugins/development/access_plugin_settings_andr_1.png)

</TabItem>

<TabItem value="ios" label="iOS">

![إعدادات البرنامج المساعد iOS 1](@site/static/img/plugins/development/access_plugin_settings_ios_2.png) ![إعدادات البرنامج المساعد iOS 2](@site/static/img/plugins/development/access_plugin_settings_ios_1.png)

</TabItem>

</Tabs>

توفر البرامج المساعدة التالية إعداداتها الخاصة:

🤖 - *فقط لإصدار أندرويد من OsmAnd.*

| اسم البرنامج المساعد | الإعدادات |
|:------------|:-------|
| [تسجيل الرحلة](#trip-recording) | تكوين [أوضاع تشغيل](../plugins/trip-recording.md#recording-parameters) تسجيل الرحلة |
| [الطقس](#weather) | تكوين وحدات القياس لعرض أحداث الطقس |
| [ملاحظات الصوت/الفيديو](#audiovideo-notes) 🤖 | تحديد [تنسيق الفيديو، مدة التخزين، إلخ.](../plugins/audio-video-notes.md#plugin-settings) |
| [تحرير OpenStreetMap](#openstreetmap-editing) | تحديد [اسم المستخدم](../plugins/osm-editing.md#plugin-settings) |
| [المستشعرات الخارجية](#external-sensors) 🤖 | الاتصال بجهاز خارجي [الإعدادات](../plugins/external-sensors.md#settings) |
| [إمكانية الوصول](#accessibility) 🤖 | [الإعدادات](../plugins/accessibility.md#plugin-settings) تسمح لك باستخدام [ميزات أندرويد لإمكانية الوصول](https://www.android.com/accessibility/) داخل OsmAnd. |
| [تطوير OsmAnd](#osmand-development) | [إعدادات البرنامج المساعد](../plugins/development.md#plugin-settings) تسمح لك بتمكين ميزات خاصة للمطورين أو المستخدمين ذوي الخبرة |
| [متتبع OsmAnd](#osmand-tracker) 🤖 | جميع الإعدادات قابلة للتكوين في تطبيق منفصل |
| [متتبع سفن AIS](#ais-vessel-tracker) | [إعدادات البرنامج المساعد](../plugins/ais-tracker.md#plugin-settings) تسمح لك بتمكين إعدادات خاصة |

### إجراءات البرنامج المساعد {#plugin-actions}

**<Translate android="true" ids="reset_plugin_to_default"/>** - *باستخدام هذا الخيار يمكن إعادة تعيين إعدادات البرنامج المساعد إلى القيم الافتراضية*.
**<Translate android="true" ids="copy_from_other_profile"/>** - *يمكن نسخ إعدادات البرنامج المساعد من ملف تعريف آخر*.

## قائمة البرامج المساعدة {#plugins-list}

### [ويكيبيديا](./wikipedia.md) {#wikipedia}

يساعدك وجود ويكيبيديا في رحلتك على معرفة المزيد عن الأماكن التي تزورها. وهي متاحة دون اتصال بالإنترنت وتُظهر مقالات ويكيبيديا المتعلقة بنقاط الاهتمام مباشرة على الخريطة.

### [الخرائط عبر الإنترنت](./online-map.md) {#online-maps}

تُعد خرائط OsmAnd عبر الإنترنت إضافة واسعة النطاق لقاعدة بيانات OpenStreetMap الموجودة بالفعل في التطبيق. باستخدام هذا البرنامج المساعد، يمكنك إضافة طبقات إلى خريطتك بمعلومات من مصادر مختلفة.

### [تسجيل الرحلة](./trip-recording.md) {#trip-recording}

لروي قصة الأماكن التي زرتها، يمكن تسجيل بيانات GPS، مثل خطوط الطول والعرض لموقعك، وتخزينها في ملف، ثم إعادة استخدامها، وتحسينها، وتعزيزها بنقاط الطريق، وتوفيرها للملاحة، ومشاركتها مع الأصدقاء، وما إلى ذلك.

### [التضاريس](./topography.md) {#topography}

تساعد معلومات التضاريس، مثل خطوط الكنتور، وتظليل التلال، والانحدار، والإغاثة ثلاثية الأبعاد، في إجراء تقييم بصري لتضاريس الأرض من خلال رؤية الارتفاع، والإغاثة، والظواهر القصوى، والانحدار، ونقاط الارتفاع المتساوية، وما إلى ذلك.

### [عرض الخريطة البحرية](./nautical-charts.md) {#nautical-map-view}

يوفر عرض الخريطة البحرية تمثيلاً رسوميًا مفصلاً للمحيطات والبحار والمناطق الساحلية والأنهار لمساعدتك في التنقل على الماء، ورؤية طرق المرور الشائعة، والعوائق في المجرى المائي، والموانئ، ومناطق الرسو، وغيرها من المراجع الأساسية.

### [عرض خريطة التزلج](./ski-maps.md) {#ski-map-view}

يُظهر عرض خريطة التزلج الألوان الشتوية ومسارات التزلج المنحدرة أو عبر البلاد، بالإضافة إلى التلفريك، ومصاعد الكراسي، والمرافق والخدمات القريبة، وهو مفيد للتنقل في الوجهات مثل مناطق الترفيه، ومنتجعات التزلج، ومنتزهات التضاريس.

### [ملاحظات الصوت/الفيديو](./audio-video-notes.md) {#audiovideo-notes}

أنشئ ملاحظات صوتية/فيديو للرجوع إليها مستقبلاً، على سبيل المثال لتذكر حدث أو مشهد أو تفاعل. تتوفر ملاحظات الصوت/الفيديو التي تم إنشاؤها من *أماكني* وكذلك على الخريطة كطبقة فردية من القصص والأفكار التي صنعها المستخدمون والمرتبطة بموقع جغرافي. لأندرويد فقط.

### [موقف السيارة](./parking.md) {#parking-position}

حدد نقطة على الخريطة حيث تُركت سيارتك في الشارع وأبلغ تقويمك عند انتهاء وقت وقوف السيارة. سيجعل هذا تتبع وقت وموقع سيارتك أسهل.

### [تحرير OpenStreetMap](./osm-editing.md) {#openstreetmap-editing}

يسمح لك برنامج تحرير OpenStreetMap المساعد بالمساهمة في OpenStreetMap، وهو مجتمع عالمي ينشئ خريطة شاملة للعالم ويوفر بيانات مفتوحة المصدر حديثة ومتاحة للجمهور.

### [مابيلاري](./mapillary.md) {#mapillary}

شاهد مناظر على مستوى الشارع لطرقك أو أماكن اهتمامك، مقدمة من [مابيلاري](https://www.mapillary.com/) (يتطلب اتصالاً بالإنترنت).

### [إمكانية الوصول](./accessibility.md) {#accessibility}

يجعل برنامج إمكانية الوصول المساعد ميزات إمكانية الوصول بالجهاز متاحة مباشرة في OsmAnd. لأندرويد فقط.

### [المستشعرات الخارجية](./external-sensors.md) {#external-sensors}

وصل المستشعرات الخارجية لعرض بياناتها في OsmAnd وتخزين المعلومات في تسجيلات المسار.

### [مقاييس المركبات](./vehicle-metrics.md) {#vehicle-metrics}

وصل ماسح OBD-II لعرض بيانات المركبة في OsmAnd وتخزين المعلومات في تسجيلات المسار.

### [الطقس](./weather.md) {#weather}

يعرض التوقعات كل ساعة لليوم الحالي ولمدة 7 أيام قادمة.

### [تطوير OsmAnd](./development.md) {#osmand-development}

يستهدف برنامج تطوير OsmAnd المساعد المطورين والمستخدمين ذوي الخبرة. يسمح لك بمحاكاة مسارات الملاحة، والتحقق من أداء عرض الشاشة، وما إلى ذلك.

### [متتبع OsmAnd](./osmand-tracker.md) {#osmand-tracker}

يساعدك متتبع OsmAnd على رؤية مكان جهات اتصالك على الخريطة في OsmAnd. لأندرويد فقط.

### [متتبع سفن AIS](./ais-tracker.md) {#ais-vessel-tracker}

يعرض مواقع AIS ومعلومات حول السفن المحيطة. تُستقبل بيانات AIS عبر الشبكة من جهاز استقبال AIS خارجي.

## [إنشاء برنامج مساعد مخصص](./custom.md) {#create-a-custom-plugin}

يمكنك إنشاء برنامج مساعد خاص بك باتباع مقال *الحزمة المخصصة*.

_______

> *آخر تحديث: مارس 2025*