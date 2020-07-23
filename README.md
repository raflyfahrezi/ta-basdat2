## Source Code

#### Table Pasien
```mysql
create table pasien (
    id_pasien int primary key ,
    nama_pasien varchar(50)
);
```
#### Table Dokter
```mysql
create table dokter (
    nik char(20) primary key ,
    nama_dokter varchar(50)
);
```
#### Table Tindakan
```mysql
create table tindakan (
    id_tindakan int primary key  ,
    nama varchar(30),
    harga int(6)
);
```
#### Table Penjualan
```mysql
create table penjualan (
    no_resep char(5) primary key ,
    no_nota char(8)
);
```
#### Table Obat
```mysql
create table obat (
    id_obat int(6) primary key ,
    nama_obat varchar(25),
    harga int(6)
);
```
#### Table Tindak
```mysql
create table tindak (
    id_tindakan int(11) primary key ,
    no_nota char(8),

    foreign key (id_tindakan) references tindakan(id_tindakan) on update cascade on delete cascade
);
```
#### Table Jual
```mysql
create table jual (
    no_resep char(5) primary key ,
    id_obat int(6),
    qty int,

    foreign key (no_resep) references penjualan(no_resep) on update cascade on delete cascade ,
    foreign key (id_obat) references obat(id_obat) on update cascade on delete cascade
);
```
#### Table Pemeriksaan
```mysql
create table pemeriksaan (
    no_nota char(8) primary key,
    id_pasien int(11),
    nik char(20),
    diskon int,
    tanggal date,

    foreign key (id_pasien) references pasien(id_pasien) on update cascade on delete cascade ,
    foreign key (nik) references dokter(nik) on update cascade on delete cascade
);
```
