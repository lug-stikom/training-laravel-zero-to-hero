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

1. Copy folder `css`, `img`, dan `js` dari dalam folder `adminlte/dist`
2. Paste ke dalam folder `online-store/public`  
    Akan ada `/public/css`, `/public/img`, dan `/public/js`
3. Buat file `master.blade.php` di dalam folder `/resources/views/layouts`
4. Buka `https://pastebin.com/kuiPYUgZ`
5. Copas ke dalam file `master.blade.php` tadi
