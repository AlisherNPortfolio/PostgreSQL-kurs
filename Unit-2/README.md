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
