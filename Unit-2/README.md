# 2-Bo'lim

### 1-Dars. SELECT operatori.

Oldingi bo'limda biz MB, MBBT, SQL tili, MB yaratish, jadval yaratish kabi tushunchalar bilan tanishgan edik. Ikkinchi bo'limda esa asosiy so'rovlarni o'rganishni davom ettiramiz. Oldingi bo'limdan farqli ravishda, ushbu bo'limda so'rovlarni o'rganish uchun oldindan yaratilgan **northwind** MB-dan foydalanamiz.

Bu MB-ni ushbu [havola](./sources/northwind.sql)dan yuklab olib ishga tushirishingiz mumkin.

Jadvaldan kerakli ma'lumotlarni olish uchun `SELECT` operatoridan foydalaniladi. Asosiy sintaksisi quyidagicha:

```bash
SELECT ustun1, ustun2, ..., ustunN FROM jadval_nomi
```

Masalan:

<img src="images/lesson-1-1.png" alt="lesson-1-1" title="lesson-1-1" style="width:90%;height:90;margin:0 auto;display:block;">

Misolda keltirilgan `*` barcha ustunlarni olishni anglatadi. Lekin doim ham `*` bilan ustunlar olinmaydi. Chunki ayrim hollarda barcha ustunlar ham kerak bo'lavermaydi. Hamma ustunni olish tizimga ortiqcha va keraksiz yuklanish tushirishi mumkin. Buning oldini olish uchun esa aynan kerak bo'ladigan ustunlar olinadi:

<img src="images/lesson-1-2.png" alt="lesson-1-2" title="lesson-1-2" style="width:90%;height:90;margin:0 auto;display:block;">

### 2-dars. Matematik amallar

SQL tili dasturlash tillari singari matematik amallarni bajarish imkonini beradi.

SQL tilidagi matematik amallar:

* `+` - qo'shish
* `-` - ayirish
* `*` - ko'paytirish
* `/` - bo'lish
* `^` - darajaga oshirish
* `|/` - kvadrat ildiz
* va boshqa ko'plab operator va funksiyalar

PostgreSQL-ning o'zida ham yana qo'shimcha matematik amallari mavjud.

Endi, amaliyotga o'tib, matematik amallarni bajarish ko'ramiz.

Ma'lumot sifatida test MB-dagi `products` jadvali ma'lumotlaridan foydalanamiz. `Products` jadvalida bitta mahsulot narxi (`unit_price`) va do'kondagi mahsulotlar soni (`unis_in_stock`) ustunlari mavjud. `Products` jadvalidagi mahsulotlar ro'yxatini chiqarishda, yangi ustunda mahsulotning umumiy narxini ham qo'shib chiqaraylik.

<img src="images/lesson-2-1.png" alt="lesson-2-1" title="lesson-2-1" style="width:90%;height:90;margin:0 auto;display:block;">

### 3-dars. DISTINCT

`DISTINCT` operatori jadvaldagi takrorlanmas (unique) ma'lumotlarni olib beradi. Misol uchun, test MB-dagi `employees` jadvalidan ishchilar yashaydigan shaharlarni olishimiz kerak bo'lsin (masalan, mana shu shaharlardan ishchilarimiz bor deb saytimizda ko'rsatmoqchimiz):

```bash
SELECT city FROM employees;
```

<img src="images/lesson-3-1.png" alt="lesson-3-1" title="lesson-3-1" style="width:90%;height:90;margin:0 auto;display:block;">

Lekin, ko'rib turganingizdek, ba'zi shaharlar takrorlanib chiqib qoldi (chunki, ayrim ishchilar bitta shahardan). Bizga esa, faqat bittasi yetarli. Duplikat (takrorlangan) shaharlarni qanday olib tashlash mumkin? Albatta, `DISTINCT` operatori bilan!

```bash
SELECT DISTINCT city FROM employees;
```

<img src="images/lesson-3-2.png" alt="lesson-3-2" title="lesson-3-2" style="width:90%;height:90;margin:0 auto;display:block;">

`DISTINCT` bilan nafaqat bitta, balki bir nechta ustunlarni ham ishlatish mumkin:

```bash
SELECT DISTINCT city, country FROM employees;
```

<img src="images/lesson-3-3.png" alt="lesson-3-3" title="lesson-3-3" style="width:90%;height:90;margin:0 auto;display:block;">

### 4-dars. COUNT

`COUNT` operatori qatorlar sonini hisoblab beradi. Masalan, `orders` jadvalida qancha yozuv borligini bilmoqchimiz:

```bash
SELECT COUNT(*) FROM orders;
```

<img src="images/lesson-4-1.png" alt="lesson-4-1" title="lesson-4-1" style="width:90%;height:90;margin:0 auto;display:block;">

Bu yerda `COUNT(*)` dagi `*` o'rniga jadvaldagi birorta ustun nomini qo'shsa ham bo'ladi:

```bash
SELECT COUNT(id) FROM orders;
```

Endi, `employees` jadvalida nechta davlat borligini ko'raylik:

```bash
SELECT COUNT(id) FROM employees;
```

Lekin bu so'rov `employees` jadavalidagi davlatlar sonini emas, balki jadvaldagi barcha qatorlar sonini hisoblab beradi. Oldingi darsda ko'rganimizdek, davlatlar takrorlanib chiqqani sababli `COUNT` bizga no'to'g'ri ma'lumot chiqarib beradi. Nima qilish kerak? Albatta, `DISTINCT`-dan foydalanamiz!

```bash
SELECT COUNT(DISTINCT country) FROM employees;
```

<img src="images/lesson-4-2.png" alt="lesson-4-2" title="lesson-4-2" style="width:90%;height:90;margin:0 auto;display:block;">
