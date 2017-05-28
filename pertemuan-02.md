# Pertemuan 02

## A. Download AdminLTE
1. Buka `https://adminlte.io`
2. Unzip di web root
3. Rename menjadi `adminlte`
4. Pastikan web server dijalankan
5. Panggil lewat browser, contoh: `http://localhost/adminlte`

## B. Laravel View

View adalah salah satu dari 3 bagian metode MVC (Model-View-Controller).  
Seperti namanya, View bertanggungjawab pada urusan tampilan di browser.

View sebenarnya hanyalah tampilan web biasa, yang dibentuk dengan HTML, CSS, dan JS.  
Laravel membagi peletakan file-file view berdasarkan jenisnya dalam folder:

- CSS: `/public/css/*`
- Javascript: `/public/js/*`
- HTML: `/resources/views/*`

Laravel juga mendukung pre-processor CSS dengan SASS dan Mix.  

Komponen web yang dibuat dari javascript frameworks (Vue, Angular, atau React) juga disimpan dalam `/resources/assets/*`

## C. Memindahkan AdminLTE ke Laravel

1. Copy folder `dist` dari dalam folder `adminlte/`
2. Paste ke dalam folder `online-store/public/`  
    Akan ada folder `/public/dist/*`
3. Copy folder `bootstrap` dari dalam folder `adminlte`
4. Paste ke dalam folder `online-store/public`  
    Akan ada folder `/public/bootstrap`
5. Buat file `master.blade.php` di dalam folder `/resources/views/layouts`
6. Buka `https://pastebin.com/kuiPYUgZ`
7. Copas ke dalam file `master.blade.php` tadi

## D. Memanggil View Melalui Route

1. Buka `file /routes/web.php`
2. Isi dengan kode
```php
Route::get('/admin', function() {
    return view('layouts.master');
});
```
3. Buka `terminal` / `cmd`
4. Masuk ke dalam aplikasi `online-store`, jalankan `php artisan serve`
5. Buka browser, arahkan ke `localhost:8000/admin`  


## E. Membuat @section Dalam Master Layout

1. Buka file `resources/views/layouts/master.blade.php`
2. Cari kode `<!-- Your Page Content Here -->`
3. Ganti menjadi `@yield('content')`
4. Buat folder `admin` dalam `/resources/views/`
5. Didalamnya buat file `dashboard.blade.php`
6. Didalam file `dashboard.blade.php`, isi kode berikut:
```php
@extends('layouts.master')

@section('content')
    Ini konten dari view dashboard.blade.php
@endsection
```
7. Buka `routes/web.php`
8. Cari kode
```php
Route::get('/admin', function() {
    return view('layouts.master');
});
```
ganti menjadi:
```php
Route::get('/admin', function() {
    return view('admin.dashboard');
});
```
9. Kembali ke browser, refresh


### E.1 Contoh penggunaan @section('content') yang lain
1. Buat folder `product` di dalam `/resources/views/`
2. Buat file `index.blade.php` di dalam folder `product` tadi
3. Buka file view `/product/index.blade.php` tadi, isi dengan kode:
```php
@extends('layouts.master')

@section('content')
    Ini konten dari view product/index.blade.php
@endsection
```
4. Buka file `/routes/web.php`
5. Isi kode baru berikut:
```php
Route::get('/product', function() {
    return view('product.index');
});
```
6. Kembali ke browser, arahkan ke route `http://localhost:8000/product`
