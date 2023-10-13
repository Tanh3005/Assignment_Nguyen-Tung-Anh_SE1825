# Assignment_Nguyen-Tung-Anh_SE1825

--CREATE DATABASE QuanLyDangKyHocPhan
--go

--USE QuanLyDangKyHocPhan
--go

--Tạo bảng Sinh Viên
CREATE TABLE SinhVien (
    MaSinhVien INT PRIMARY KEY,
    HoTen NVARCHAR(50),
    Email NVARCHAR(50)
)
go

--Tạo bảng Môn Học
CREATE TABLE MonHoc (
    MaMonHoc INT PRIMARY KEY,
    TenMonHoc NVARCHAR(50),
    SoTinChi INT
)
go

-- Tạo bảng Giáo viên
CREATE TABLE GiaoVien (
    MaGiaoVien INT PRIMARY KEY,
    HoTen NVARCHAR(50),
    Email NVARCHAR(50)
)
go

-- Tạo bảng HocKy
CREATE TABLE HocKy (
    MaHocKy INT PRIMARY KEY,
    TenHocKy NVARCHAR(50)
)
go

-- Tạo bảng DangKyHocPhan
CREATE TABLE DangKyHocPhan (
    ID INT PRIMARY KEY,
    MaSinhVien INT,
    MaMonHoc INT,
    MaHocKy INT,
    FOREIGN KEY (MaSinhVien) REFERENCES SinhVien(MaSinhVien),
    FOREIGN KEY (MaMonHoc) REFERENCES MonHoc(MaMonHoc),
    FOREIGN KEY (MaHocKy) REFERENCES HocKy(MaHocKy)
)
go

-- Tạo bảng PhanCongGiangDay
CREATE TABLE PhanCongGiangDay (
    ID INT PRIMARY KEY,
    MaGiaoVien INT,
    MaMonHoc INT,
    MaHocKy INT,
    FOREIGN KEY (MaGiaoVien) REFERENCES GiaoVien(MaGiaoVien),
    FOREIGN KEY (MaMonHoc) REFERENCES MonHoc(MaMonHoc),
    FOREIGN KEY (MaHocKy) REFERENCES HocKy(MaHocKy)
)
go

--Tạo dữ liệu
INSERT INTO SinhVien (MaSinhVien, HoTen, Email)
VALUES 
    (1, 'Nguyen Van A', 'nguyenvana@gmail.com'),
    (2, 'Tran Thi B', 'tranthib@gmail.com'),
    (3, 'Le Van C', 'levanc@gmail.com');
go

INSERT INTO MonHoc (MaMonHoc, TenMonHoc, SoTinChi)
VALUES 
    (101, 'Toán', 4),
    (102, 'Văn', 3),
    (103, 'Lý', 4);
go

INSERT INTO GiaoVien (MaGiaoVien, HoTen, Email)
VALUES 
    (501, 'Nguyễn Thị D', 'nguyenthid@gmail.com'),
    (502, 'Trần Văn E', 'tranve@gmail.com'),
    (503, 'Lê Thị F', 'lethif@gmail.com');
go

INSERT INTO HocKy (MaHocKy, TenHocKy)
VALUES 
    (201, 'Học kỳ 1'),
    (202, 'Học kỳ 2'),
    (203, 'Học kỳ hè');
go

INSERT INTO DangKyHocPhan (ID, MaSinhVien, MaMonHoc, MaHocKy)
VALUES 
    (301, 1, 101, 201),
    (302, 2, 102, 202),
    (303, 3, 103, 202);
go

INSERT INTO PhanCongGiangDay (ID, MaGiaoVien, MaMonHoc, MaHocKy)
VALUES 
    (401, 501, 101, 201),
    (402, 502, 102, 202),
    (403, 503, 103, 202);
go

