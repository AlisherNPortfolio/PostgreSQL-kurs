# 4-bo'lim

### 1-dars. Ost-so'rovlar.

Ba'zi paytlarda, proyektlarda anchagina murakkab so'rovlarni yozishga to'g'ri keladi. Shu paytgacha yozgan so'rovlarimiz esa unchalik ham murakkab emas edi.

Agar juda murakkab so'rov yozishga to'g'ri kelsa, uni ost-so'rovlarga ajratib yozishga harakat qilib ko'rish kerak. Chunki, bunda katta murakkab so'rovni butunicha tushunishdan ko'ra, uni mayda qismlarga bo'lib tushunish osonroq bo'ladi.

Ba'zi hollarda esa, ayrim so'rovlarni ost-so'rovlarga bo'lmay hal qilishning deyarli  iloji bo'lmaydi.

Ba'zi hollarda esa, ost-so'rovlardan foydalanmaslik ham kerak bo'ladi. Masalan, uning o'rniga bog'lanishlardan foydalanish mumkin bo'lsa.

Ost-so'rovlardan doim ham foydalanmagan ma'qulmi?

* Shart emas. Vaziyatga qarash kerak.
* Agar ost-so'rov bog'lanishlar bilan bir xilda samarador bo'lsa, qaysi birini o'qish oson bo'lsa, o'shanisidan foydalanish kerak.

Vazifa: mijozlar buyurtma bergan mamlakatlardagi barcha yetkazib beruvchi kompaniyalarni chiqarib bering.

Buning uchun avvalo, buyurtma beruvchi mijozlar joylashgan davlatlarni topamiz:

```bash
SELECT DISTINCT country
FROM customers;
```

Keyin esa, olingan ro'yxatdagi davlatlarda joylashgan yetkazib berish kompaniyalarini topamiz. Bunda filterlashda `IN` dan keyin qavs ichida yuqoridagi so'rovni beramiz:

```bash
SELECT company_name
FROM suppliers
WHERE country IN (
	SELECT DISTINCT country
	FROM customers
);
```

Bu so'rov quyidagi bilan bir xil hisoblanadi:

```bash
SELECT company_name
FROM suppliers
WHERE country IN ('Argentina', 'Spain', 'Switzerland', 'Italy', 'Venezuela');
```

Farqi, oldingi so'rovimizda qavs ichida berilgan davlat nomlarini so'rov bilan `customers` jadvalidan olamiz.

Endi oxirgi so'rovimizni `JOIN` bilan yozib ko'ramiz:

```bash
SELECT DISTINCT suppliers.company_name 
FROM suppliers
JOIN customers USING(country);
```

Keyingi vazifa. Mahsulotlar narxining yig'inidisini kategoriya bo'yicha guruhlab chiqarish kerak bo'lsin. Bunda chiquvchi ma'lumotlar soni `products` jadvalining eng kichik `product_id`-siga 4 qo'shilganidan oshmasin:

```bash
SELECT category_name, SUM(units_in_stock)
FROM products
INNER JOIN categories USING(category_id)
GROUP BY category_name
ORDER BY SUM(units_in_stock)  DESC
LIMIT (SELECT MIN(product_id) + 4 FROM products);
```

Vazifa: `products` jadvalida narxi barcha mahsulotlarning o'rtacha narxidan yuqori bo'lgan mahsulotlarni chiqaring.

```bash
SELECT product_name, units_in_stock 
FROM products
WHERE units_in_stock > (
	SELECT AVG(units_in_stock)
	FROM products
)
ORDER BY units_in_stock;
```
