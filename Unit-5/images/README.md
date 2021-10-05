# 5-bo'lim

### 1-dars. DDL

**DDL - Data Defenition Language**. `DDL` - `SQL` tilining bir qismi bo'lib, u ma'lumotlarni yaratish, o'zgartirish va o'chirish kabi ishlarni bajarishda qo'llaniladi.

Bu darsda quyidagi tuzilmalarni o'rganamiz:

* **CREATE TABLE jadval_nomi** - jadval yaratish
* **ALTER TABLE jadval_nomi** - mavjud jadvalni o'zgartirish
  * **ADD COLUMN ustun_nomi malumot_tipi** - mavjud jadvalga ustun qo'shish
  * **RANAME TO jadvalning_yangi_nomi** - mavjud jadval nomini o'zgartirish
  * **RANAME ustunning_eski_nomi TO ustunning_yangi_nomi** - jadvaldagi ustun nomini o'zgartirish
  * **ALTER COLUMN ustun_nomi SET DATA TYPE malumot_tipi** - jadvaldagi ustun ma'lumotlarini o'zgartirish
* **DROP TABLE jadval_nomi** - jadvalni o'chirish
* **TRUNCATE TABLE jadval_nomi** - jadval ichidagi ma'lumotlarni tozalab tashalash. Bu yerda, agar jadvalda tashqi kalit (foreign key)li ustun mavjud bo'lsa, TRUNCATE jadvalni tozalay olmaydi.
* **DROP COLUMN ustun_nomi** - jadvaldagi ustunni o'chirish


**CREATE TABLE.**

Jadval yaratishni oldingi darslarda ko'rgan edik. Bu darsda ham misol ko'ramiz. *Talaba* va *kafedra* jadvallarini yaratamiz:

```bash
create table students
(
	student_id serial,
	first_name varchar,
	last_name varchar,
	birthday date,
	phone varchar
);

create table cathedra
(
	cathedra_id serial,
	cathedra_name varchar,
	dean varchar
);

create table faculty
(
	faculty_id serial,
	faculty_name varchar
); -- fakultetlarga ma'lumot kiritiladi. ma'lumot kiritishni keyingi darslarda ko'ramiz.
```

**ALTER TABLE.**

**ADD COLUMN.**

```bash
alter table students 
add column middle_name varchar;

alter table students 
add column rating float;

alter table students 
add column enrolled date;
```

**DROP COLUMN.**

```bash
alter table students 
drop column middle_name;
```

**RENAME TO.**

```bash
alter table cathedra 
rename to chair;
```

**RENAME ... TO**

```bash
alter table chair
rename cathedra_id to chair_id;

alter table chair
rename cathedra_name to chair_name;
```

**ALTER COLUMN**

```bash
alter table students 
alter column first_name set data type varchar(64);

alter table students
alter column last_name set data type varchar(64);

alter table students
alter column phone set data type varchar(30);
```

**TRUNCATE TABLE.**

```bash
truncate table faculty;
```

`TRUNCATE` bilan jadval tozalanganda,` serial` ketma-ketligini tozalamaydi. Shu sababli ham tozalangan jadvalga ma'lumot kiritilsa yangi `id`-lar oldingi kelib qolgan sondan boshlanib ketadi.

`id` qaytadan 1 bilan boshlanishi uchun, uni `RESTART` qilish kerak bo'ladi (odatiy holatda `CONTINUE` bo'lib tozalanadi):

```bash
truncate table faculty restart identity;
```

`truncate table faculty;` va `truncate table faculty continue identity;` so'rovlari bir xil amalni bajaradi.

**DROP TABLE.**

```bash
drop table faculty;
```
