# Pertemuan 03

## A. Migration

Migration adalah cara Laravel untuk membuat semua orang (end-user maupun anggota tim) mendapatkan struktur database yang sama.  

Migration ditulis dalam bahasa PHP dengan menggunakan syntax/method dari Laravel.  

### A.1 Contoh menulis migration

Ambil contoh kita akan membuat tabel `employees`. Tabel ini akan berisi kolom-kolom sebagai berikut:  
- `id` : primary key, auto-increment
- `nik`: string, unique
- `nama`: string
- `email`: string, unique
- `tanggal_lahir`: date
- `gaji_pokok`: double

Maka pembuatan migration-nya adalah sebagai berikut:
1. Buka `terminal` / `cmd`
2. Masuk ke folder aplikasi `online-store`
3. Jalankan: `php artisan make:migration create_employees_table --create=employees`
4. Akan muncul file baru dengan nama sama seperti di atas dalam `/database/migrations`
5. Buka file baru tersebut (`yyyy_mm_dd_hhiiss_create_employees_table.php`)
6. Di dalam method `up()`, isikan kode berikut:
```php
Schema::create('employees', function (Blueprint $table) {
    $table->increments('id');
    $table->string('nik')->unique();
    $table->string('nama');
    $table->string('email')->unique();
    $table->date('tanggal_lahir');
    $table->double('gaji_pokok');
    $table->timestamps();
});
```
7. Kembali ke `terminal` / `cmd`, jalankan: `php artisan migrate:refresh`
8. Buka PhpMyAdmin (atau MySQL client apapun)
9. Seharusnya di sana terdapat tabel baru bernama `employees`

Demikianlah keterangan singkat dan contoh tentang migration.

## B. Kebutuhan Migration Untuk Online Store

Dengan cara yang sama seperti contoh di atas, buatlah tabel-tabel di bawah ini.  
Berikut ini adalah daftar migration untuk urusan online store ini:

Tabel: __categories__  

| Columns        | Attributes                  |
| :------------- | :-------------------------- |
| id             | increments                  |
| name           | string, unique              |
| parent_id      | integer, unsigned, nullable |
| timestamps     |                             |

Tabel: __products__  

| Columns        | Attributes                  |
| :------------- | :-------------------------- |
| id             | increments                  |
| sku            | string, unique              |
| name           | string, unique              |
| parent_id      | integer, unsigned, nullable |
| unit_price     | double                      |
| sale_price     | double, default:0           |
| stock          | integer                     |
| description    | text                        |
| timestamps     |                             |

Tabel: __category_product__  

| Columns        | Attributes                  |
| :------------- | :-------------------------- |
| category_id    | integer, unsigned           |
| product_id     | integer, unsigned           |

Tabel: __statuses__  

| Columns        | Attributes                  |
| :------------- | :-------------------------- |
| id             | increments                  |
| name           | string, unique              |
| timestamps     |                             |

Tabel: __gateways__  

| Columns        | Attributes                  |
| :------------- | :-------------------------- |
| id             | increments                  |
| name           | string, unique              |
| timestamps     |                             |

Tabel: __orders__  

| Columns        | Attributes                  |
| :------------- | :-------------------------- |
| id             | increments                  |
| order_no       | string, unique              |
| user_id        | integer, unsigned           |
| gateway_id     | integer, unsigned           |
| grand_total    | double                      |
| notes          | text, nullable              |
| timestamps     |                             |

Tabel: __order_product__  

| Columns        | Attributes                  |
| :------------- | :-------------------------- |
| id             | increments                  |
| order_id       | integer, unsigned           |
| product_id     | integer, unsigned           |
| quantity       | integer                     |
| subtotal       | integer                     |
| timestamps     |                             |

Tabel: __order_status__  

| Columns        | Attributes                  |
| :------------- | :-------------------------- |
| id             | increments                  |
| order_id       | integer, unsigned           |
| status_id      | integer, unsigned           |
| timestamps     |                             |
