---
machine_translated: true
machine_translated_rev: 72537a2d527c63c07aa5d2361a8829f3895cf2bd
toc_priority: 40
toc_title: "\u06A9\u0627\u0631 \u0628\u0627 \u0631\u0634\u062A\u0647 \u0647\u0627"
---

# توابع برای کار با رشته {#functions-for-working-with-strings}

## خالی {#empty}

بازده 1 برای یک رشته خالی و یا 0 برای یک رشته غیر خالی.
نتیجه این نوع UInt8.
یک رشته در نظر گرفته شده است غیر خالی اگر شامل حداقل یک بایت, حتی اگر این یک فضا یا یک بایت پوچ است.
این تابع همچنین برای ارریس کار می کند.

## notEmpty {#notempty}

بازده 0 برای یک رشته خالی یا 1 برای یک رشته غیر خالی.
نتیجه این نوع UInt8.
این تابع همچنین برای ارریس کار می کند.

## طول {#length}

بازگرداندن طول یک رشته در بایت (نه در شخصیت, و نه در نقاط کد).
نتیجه این نوع UInt64.
این تابع همچنین برای ارریس کار می کند.

## طول 8 {#lengthutf8}

بازگرداندن طول یک رشته در نقاط کد یونیکد (نه در شخصیت), فرض کنید که رشته شامل مجموعه ای از بایت است که متن کد گذاری شده را تشکیل می دهند. اگر این فرض ملاقات نکرده است, این گرداند برخی از نتیجه (این یک استثنا پرتاب نمی کند).
نتیجه این نوع UInt64.

## _شروع مجدد {#char-length}

بازگرداندن طول یک رشته در نقاط کد یونیکد (نه در شخصیت), فرض کنید که رشته شامل مجموعه ای از بایت است که متن کد گذاری شده را تشکیل می دهند. اگر این فرض ملاقات نکرده است, این گرداند برخی از نتیجه (این یک استثنا پرتاب نمی کند).
نتیجه این نوع UInt64.

## _شخصیت شناسی {#character-length}

بازگرداندن طول یک رشته در نقاط کد یونیکد (نه در شخصیت), فرض کنید که رشته شامل مجموعه ای از بایت است که متن کد گذاری شده را تشکیل می دهند. اگر این فرض ملاقات نکرده است, این گرداند برخی از نتیجه (این یک استثنا پرتاب نمی کند).
نتیجه این نوع UInt64.

## پایین تر {#lower}

تبدیل نمادهای اسکی لاتین در یک رشته به حروف کوچک.

## بالارفتن {#upper}

تبدیل نمادهای اسکی لاتین در یک رشته به حروف بزرگ.

## لوراتف8 {#lowerutf8}

تبدیل یک رشته به حروف کوچک, فرض رشته شامل مجموعه ای از بایت که یک متن کد گذاری شده-8 را تشکیل می دهند.
این زبان را تشخیص نمی دهد. بنابراین برای ترکیه نتیجه ممکن است دقیقا درست باشد.
اگر طول توالی یونایتد-8 بایت برای مورد بالا و پایین تر از یک نقطه کد متفاوت است, نتیجه ممکن است برای این نقطه کد نادرست.
اگر رشته شامل مجموعه ای از بایت است که سخن گفتن نیست-8, سپس رفتار تعریف نشده است.

## یوتف8 {#upperutf8}

تبدیل یک رشته به حروف بزرگ, فرض رشته شامل مجموعه ای از بایت که یک متن کد گذاری شده-8 را تشکیل می دهند.
این زبان را تشخیص نمی دهد. بنابراین برای ترکیه نتیجه ممکن است دقیقا درست باشد.
اگر طول توالی یونایتد-8 بایت برای مورد بالا و پایین تر از یک نقطه کد متفاوت است, نتیجه ممکن است برای این نقطه کد نادرست.
اگر رشته شامل مجموعه ای از بایت است که سخن گفتن نیست-8, سپس رفتار تعریف نشده است.

## اسوالدیدوتف8 {#isvalidutf8}

بازده 1, اگر مجموعه ای از کلمه در ادامه متن معتبر است-8 کد گذاری, در غیر این صورت 0.

## تولدیدوتف8 {#tovalidutf8}

8 کاراکتر نامعتبر را جایگزین می کند `�` اطلاعات دقیق همه در حال اجرا در یک ردیف شخصیت نامعتبر را به یک شخصیت جایگزین فرو ریخت.

