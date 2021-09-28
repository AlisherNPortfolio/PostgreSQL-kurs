# SQL va PostgreSQL kursi

### 1- dars. Asosiy tushunchalar

Ma'lumotlar bazasi (MB) nima?

> MB - bu qandaydir darajada o'zaro bog'langan va biror saqlovchida saqlanadigan ma'lumotlar to'plami.

Masalan, MB biror bir txt, sql yoki json qisqartmali faylda saqlanishi mumkin.

Odatda, ma'lumotlarni biror saqlovchida shunchaki saqlanib turishidan bizga foyda yo'q. Biz ular ustida amal bajarib o'zimizga kerakli bo'lgan ma'lumotni olishimiz, o'chirishimiz, o'zgartirishimiz yoki yangi ma'lumotni unda saqlashimiz kerak bo'ladi. Bu amallarni esa to'g'ridan to'g'ri qo'lda qilib bo'lmaydi. Buning uchun biz **ma'lumotlar bazasini boshqarish tizimi**dan (ing, **Database Management System** - **DBMS** - **MBBT**) foydalanamiz.

MBBT MB-dagi ma'lumotlarni boshqarish MB tilidan foydalanadi (kursda `SQL` tilini ishlatamiz).

Amaliyotga o'tishdan avval biroz nazariya ham o'tib ketaylik.

MBBT-ning bir qancha turlari mavjud:

* **Fayl-serverli**: Microsoft Access
* **Kliyent-server**: MySQL, PostgreSQL, ...
* **Ichki o'rnatilgan (Built-in)**: SQLite

**Fayl-serverli** MBBT-larda MB markazlashgan fayl-serverda joylashadi. Ma'lumotlarni boshqarish kliyent kompyuterlaridan turib amalga oshiriladi. Bu turdagi MBBT-ning afzalligi, u fayl tizimiga katta yuklanish tashlamaydi. Kamchiligi esa, lokal tarmoqqa yuklanish tushirishidir. Shu sababli, u ishonchlilik, xavfsizlik, har doim murojaat qila bilish imkoniyatlarida muammoga duch kelishi mumkin.

Yuqorida keltirilgan kamchiliklar sababli, fayl-serverli MBBT yuqori yuklanishda ishlay olmaydi.

**Kliyent-server**li MBBT-da MB va MBBT serverda joylashadi. Ularni kliyent tomonidan masofadan turib boshqarish imkoni mavjud bo'ladi. Kliyent tomonidan berilgan so'rovlar MBBT tomonida ishga tushiriladi.

Hozirda kliyent-serverli MBBT-lar eng ko'p ishlatiladigan MBBT turi hisoblanadi. Chunki, bu turdagi MBBT yuqori yuklanishda katta hajmdagi ma'lumotlar bilan yaxshi ishlay oladi. Bundan tashqari, u ishonchli va ancha xavfsiz ham.

Lekin, kliyent-server MBBT-larning ham kamchiligi bor. Bu ularni barcha qurilmalarga ham o'rnatib, ishlatib bo'lmasligidir. Chunki, ba'zi qurilmalarda xotira hajmi kichik, protsessori kuchsiz bo'lishi mumkin. Bunday holatlarda esa bizga ichki o'rnatilgan MBBT-lar qo'l keladi.

**Ichki o'rnatilgan** MBBT. Ayrim hollarda, qurilmalar ishlash tezligini oshirish uchun yoki boshqa sabab tufayli katta hajmli MB-ning kichik bir qismini o'zida saqlab turishi kerak bo'ladi. Aynan shu holatlarda ichki o'rnatilgan MBBT-dan foydalaniladi.

Kursimizda Kliyent-serverli MBBT-ni o'rganamiz. Kliyent-serverli MBBT-larga misol qilib quyidagilarni keltirish mumkin:

* MySQL
* PostgreSQL
* Oracle
* MS SQL

Bu MBBT-larning barchasi **relatsion MBBT** bo'lib, ularning barchasi SQL (Structured Query Language) tilidan foydalanadi.

Relatsion MBBT-lar paydo bo'lishidan oldin relatsion bo'lmagan MBBT-lar (m: iyerarxik) ishlatilgan. 1970-yillarga kelib, relatsion MBBT-lar paydo bo'ldi. 2010-yillarga kelib esa matematik izlanishlar natijasida zamnaviy relatsion bo'lmagan MBBT-lar yaratildi. Google kompaniyasi o'zining qidirish tizimida ishlatgan algoritmlari yordamida ancha samarali bo'lgan MBBT yaratish mumkinligini ko'rsatdi.  Yangi turdagi MBBT-da SQL tili ishlatilmadi. Shu sababli uning nomi **NoSQL** deb nomlandi. `MongoDB` MBBT-ni NoSQL MBBT turiga misol qilib keltirish mumkin. MongoDB MBBT json ko'rinishiga o'xshash ko'rinishda saqlanuvchi ma'lumotlar bilan ishlaydi.

