SmartLibraryPlus

Hibernate ORM Tabanlı Akıllı Kütüphane Sistemi

Proje Açıklaması

Bu proje, Nesneye Yönelik Programlama (OOP) prensipleri ve Hibernate ORM kullanılarak geliştirilmiş, SQLite veritabanı ile çalışan bir masaüstü konsol uygulamasıdır.
Amaç; entity–relationship yapılarının, ORM mantığının ve CRUD işlemlerinin uygulamalı olarak gösterilmesidir.

Uygulama, bir üniversite kütüphanesinde kitapların ve öğrencilerin yönetilmesini, kitap ödünç verme ve iade işlemlerinin takip edilmesini sağlar.

Kullanılan Teknolojiler

Java

Hibernate ORM

SQLite

Maven

Annotation tabanlı mapping

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


entity: Veritabanı tablolarını temsil eden sınıflar

dao: Veritabanı işlemlerinin yapıldığı katman

util: Hibernate yapılandırması ve yardımcı sınıflar

app: Uygulamanın çalıştığı ana sınıf (Main)

Entity Sınıfları
Book

id

title

author

publishYear

status (AVAILABLE / BORROWED)

Student

id

name

department

Bir öğrenci birden fazla ödünç alma kaydına sahip olabilir.

Loan

id

borrowDate

returnDate

Nesne İlişkileri

Student – Loan → OneToMany / ManyToOne

Loan – Book → OneToOne

İlişkiler Hibernate annotation’ları kullanılarak tanımlanmıştır.

DAO Katmanı

Her entity için ayrı DAO sınıfı bulunmaktadır:

BookDao

StudentDao

LoanDao

Her DAO sınıfında aşağıdaki metotlar yer almaktadır:

save

update

delete

getById

getAll

Tüm veritabanı işlemleri Hibernate Session ve Transaction kullanılarak gerçekleştirilmiştir.

Veritabanı

SQLite kullanılmıştır

Tablolar Hibernate tarafından otomatik oluşturulmaktadır

hbm2ddl.auto = update ayarı aktiftir

Konsol Menü

Uygulama çalıştığında kullanıcıya aşağıdaki menü sunulur:

1 - Kitap Ekle
2 - Kitapları Listele
3 - Öğrenci Ekle
4 - Öğrencileri Listele
5 - Kitap Ödünç Ver
6 - Ödünç Listesini Görüntüle
7 - Kitap Geri Teslim Al
0 - Çıkış

Uygulama Kuralları

Ödünç verilmiş bir kitap tekrar ödünç verilemez

Kitap iade edildiğinde durumu tekrar AVAILABLE olarak güncellenir

JDBC ile doğrudan SQL yazılmamıştır

Çalıştırma

Proje bir Java IDE’sinde (IntelliJ IDEA vb.) açılır

Maven bağımlılıkları yüklenir

Main sınıfı çalıştırılır

Konsol üzerinden işlemler yapılır