``` sql
toValidUTF8( input_string )
```

پارامترها:

-   input_string — Any set of bytes represented as the [رشته](../../sql-reference/data-types/string.md) شی نوع داده.

مقدار بازگشتی: معتبر یونایتد-8 رشته.

**مثال**

``` sql
SELECT toValidUTF8('\x61\xF0\x80\x80\x80b')
```

``` text
┌─toValidUTF8('a����b')─┐
│ a�b                   │
└───────────────────────┘
```

## تکرار {#repeat}

تکرار یک رشته را به عنوان چند بار به عنوان مشخص شده و concatenates تکراری ارزش به عنوان یک رشته است.

**نحو**

``` sql
repeat(s, n)
```

**پارامترها**

-   `s` — The string to repeat. [رشته](../../sql-reference/data-types/string.md).
-   `n` — The number of times to repeat the string. [اینترنت](../../sql-reference/data-types/int-uint.md).

**مقدار بازگشتی**

تک رشته ای که حاوی رشته است `s` تکرار `n` زمان. اگر `n` \< 1, تابع رشته خالی می گرداند.

نوع: `String`.

**مثال**

پرسوجو:

``` sql
SELECT repeat('abc', 10)
```

نتیجه:

``` text
┌─repeat('abc', 10)──────────────┐
│ abcabcabcabcabcabcabcabcabcabc │
└────────────────────────────────┘
```

## معکوس {#reverse}

معکوس رشته (به عنوان یک دنباله از بایت).

## معکوس کردن8 {#reverseutf8}

معکوس دنباله ای از نقاط کد یونیکد, فرض کنید که رشته شامل مجموعه ای از بایت به نمایندگی از یک متن گفته-8. در غیر این صورت, این کار چیز دیگری (این یک استثنا پرتاب نمی).

## format(pattern, s0, s1, …) {#format}

قالب بندی الگوی ثابت با رشته ذکر شده در استدلال. `pattern` یک الگوی فرمت پایتون ساده شده است. رشته فرمت شامل “replacement fields” احاطه شده توسط پرانتز فرفری `{}`. هر چیزی که در پرانتز موجود نیست در نظر گرفته شده است متن تحت اللفظی است که بدون تغییر به خروجی کپی شده است. اگر شما نیاز به شامل یک شخصیت بند در متن تحت اللفظی, این را می توان با دو برابر فرار: `{{ '{{' }}` و `{{ '}}' }}`. نام فیلد می تواند اعداد (با شروع از صفر) یا خالی (سپس به عنوان شماره نتیجه درمان می شوند).

``` sql
SELECT format('{1} {0} {1}', 'World', 'Hello')
```

``` text
┌─format('{1} {0} {1}', 'World', 'Hello')─┐
│ Hello World Hello                       │
└─────────────────────────────────────────┘
```

``` sql
SELECT format('{} {}', 'Hello', 'World')
```

``` text
┌─format('{} {}', 'Hello', 'World')─┐
│ Hello World                       │
└───────────────────────────────────┘
```

## الحاق {#concat}

رشته های ذکر شده در استدلال بدون جدا کننده را تصدیق می کند.

**نحو**

``` sql
concat(s1, s2, ...)
```

**پارامترها**

ارزش رشته نوع و یا رشته ثابت.

**مقادیر بازگشتی**

را برمی گرداند رشته ای که منجر به از الحاق استدلال.

اگر هر یک از مقادیر استدلال است `NULL`, `concat` بازگشت `NULL`.

**مثال**

پرسوجو:

``` sql
SELECT concat('Hello, ', 'World!')
```

نتیجه:

``` text
┌─concat('Hello, ', 'World!')─┐
│ Hello, World!               │
└─────────────────────────────┘
```

## همبسته {#concatassumeinjective}

