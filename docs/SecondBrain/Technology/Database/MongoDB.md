---
Created: 21:34 27-09-2023
Link: 
tags:
  - secondbrain
  - secondbrain/technology
---

# MongoDB

### Cách thiết kế NOSQL

###  Một số lệnh truy vấn cơ bản

|Truy vấn|MongoDB|MySQL|
|---|---|---|
|Tạo DB|use db_name;|CREATE DATABASE db_name;|
|Xóa DB|db.dropDatabase();|DROP DATABASE db_name;|
|Tạo bảng|db.createCollection('t_name');|CREATE TABLE t_name (c1_name c1_type, c2_name c2_type ...);|
|Xóa bảng|db.t_name.drop();|DROP TABLE t_name;|
|Chèn bảng|db.t_name.insert({c1_name: c1_value, c2_name: c2_type, ...});|INSERT INTO t_name (c1_name, c2_name, ...) VALUES (c1_type, c2_type, ...);|
|Cập nhật|db.t_name.update({ _id: id_value }, { $set: { c_name: c_new_value } });|UPDATE t_name SET c_name = c_new_value WHERE id = c_id;|
|Xóa |db.t_name.remove({_id: id_value});|DELETE FROM t_name WHERE id = c_id;|
|Xóa all|db.t_name.deleteMany();|DELETE FROM t_name;|
|Tìm all|db.t_name.find();|SELECT * FROM t_name;|
|Tìm theo trường|db.t_name.find({c_name: c_value});|SELECT * FROM t_name WHERE c_name = c_value;|







--- 
# References
[MongoDB Tutorial (tutorialspoint.com)](https://www.tutorialspoint.com/mongodb/index.htm)
[Bắt đầu với NoSQL và MongoDB (viblo.asia)](https://viblo.asia/p/bat-dau-voi-nosql-va-mongodb-jvEla00zZkw)



--- 
# Links to this page

