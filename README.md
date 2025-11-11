MariaDB [(none)]> create database Bandara;
Query OK, 1 row affected (0.005 sec)

MariaDB [(none)]> Show databases;
+--------------------+
| Database           |
+--------------------+
| bandara            |
| information_schema |
| mysql              |
| performance_schema |
| phpmyadmin         |
| test               |
| tugas3_d0224032    |
| uts_d0224032       |
+--------------------+
8 rows in set (0.002 sec)

MariaDB [(none)]> use Bandara;
Database changed
MariaDB [Bandara]> Create table Maskapai(
    -> id_maskapai INT PRIMARY KEY,
    -> nama_maskapai Varchar(100),
    -> negara_asal Varchar(100),
    -> kode Varchar(10)
    -> );
Query OK, 0 rows affected (0.074 sec)

MariaDB [Bandara]> Create table Penerbangan(
    -> id_penerbangan INT PRIMARY KEY,
    -> id_maskapai INT,
    -> tujuan Varchar(100),
    -> jadwal Time,
    -> tanggal Date,
    -> FOREIGN KEY (id_maskapai) REFERENCES maskapai(id_maskpai)
    -> );
ERROR 1005 (HY000): Can't create table `bandara`.`penerbangan` (errno: 150 "Foreign key constraint is incorrectly formed")
MariaDB [Bandara]> Create table Penerbangan(
    -> id_penerbangan INT PRIMARY KEY,
    ->     id_maskapai INT,
    ->     tujuan VARCHAR(100),
    ->     jadwal TIME,
    ->     tanggal DATE,
    ->     FOREIGN KEY (id_maskapai) REFERENCES maskapai(id_maskapai)
    -> );
Query OK, 0 rows affected (0.074 sec)

MariaDB [Bandara]> desc penerbangan;
+----------------+--------------+------+-----+---------+-------+
| Field          | Type         | Null | Key | Default | Extra |
+----------------+--------------+------+-----+---------+-------+
| id_penerbangan | int(11)      | NO   | PRI | NULL    |       |
| id_maskapai    | int(11)      | YES  | MUL | NULL    |       |
| tujuan         | varchar(100) | YES  |     | NULL    |       |
| jadwal         | time         | YES  |     | NULL    |       |
| tanggal        | date         | YES  |     | NULL    |       |
+----------------+--------------+------+-----+---------+-------+
5 rows in set (0.081 sec)

MariaDB [Bandara]> desc maskapai;
+---------------+--------------+------+-----+---------+-------+
| Field         | Type         | Null | Key | Default | Extra |
+---------------+--------------+------+-----+---------+-------+
| id_maskapai   | int(11)      | NO   | PRI | NULL    |       |
| nama_maskapai | varchar(100) | YES  |     | NULL    |       |
| negara_asal   | varchar(100) | YES  |     | NULL    |       |
| kode          | varchar(10)  | YES  |     | NULL    |       |
+---------------+--------------+------+-----+---------+-------+
4 rows in set (0.061 sec)

MariaDB [Bandara]> desc penumpang;
+----------------+--------------+------+-----+---------+-------+
| Field          | Type         | Null | Key | Default | Extra |
+----------------+--------------+------+-----+---------+-------+
| id_penumpang   | int(11)      | NO   | PRI | NULL    |       |
| id_penerbangan | int(11)      | YES  | MUL | NULL    |       |
| nama_penumpang | varchar(100) | YES  |     | NULL    |       |
| nomor_kursi    | varchar(10)  | YES  |     | NULL    |       |
+----------------+--------------+------+-----+---------+-------+
4 rows in set (0.054 sec)

MariaDB [Bandara]> Insert into Maskapai Values
    -> (1,'Garuda Indonesia','Indonesia','GA'),
    -> (2,'Lion Air','Indonesia','JT'),
    -> (3,'Batik Air','Indonesia','ID'),
    -> (4,'Citilink','Indonesia','QG'),
    -> (5,'AirAsia','Malaysia','AK'),
    -> (6,'Malaysia Airlines','Malaysia','MH'),
    -> (7,'Singapore Airlines','Singapore','SQ'),
    -> (8,'Emirates','Uni Emirat Arab','EK'),
    -> (9,'Qatar Airways','Qatar','QR'),
    -> (10,'Etihad Airways','Uni Emirat Arab','EY'),
    -> (11,'Japan Airlines','Jepang','JL'),
    -> (12,'ANA','Jepang','NH'),
    -> (13,'Thai Airways','Thailand','TG'),
    -> (14,'Scoot','Singapore','TR'),
    -> (15,'KLM Royal Dutch','Belanda','KL');
Query OK, 15 rows affected (0.125 sec)
Records: 15  Duplicates: 0  Warnings: 0