مثل [الحاق](#concat) تفاوت این است که شما نیاز به اطمینان حاصل شود که `concat(s1, s2, ...) → sn` این برای بهینه سازی گروه توسط استفاده می شود.

تابع به نام “injective” اگر همیشه نتیجه های مختلف برای مقادیر مختلف استدلال می گرداند. به عبارت دیگر: استدلال های مختلف هرگز نتیجه یکسان عملکرد.

**نحو**

``` sql
concatAssumeInjective(s1, s2, ...)
```

**پارامترها**

ارزش رشته نوع و یا رشته ثابت.

**مقادیر بازگشتی**

را برمی گرداند رشته ای که منجر به از الحاق استدلال.

اگر هر یک از مقادیر استدلال است `NULL`, `concatAssumeInjective` بازگشت `NULL`.

**مثال**

جدول ورودی:

``` sql
CREATE TABLE key_val(`key1` String, `key2` String, `value` UInt32) ENGINE = TinyLog;
INSERT INTO key_val VALUES ('Hello, ','World',1), ('Hello, ','World',2), ('Hello, ','World!',3), ('Hello',', World!',2);
SELECT * from key_val;
```

``` text
┌─key1────┬─key2─────┬─value─┐
│ Hello,  │ World    │     1 │
│ Hello,  │ World    │     2 │
│ Hello,  │ World!   │     3 │
│ Hello   │ , World! │     2 │
└─────────┴──────────┴───────┘
```

پرسوجو:

``` sql
SELECT concat(key1, key2), sum(value) FROM key_val GROUP BY concatAssumeInjective(key1, key2)
```

نتیجه:

``` text
┌─concat(key1, key2)─┬─sum(value)─┐
│ Hello, World!      │          3 │
│ Hello, World!      │          2 │
│ Hello, World       │          3 │
└────────────────────┴────────────┘
```

## زیر رشته(بازدید کنندگان, انحراف, طول), اواسط(بازدید کنندگان, انحراف, طول), عام (بازدید کنندگان, انحراف, طول) {#substring}

بازگرداندن یک رشته شروع با بایت از ‘offset’ شاخص این است ‘length’ کلمه در ادامه متن طولانی. نمایه سازی شخصیت از یک شروع می شود (همانطور که در گذاشتن استاندارد). این ‘offset’ و ‘length’ استدلال باید ثابت باشد.

## زیر بغل کردن 8(بازدید کنندگان, انحراف, طول) {#substringutf8}

همان ‘substring’, اما برای نقاط کد یونیکد. این نسخهها کار میکند با این فرض که رشته شامل مجموعه ای از بایت به نمایندگی از یک متن کد گذاری شده وزارت مخابرات 8. اگر این فرض ملاقات نکرده است, این گرداند برخی از نتیجه (این یک استثنا پرتاب نمی کند).

## appendTrailingCharIfAbsent(s, c) {#appendtrailingcharifabsent}

اگر ‘s’ رشته غیر خالی است و حاوی نیست ‘c’ شخصیت در پایان این برنامه ‘c’ شخصیت به پایان.

## تبدیل(بازدید کنندگان, از, به) {#convertcharset}

بازگرداندن رشته ‘s’ که از رمزگذاری در تبدیل شد ‘from’ به رمزگذاری در ‘to’.

## کد زیر 64) {#base64encode}

کدگذاریها ‘s’ رشته به پایگاه64

## کد زیر 64) {#base64decode}

رمزگشایی پایگاه64-رشته کد گذاری شده ‘s’ به رشته اصلی. در صورت شکست را افزایش می دهد یک استثنا.

## تریباس64دسیدی) {#trybase64decode}

شبیه به حالت کد باس64, اما در صورت خطا یک رشته خالی می شود بازگشت.

## endsWith(s, پسوند) {#endswith}

بازگرداندن اینکه با پسوند مشخص شده پایان یابد. بازده 1 اگر رشته به پایان می رسد با پسوند مشخص, در غیر این صورت باز می گردد 0.

## startsWith(str, پیشوند) {#startswith}

بازده 1 اینکه رشته با پیشوند مشخص شروع می شود, در غیر این صورت باز می گردد 0.

``` sql
SELECT startsWith('Spider-Man', 'Spi');
```

**مقادیر بازگشتی**

-   1, اگر رشته با پیشوند مشخص شروع می شود.
-   0, اگر رشته با پیشوند مشخص شروع نشد.

**مثال**

پرسوجو:

``` sql
SELECT startsWith('Hello, world!', 'He');
```

نتیجه:

``` text
┌─startsWith('Hello, world!', 'He')─┐
│                                 1 │
└───────────────────────────────────┘
```

## تر و تمیز {#trim}

حذف تمام شخصیت های مشخص شده از شروع یا پایان یک رشته.
به طور پیش فرض حذف همه وقوع متوالی از فضای سفید مشترک (شخصیت اسکی 32) از هر دو به پایان می رسد از یک رشته.

**نحو**

``` sql
trim([[LEADING|TRAILING|BOTH] trim_character FROM] input_string)
```

**پارامترها**

-   `trim_character` — specified characters for trim. [رشته](../../sql-reference/data-types/string.md).
-   `input_string` — string for trim. [رشته](../../sql-reference/data-types/string.md).

**مقدار بازگشتی**

یک رشته بدون پیشرو و (یا) انتهایی شخصیت مشخص شده است.

نوع: `String`.

**مثال**

پرسوجو:

``` sql
SELECT trim(BOTH ' ()' FROM '(   Hello, world!   )')
```

نتیجه:

``` text
┌─trim(BOTH ' ()' FROM '(   Hello, world!   )')─┐
│ Hello, world!                                 │
└───────────────────────────────────────────────┘
```

## trimLeft {#trimleft}

حذف تمام رخدادهای متوالی از فضای سفید مشترک (شخصیت اسکی 32) از ابتدای یک رشته. این کار انواع دیگر از شخصیت های فضای سفید را حذف کنید (باریکه, فضای بدون استراحت, و غیره.).

**نحو**

``` sql
trimLeft(input_string)
```

نام مستعار: `ltrim(input_string)`.

**پارامترها**

-   `input_string` — string to trim. [رشته](../../sql-reference/data-types/string.md).

**مقدار بازگشتی**

یک رشته بدون پیشرو فضاهای سفید مشترک.

نوع: `String`.

**مثال**

پرسوجو:

``` sql
SELECT trimLeft('     Hello, world!     ')
```

نتیجه:

``` text
┌─trimLeft('     Hello, world!     ')─┐
│ Hello, world!                       │
└─────────────────────────────────────┘
```

## trimRight {#trimright}

حذف تمام رخدادهای متوالی از فضای سفید مشترک (شخصیت اسکی 32) از پایان یک رشته. این کار انواع دیگر از شخصیت های فضای سفید را حذف کنید (باریکه, فضای بدون استراحت, و غیره.).

**نحو**

``` sql
trimRight(input_string)
```

نام مستعار: `rtrim(input_string)`.

**پارامترها**

-   `input_string` — string to trim. [رشته](../../sql-reference/data-types/string.md).

**مقدار بازگشتی**

یک رشته بدون انتهایی فضاهای خالی مشترک.

نوع: `String`.

**مثال**

پرسوجو:

``` sql
SELECT trimRight('     Hello, world!     ')
```

نتیجه:

``` text
┌─trimRight('     Hello, world!     ')─┐
│      Hello, world!                   │
└──────────────────────────────────────┘
```

## اصلاح {#trimboth}

حذف تمام رخدادهای متوالی از فضای سفید مشترک (شخصیت اسکی 32) از هر دو به پایان می رسد از یک رشته. این کار انواع دیگر از شخصیت های فضای سفید را حذف کنید (باریکه, فضای بدون استراحت, و غیره.).

**نحو**

``` sql
trimBoth(input_string)
```

نام مستعار: `trim(input_string)`.

**پارامترها**

-   `input_string` — string to trim. [رشته](../../sql-reference/data-types/string.md).

**مقدار بازگشتی**

یک رشته بدون پیشرو و انتهایی فضاهای سفید مشترک.

نوع: `String`.

**مثال**

پرسوجو:

``` sql
SELECT trimBoth('     Hello, world!     ')
```

نتیجه:

``` text
┌─trimBoth('     Hello, world!     ')─┐
│ Hello, world!                       │
└─────────────────────────────────────┘
```

## CRC32(s) {#crc32}

بازگرداندن کنترلی از یک رشته, با استفاده از کروک-32-یی 802.3 چند جملهای و مقدار اولیه `0xffffffff` هشدار داده می شود

نتیجه این نوع UInt32.

## CRC32IEEE(s) {#crc32ieee}

را برمی گرداند کنترل از یک رشته, با استفاده از کروم-32-یی 802.3 چند جملهای.

نتیجه این نوع UInt32.

## CRC64(s) {#crc64}

بازده CRC64 کنترلی از یک رشته با استفاده از CRC-64-ECMA چند جملهای.

نتیجه این نوع UInt64.

[مقاله اصلی](https://clickhouse.tech/docs/en/query_language/functions/string_functions/) <!--hide-->
