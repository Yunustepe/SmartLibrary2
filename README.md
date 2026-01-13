SmartLibraryPlus - ORM Tabanlı Akıllı Kütüphane Sistemi

Bu proje, Nesneye Yönelik Programlama (OOP) ve Hibernate ORM teknolojileri kullanılarak geliştirilmiş, konsol tabanlı bir kütüphane yönetim sistemidir. Proje, doğrudan JDBC kodları yerine Hibernate framework'ü kullanılarak veritabanı bağımsız ve sürdürülebilir bir yapı sunmayı amaçlar.

## 🎯 Projenin Amacı

•⁠  ⁠*ORM (Object Relational Mapping)* mantığını kavramak ve uygulamak.
•⁠  ⁠*Hibernate* ile veritabanı işlemlerini (CRUD) gerçekleştirmek.
•⁠  ⁠Entity ve İlişki (OneToMany, OneToOne) yapılarını kurmak.
•⁠  ⁠SQLite veritabanı üzerinde kalıcı veri saklamak.

## 🛠️ Kullanılan Teknolojiler

•⁠  ⁠*Programlama Dili:* Java (JDK 8+)
•⁠  ⁠*ORM Framework:* Hibernate
•⁠  ⁠*Veritabanı:* SQLite
•⁠  ⁠*Build Tool:* Maven
•⁠  ⁠*IDE:* IntelliJ IDEA / Eclipse

## 📂 Proje Yapısı

Proje, katmanlı bir mimari yaklaşımıyla geliştirilmiştir.
Entity, DAO ve uygulama katmanları birbirinden ayrılmıştır.


⁠ text
SmartLibraryPlus/
│
├── src/main/java/
│   ├── entity/     # Veritabanı tablolarına karşılık gelen POJO sınıfları
│   ├── dao/        # Veritabanı erişim nesneleri (CRUD işlemleri)
│   ├── util/       # Hibernate konfigürasyon ve SessionFactory yönetimi
│   └── app/        # Main sınıfı ve Konsol Menü mantığı
│
├── hibernate.cfg.xml # Veritabanı bağlantı ayarları
├── pom.xml           # Bağımlılık yönetimi (Hibernate, SQLite Driver)
└── README.md         # Proje dokümantasyonu

 ⁠

## 🧱 Veritabanı Tasarımı ve İlişkiler (ER Diagram)

Projede üç ana Entity bulunmaktadır ve aralarındaki ilişkiler şu şekildedir:

1.⁠ ⁠*Book (Kitap):* Kitap bilgilerini tutar.
•⁠  ⁠İlişki: ⁠ Loan ⁠ ile *OneToOne* ilişkisi vardır.


2.⁠ ⁠*Student (Öğrenci):* Kütüphaneye kayıtlı öğrencileri tutar.
•⁠  ⁠İlişki: ⁠ Loan ⁠ ile *OneToMany* ilişkisi vardır (Bir öğrenci birden fazla işlem yapabilir).


3.⁠ ⁠*Loan (Ödünç Alma):* Hangi kitabın hangi öğrenci tarafından alındığını tutar.

### Entity Özellikleri

| Sınıf | Özellikler | İlişki Notları |
| --- | --- | --- |
| *Book* | id, title, author, year, status | ⁠ status ⁠: AVAILABLE / BORROWED |
| *Student* | id, name, department | ⁠ List<Loan> loans ⁠ |
| *Loan* | id, borrowDate, returnDate | ⁠ Student student ⁠, ⁠ Book book ⁠ |

## ⚙️ Kurulum ve Çalıştırma

1.⁠ ⁠*Projeyi Klonlayın/İndirin:* Proje dosyalarını bilgisayarınıza kaydedin.
2.⁠ ⁠*Bağımlılıkları Yükleyin:*
•⁠  ⁠Proje Maven tabanlıdır. ⁠ pom.xml ⁠ dosyasındaki bağımlılıkların (Hibernate Core, SQLite JDBC) inmesini bekleyin.


3.⁠ ⁠*Veritabanı Ayarı:*
•⁠  ⁠⁠ hibernate.cfg.xml ⁠ dosyası proje kök dizininde veya ⁠ resources ⁠ altında olmalıdır.
•⁠  ⁠⁠ hbm2ddl.auto ⁠ özelliği ⁠ update ⁠ olarak ayarlandığı için tablolar ilk çalıştırmada otomatik oluşturulacaktır.


4.⁠ ⁠*Uygulamayı Başlatın:*
•⁠  ⁠⁠ src/app/Main.java ⁠ (veya uygulamanın giriş noktası olan sınıf) dosyasını çalıştırın.



## 📋 Kullanım (Menü İşlemleri)

Uygulama çalıştırıldığında aşağıdaki konsol menüsü sizi karşılayacaktır:

1.⁠ ⁠*Kitap Ekle:* Sisteme yeni kitap ekler (Varsayılan durum: AVAILABLE).
2.⁠ ⁠*Kitapları Listele:* Tüm kitapları ve ödünç durumlarını listeler.
3.⁠ ⁠*Öğrenci Ekle:* Sisteme yeni öğrenci kaydeder.
4.⁠ ⁠*Öğrencileri Listele:* Kayıtlı öğrencileri listeler.
5.⁠ ⁠*Kitap Ödünç Ver:*
•⁠  ⁠Seçilen öğrenciye seçilen kitabı ödünç verir.
•⁠  ⁠Kontrol: Eğer kitap zaten ödünçteyse (BORROWED) işlem engellenir.


6.⁠ ⁠*Ödünç Listesini Görüntüle:* Kimin hangi kitabı ne zaman aldığını gösterir.
7.⁠ ⁠*Kitap Geri Teslim Al:*
•⁠  ⁠Kitabın iade tarihini (returnDate) günceller.
•⁠  ⁠Kitabın durumunu tekrar AVAILABLE yapar.


8.⁠ ⁠*Çıkış:* Uygulamayı kapatır ve Hibernate oturumunu sonlandırır.

## ⚠️ Kısıtlamalar ve Kurallar

•⁠  ⁠*JDBC Kullanımı:* Yasaktır. Tüm işlemler Hibernate Session ve Transaction üzerinden yürütülür.
•⁠  ⁠*SQL Sorguları:* Manuel SQL yazılmamış, HQL veya Hibernate metotları kullanılmıştır.
•⁠  ⁠*GUI:* Grafik arayüz yoktur, tamamen konsol tabanlıdır.