MariaDB [Bandara]> Insert Into Penerbangan Values
    ->  (1,1,'Jakarta','08:00:00','2025-01-10'),
    ->  (2,2,'Surabaya','09:30:00','2025-01-10'),
    ->  (3,3,'Denpasar','10:15:00','2025-01-10'),
    -> (4,4,'Makassar','11:45:00','2025-01-10'),
    -> (5,5,'Kuala Lumpur','12:30:00','2025-01-10'),
    -> (6,6,'Penang','15:00:00','2025-01-10'),
    -> (7,7,'Singapore','07:25:00','2025-01-11'),
    -> (8,8,'Dubai','21:00:00','2025-01-11'),
    -> (9,9,'Doha','22:10:00','2025-01-11'),
    -> (10,10,'Abu Dhabi','23:15:00','2025-01-11'),
    -> (11,11,'Tokyo','06:45:00','2025-01-12'),
    -> (12,12,'Osaka','13:20:00','2025-01-12'),
    -> (13,13,'Bangkok','14:30:00','2025-01-12'),
    -> (14,14,'Singapore','16:40:00','2025-01-12'),
    -> (15,15,'Amsterdam','00:15:00','2025-01-12');
Query OK, 15 rows affected (0.007 sec)
Records: 15  Duplicates: 0  Warnings: 0

MariaDB [Bandara]> Insert Into Penumpang Values
    -> (1,1,'Aulia Rahman','12A'),
    -> (2,2,'Rizky Putra','14B'),
    -> (3,3,'Siti Aisyah','10C'),
    -> (4,4,'Bimo Pratama','08D'),
    -> (5,5,'Putri Lestari','16F'),
    -> (6,6,'Fajar Nugraha','09A'),
    -> (7,7,'Hana Safitri','07C'),
    -> (8,8,'Dewi Anggraini','02A'),
    -> (9,9,'Randy Maulana','05B'),
    -> (10,10,'Winda Kartika','13D'),
    -> (11,11,'Adit Mahendra','04A'),
    -> (12,12,'Nia Ayuningrum','11C'),
    -> (13,13,'Samsul Bahri','17E'),
    -> (14,14,'Rina Wulandari','15A'),
    -> (15,15,'Dedi Permana','03B');
Query OK, 15 rows affected (0.007 sec)
Records: 15  Duplicates: 0  Warnings: 0

MariaDB [Bandara]> select * from Maskapai;
+-------------+--------------------+-----------------+------+
| id_maskapai | nama_maskapai      | negara_asal     | kode |
+-------------+--------------------+-----------------+------+
|           1 | Garuda Indonesia   | Indonesia       | GA   |
|           2 | Lion Air           | Indonesia       | JT   |
|           3 | Batik Air          | Indonesia       | ID   |
|           4 | Citilink           | Indonesia       | QG   |
|           5 | AirAsia            | Malaysia        | AK   |
|           6 | Malaysia Airlines  | Malaysia        | MH   |
|           7 | Singapore Airlines | Singapore       | SQ   |
|           8 | Emirates           | Uni Emirat Arab | EK   |
|           9 | Qatar Airways      | Qatar           | QR   |
|          10 | Etihad Airways     | Uni Emirat Arab | EY   |
|          11 | Japan Airlines     | Jepang          | JL   |
|          12 | ANA                | Jepang          | NH   |
|          13 | Thai Airways       | Thailand        | TG   |
|          14 | Scoot              | Singapore       | TR   |
|          15 | KLM Royal Dutch    | Belanda         | KL   |
+-------------+--------------------+-----------------+------+
15 rows in set (0.001 sec)

MariaDB [Bandara]> Select * from Penerbangan;
+----------------+-------------+--------------+----------+------------+
| id_penerbangan | id_maskapai | tujuan       | jadwal   | tanggal    |
+----------------+-------------+--------------+----------+------------+
|              1 |           1 | Jakarta      | 08:00:00 | 2025-01-10 |
|              2 |           2 | Surabaya     | 09:30:00 | 2025-01-10 |
|              3 |           3 | Denpasar     | 10:15:00 | 2025-01-10 |
|              4 |           4 | Makassar     | 11:45:00 | 2025-01-10 |
|              5 |           5 | Kuala Lumpur | 12:30:00 | 2025-01-10 |
|              6 |           6 | Penang       | 15:00:00 | 2025-01-10 |
|              7 |           7 | Singapore    | 07:25:00 | 2025-01-11 |
|              8 |           8 | Dubai        | 21:00:00 | 2025-01-11 |
|              9 |           9 | Doha         | 22:10:00 | 2025-01-11 |
|             10 |          10 | Abu Dhabi    | 23:15:00 | 2025-01-11 |
|             11 |          11 | Tokyo        | 06:45:00 | 2025-01-12 |
|             12 |          12 | Osaka        | 13:20:00 | 2025-01-12 |
|             13 |          13 | Bangkok      | 14:30:00 | 2025-01-12 |
|             14 |          14 | Singapore    | 16:40:00 | 2025-01-12 |
|             15 |          15 | Amsterdam    | 00:15:00 | 2025-01-12 |
+----------------+-------------+--------------+----------+------------+
15 rows in set (0.001 sec)