Relatsion MBBT-ni relatsion bo'lmagan MBBT-dan ustunlik yoki kamchilik joyi yo'q va aksincha. Ikkala turdagi MBBT-ning o'zining afzalligi va kamchiligiga qarab ishlatiladigan joyi bor.

### 2-dars. Relatsion model va SQL.

Relatsion MBBT-ning asosini relatsion algebra tashkil qiladi. Relatsion algebrani maktabda ham, institutda ham o'tmaganmiz. Relatsion algebraning paydo bo'lganiga unchalik ko'p vaqt ham bo'lgani yo'q (taxminan, 70-yillarda). 

Relatsion algebra munosabatlar (jadvallar) o'rtasida amallar bajarishni belgilab beradi: birlashtirish, kesishish, ayirish, bog'lash va shu kabi amallar. Bu amallarning barchasi SQL tili yordamida bajariladi.

Albatta, kursda relatsion algebraning o'zi o'tilmaydi).

Relatsion MBBT-da ba'zi tushunchalar.

* Jadval - munosabat
* Ustun - atribut
* Qator - yozuv (record)
* Natijaviy to'plam - SQL so'rov natijasi. M: `SELECT phone, address FROM users LIMIT 10`

**SQL - Structured Query Language.**

SQL - bu protsedurali yoki umumiy maqsadli til emas. SQL yordamida biror dastur, o'yin yoza olmaymiz. U MB-da ma'lumotlar ustida amal bajarishda ishlatiladi. SQL-ni ishlatish uchun boshqa biror bir dasturlash tili kerak bo'ladi. M: Python, C#, Java va h.k.

SQL tili turli tipdagi so'rovlardan tashkil topgan:

* DDL (Data Defenition Language) - CREATE, ALTER, DROP
* DML (Data Manipulation Language) - SELECT, INSERT, UPDATE, DELETE
* TCL (Transaction Control Language) - COMMIT, ROLLBACK, SAVEPOINT
* DCL (Data Control Language) - GRANT, REVOKE, DENY

Barcha SQL ishlatuvchi MBBT-lar o'zining SQL dialektiga ega. Ya'ni turli MBBT-larda har xil ko'rinishda SQL so'rov ishlatilishi mumkin (lekin asosiy so'rovlar bir xil. 90% SQL so'rovlar barcha MBBT-larda deyarli bir xil sintaksisda ishlatiladi.). Lekin, barcha MBBT-lar **ANSI SQL-92** standartida ishlaydi.

Turli MBBT-larda ishlatiluvchi SQL dialektlar:

* **PL/pgSQL** - PostgreSQL
* **PL/SQL** - Oracle
* **T-SQL** - MS SQL

### 3-dars. Nega PostgreSQL-dan foydalanish kerak?

PostgreSQL-ning afzalliklari

* **Tekin** (Open Source)
* O'rnatish va o'rganish uchun oson
* Tranzaksiyali MBBT hisoblanadi (MySQL-da tranzaksiylalilik bilan muammolar mavjud).
* Doimiy rivojlanishda
* MySQL bilan solishtirganda o'zining afzallik va kamchiliklari bor.
* Har qanday holatda, SQL dialektikasi 90% da boshqa MBBT-larga mos keladi.

### 4-dars. PostgreSQL-ni o'rnatish.

