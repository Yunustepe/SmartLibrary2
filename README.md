SmartLibraryPlus
Proje Hakkında;

Bu proje, Java ve Hibernate ORM kullanılarak geliştirilmiş, SQLite veritabanı ile çalışan bir konsol tabanlı kütüphane yönetim sistemidir.
Amaç; OOP prensiplerini, ORM mantığını, entity ilişkilerini ve CRUD işlemlerini uygulamalı olarak göstermektir.

Kullanılan Teknolojiler:
-Java
-Hibernate ORM
-SQLite
-Maven
-Annotation tabanlı mapping

Proje Yapısı
SmartLibraryPlus/
 ├── src/
 │   ├── entity/
 │   ├── dao/
 │   ├── util/
 │   └── app/
 ├── hibernate.cfg.xml
 ├── pom.xml
 └── README.md

Entity’ler:
Book: id, title, author, publishYear, status
Student: id, name, department
Loan: id, borrowDate, returnDate

İlişkiler:
Student – Loan → OneToMany / ManyToOne
Loan – Book → OneToOne
DAO Katmanı
Her entity için ayrı DAO sınıfı vardır:
BookDao
StudentDao
LoanDao

Her DAO’da:
-save
-update
-delete
-getById
-getAll
-metotları yer almaktadır.

Uygulama Özellikleri:
-Kitap ekleme ve listeleme
-Öğrenci ekleme ve listeleme
-Kitap ödünç verme
-Ödünç listesini görüntüleme
-Kitap iade işlemi
-Ödünç verilen kitap tekrar ödünç verilemez.

Veritabanı:
-SQLite kullanılmaktadır
-Tablolar Hibernate tarafından otomatik oluşturulmaktadır
-hbm2ddl.auto = update aktiftir

Çalıştırma:
-Main sınıfı çalıştırılarak uygulama başlatılır ve işlemler konsol üzerinden yapılır.