MariaDB [Bandara]> Select * from Penumpang;
+--------------+----------------+----------------+-------------+
| id_penumpang | id_penerbangan | nama_penumpang | nomor_kursi |
+--------------+----------------+----------------+-------------+
|            1 |              1 | Aulia Rahman   | 12A         |
|            2 |              2 | Rizky Putra    | 14B         |
|            3 |              3 | Siti Aisyah    | 10C         |
|            4 |              4 | Bimo Pratama   | 08D         |
|            5 |              5 | Putri Lestari  | 16F         |
|            6 |              6 | Fajar Nugraha  | 09A         |
|            7 |              7 | Hana Safitri   | 07C         |
|            8 |              8 | Dewi Anggraini | 02A         |
|            9 |              9 | Randy Maulana  | 05B         |
|           10 |             10 | Winda Kartika  | 13D         |
|           11 |             11 | Adit Mahendra  | 04A         |
|           12 |             12 | Nia Ayuningrum | 11C         |
|           13 |             13 | Samsul Bahri   | 17E         |
|           14 |             14 | Rina Wulandari | 15A         |
|           15 |             15 | Dedi Permana   | 03B         |
+--------------+----------------+----------------+-------------+
15 rows in set (0.002 sec)

MariaDB [Bandara]> Select * from Maskapai
    -> Where negara_asal = 'Indonesia';
+-------------+------------------+-------------+------+
| id_maskapai | nama_maskapai    | negara_asal | kode |
+-------------+------------------+-------------+------+
|           1 | Garuda Indonesia | Indonesia   | GA   |
|           2 | Lion Air         | Indonesia   | JT   |
|           3 | Batik Air        | Indonesia   | ID   |
|           4 | Citilink         | Indonesia   | QG   |
+-------------+------------------+-------------+------+
4 rows in set (0.001 sec)

MariaDB [Bandara]> Select * from Penerbangan
    -> Where tujuan = 'Surabaya';
+----------------+-------------+----------+----------+------------+
| id_penerbangan | id_maskapai | tujuan   | jadwal   | tanggal    |
+----------------+-------------+----------+----------+------------+
|              2 |           2 | Surabaya | 09:30:00 | 2025-01-10 |
+----------------+-------------+----------+----------+------------+
1 row in set (0.001 sec)

MariaDB [Bandara]> Select * from Penerbangan
    -> Where tanggal BETWEEN '2025-01-10' AND '2025-01-11';
+----------------+-------------+--------------+----------+------------+
| id_penerbangan | id_maskapai | tujuan       | jadwal   | tanggal    |
+----------------+-------------+--------------+----------+------------+
|              1 |           1 | Jakarta      | 08:00:00 | 2025-01-10 |
|              2 |           2 | Surabaya     | 09:30:00 | 2025-01-10 |
|              3 |           3 | Denpasar     | 10:15:00 | 2025-01-10 |
|              4 |           4 | Makassar     | 11:45:00 | 2025-01-10 |
|              5 |           5 | Kuala Lumpur | 12:30:00 | 2025-01-10 |
|              6 |           6 | Penang       | 15:00:00 | 2025-01-10 |
|              7 |           7 | Singapore    | 07:25:00 | 2025-01-11 |
|              8 |           8 | Dubai        | 21:00:00 | 2025-01-11 |
|              9 |           9 | Doha         | 22:10:00 | 2025-01-11 |
|             10 |          10 | Abu Dhabi    | 23:15:00 | 2025-01-11 |
+----------------+-------------+--------------+----------+------------+
10 rows in set (0.073 sec)

MariaDB [Bandara]> Select * from Penerbangan
    -> Where jadwal BETWEEN '08:00:00' AND '12:00:00';
+----------------+-------------+----------+----------+------------+
| id_penerbangan | id_maskapai | tujuan   | jadwal   | tanggal    |
+----------------+-------------+----------+----------+------------+
|              1 |           1 | Jakarta  | 08:00:00 | 2025-01-10 |
|              2 |           2 | Surabaya | 09:30:00 | 2025-01-10 |
|              3 |           3 | Denpasar | 10:15:00 | 2025-01-10 |
|              4 |           4 | Makassar | 11:45:00 | 2025-01-10 |
+----------------+-------------+----------+----------+------------+
4 rows in set (0.001 sec)# NurulAuliaRamadhani_BasisData