[PostgreSQL](https://www.postgresql.org/https://)-ning rasmiy saytiga o'tilib, [download](https://www.postgresql.org/download/https://) tugmasi bosiladi. Kerakli operatsion tizimni tanlab yuklab olish sahifasiga o'tiladi. So'ng [Download the installer](https://www.enterprisedb.com/downloads/postgres-postgresql-downloadshttps://) havolasi bosiladi. Ochilgan oynadan, kerakli versiya tanlanib dastur yuklab olinadi:

<img src="images/download-page.png" alt="dowload-page" title="PostgreSQL-ning yuklab olish sahifasi" style="width:90%;height:90;margin:0 auto;display:block;">


Kursda PostgreSQL-ning windows operatsion tizimga mo'ljallangan 12.8 versiyasini ishlatamiz.

O'rnatish ketma-ketligi:

1. O'rnatuvchi faylni ishga tushiramiz va ochilgan oynadan next tugmasini bosamiz:

<img src="images/install-1.png" alt="dowload-page" title="PostgreSQL-ni o'rnatishni boshlovchi oyna" style="width:90%;height:90;margin:0 auto;display:block;">

2. O'rnatiladigan papka tanlanadi:

<img src="images/install-1.1.png" alt="dowload-page" title="PostgreSQL o'rnatiladigan papkani tanlash oynasi" style="width:90%;height:90;margin:0 auto;display:block;">


3. Kerakli tool-lar tanlanadi, next tugmasi bosiladi:

<img src="images/install-2.png" alt="dowload-page" title="PostgreSQL tool tanlash oynasi" style="width:90%;height:90;margin:0 auto;display:block;">

4. Keyingi oynadan ma'lumotlarimiz saqlanadigan papka tanlanab, next tugmasini bosamiz:

<img src="images/install-3.png" alt="dowload-page" title="Foydalanuvchi ma'lumotlari saqlanuvchi papkani tanlash" style="width:90%;height:90;margin:0 auto;display:block;">

5. Ochilgan oynada ma'lumotlar xavfsizligi uchun parol teriladi:

<img src="images/install-4.png" alt="dowload-page" title="PostgreSQL uchun parol terish sahifasi" style="width:90%;height:90;margin:0 auto;display:block;">

6. Port oynasida postgresql foydalanadigan port yoziladi. Odatiy holda postgresql 5432 portidan foydalanadi:

<img src="images/install-5.png" alt="dowload-page" title="PostgreSQL uchun port terish sahifasi" style="width:90%;height:90;margin:0 auto;display:block;">

7. Keyingi oynadan interfeys tili tanlanadi:


<img src="images/install-6.png" alt="dowload-page" title="Interfeys tilini tanlash oynasi" style="width:90%;height:90;margin:0 auto;display:block;">

8. O'rantishni boshlash uchun yakuniy oyna. Next tugmasi bosilgandan so'ng chiqqan oynada yana next tugmasini bosib o'rnatish boshlanadi:

<img src="images/install-7.png" alt="dowload-page" title="O'rnatishni boshlash" style="width:90%;height:90;margin:0 auto;display:block;">

9. O'rnatish oynasi:

<img src="images/install-8.png" alt="dowload-page" title="O'rnatish oynasi" style="width:90%;height:90;margin:0 auto;display:block;">

10. Finish tugmasini bosib PostgreSQL-ni o'rnatish yakunlanadi:

<img src="images/install-9.png" alt="dowload-page" title="PostgreSQL-ni o'rnatishni yakunlash" style="width:90%;height:90;margin:0 auto;display:block;">

PostgreSQL MBBT o'rnatildi. Endi uni ishlatib ko'rsak ham bo'ladi. MBBT-dagi baza va jadvallarni ko'rish, ma'lumotlar ustida amallar bajarishni qulay qilish uchun bizga interfeys kerak bo'ladi. PostgreSQL MBBT-ni ochish uchun o'zining PgAdmin nomli dasturi bor. Bundan tashqari boshqa bir qancha dasturlardan ham foydalanish mumkin. Kursda DBeaver dasturidan foydalanamiz. Chunki undan foydalanish (men uchun) ancha qulay hisoblanadi. DBeaver dasturini o'zining rasmiy [sayt](https://dbeaver.io/download/https://)idan yuklab olish mumkin.

DBeaver-ni o'rnatgandan so'ng uni ochib PostgreSQL MBBT-ga bog'lanamiz:

1. Dasturni ochamiz:

<img src="images/dbeaver-1.png" alt="DBeaver-1" title="DBeaver-1" style="width:90%;height:90;margin:0 auto;display:block;">

2. Dasturda yangi bog'lanish yaratish uchun "bog'lanish" menyusini tanlaymiz:

<img src="images/dbeaver-2.png" alt="DBeaver-2" title="DBeaver-2" style="width:90%;height:90;margin:0 auto;display:block;">

3. Ochilgan oynadan PostgreSQL-ni tanlaymiz:

<img src="images/dbeaver-3.png" alt="DBeaver-3" title="DBeaver-3" style="width:90%;height:90;margin:0 auto;display:block;">

4. Keyin PostgreSQL uchun sozlamalar to'g'rilanadi.

<img src="images/dbeaver-4.png" alt="DBeaver-4" title="DBeaver-4" style="width:90%;height:90;margin:0 auto;display:block;">

* Agar masofadan bog'lanilsa, host-ga serverning IP manzili, lokal ishlansa localhost qo'yiladi.
* Agar aynan bitta MB-ga ulanayotgan bo'linsa, database-ga MB nomi (odatiy holda postgres turadi).
* Odatiy holda PostgreSQL 5432 port-ni ishlatadi. Agar port o'zgartirilgan bo'lsa, port sozlamasiga o'zgargan port qo'yiladi.
* PostgreSQL-da default user postgres hisoblanadi (user sozlamasida ham shu user nomi turadi). Agar boshqa foydalanuvchi yaratilgan bo'lsa, shu foydalanuvchi nomi user sozlamasiga kiritiladi.
* Locale client qismida PostgreSQL-ning kerakli versiyasi tanlanadi.
* SSH, Porxy, SSL va boshqa sozlamalar ham mavjud. Hozircha yuqoridagilar eng minimal sozlamalar hisoblanadi.

5. Bog'lanish tugaganidan so'ng DBeaver-ning o'ng tomonidagi ro'yxatda yangi bog'lanish paydo bo'ladi:

<img src="images/dbeaver-5.png" alt="DBeaver-5" title="DBeaver-5" style="width:90%;height:90;margin:0 auto;display:block;">

### 5-dars. Asosiy tiplar.