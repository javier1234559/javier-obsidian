---
Created: 13:09 18-08-2024
tags:
  - area
  - area/technology
---


### Prisma cli 
Tải về với lệnh  `yarn add -D prisma ``
chạy bằng lệnh `npx prisma init`

- **`prisma init`**: Khởi tạo dự án Prisma bằng cách tạo ra cấu trúc cơ bản cần thiết cho việc quản lý cơ sở dữ liệu.
- **`prisma generate`**: Tạo Prisma Client dựa trên schema hiện tại, giúp tương tác với cơ sở dữ liệu một cách an toàn và dễ dàng trong mã ứng dụng.
- **`prisma deploy`**: Áp dụng schema Prisma vào cơ sở dữ liệu, phù hợp với các cơ sở dữ liệu hỗ trợ migration như PostgreSQL, MySQL và SQLite.
- **`prisma migrate`**: Quản lý migration cơ sở dữ liệu, bao gồm tạo migration mới, áp dụng migration và rollback nếu cần.
- **`prisma db pull`**: Cập nhật schema Prisma để phản ánh trạng thái hiện tại của cơ sở dữ liệu, hữu ích khi muốn đồng bộ hóa schema với cơ sở dữ liệu hiện có không được quản lý ban đầu bởi Prisma.
- **`prisma db push`**: Áp dụng trực tiếp các thay đổi từ schema Prisma vào cơ sở dữ liệu mà không tạo migration, phương pháp đơn giản nhưng ít linh hoạt hơn so với sử dụng migration.
- **`prisma studio`**: Mở Prisma Studio, giao diện đồ họa cho phép xem và chỉnh sửa dữ liệu trong cơ sở dữ liệu.
- **`prisma validate`**: Kiểm tra schema Prisma theo tiêu chuẩn định dạng Prisma, đảm bảo schema đúng định dạng và tuân thủ quy định.
- **`prisma format`**: Định dạng lại schema Prisma theo hướng dẫn định dạng của Prisma, đảm bảo tính nhất quán và dễ đọc hơn.

### quan hệ trong prisma
The following Prisma schema includes every type of relation:

- one-to-one: `User` ↔ `Profile`
- one-to-many: `User` ↔ `Post`
- many-to-many: `Post` ↔ `Category`

```prisma
model User {
  id      Int      @id @default(autoincrement())
  posts   Post[]
  profile Profile?
}

model Profile {
  id     Int  @id @default(autoincrement())
  user   User @relation(fields: [userId], references: [id])
  userId Int  @unique // relation scalar field (used in the `@relation` attribute above)
}

model Post {
  id         Int        @id @default(autoincrement())
  author     User       @relation(fields: [authorId], references: [id])
  authorId   Int // relation scalar field  (used in the `@relation` attribute above)
  categories Category[]
}

model Category {
  id    Int    @id @default(autoincrement())
  posts Post[]
}

```