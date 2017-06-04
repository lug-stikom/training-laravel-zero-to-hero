# Pertemuan 04

## A. Seeder

Seeder adalah cara Laravel untuk mengisi data awal aplikasi kita.  
Data awal ini bisa berupa: data default yang harus ada, biasanya untuk config; atau data master.

## A.1 Membuat File Seeder

1. Buka `terminal` / `cmd`
2. Masuk ke `online-store`
3. Jalankan: `php artisan make:seeder EmployeesTableSeeder`
4. Jika sukses, akan ada file `EmployeesTableSeeder.php` di dalam `/database/seeds`

## A.2 Mengisi Seeder

1. Buka file `EmployeesTableSeeder.php`
2. Di line 3 tambahkan: `use Carbon\Carbon;`
3. Di dalam fungsi `run()` isikan kode berikut:
```php
DB::table('employees')->insert([
    'nik' => 'N-0001',
    'nama' => 'Kukuh',
    'email' => 'rkukuh@gmail.com',
    'tanggal_lahir' => Carbon::now()->->setDate(1987, 1, 31)
    'gaji_pokok' => 10000000,
    'created_at' => new DateTime(),
    'updated_at' => new DateTime(),
]);
```
4. Buka file `DatabaseSeeder.php`
5. Di dalam fungsi `run()` tambahkan: `$this->call(EmployeesTableSeeder::class);`
