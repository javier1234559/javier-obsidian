---
Created: 01:34 20-10-2024
tags:
  - issue
---
Link relate:
- 

---

TLDR:
- Compound Pattern:
    - Tập trung vào việc xây dựng các component có mối quan hệ chặt chẽ và phụ thuộc lẫn nhau.
    - Thường được sử dụng để tạo ra các component phức tạp với API linh hoạt, cho phép người dùng tùy chỉnh cách sử dụng và hiển thị.
    - Ví dụ điển hình là các component như Menu, Form, hay Tabs.
- Composite Pattern:
    - Tập trung vào việc tạo ra một cấu trúc cây của các component, cho phép xử lý các component đơn lẻ và nhóm component một cách thống nhất.
    - Thường được sử dụng để xây dựng các layout phức tạp hoặc cấu trúc dữ liệu dạng cây.
    - Ví dụ điển hình là các component layout như Grid system hay Tree view.

## Compound Pattern

1. Mục đích:
   - Tạo ra các component có quan hệ chặt chẽ và phụ thuộc lẫn nhau.
   - Cung cấp API linh hoạt cho người dùng component.

2. Đặc điểm:
   - Các component con thường được định nghĩa như thuộc tính tĩnh của component cha.
   - Sử dụng React Context để chia sẻ state giữa các component con.
   - Cho phép tùy chỉnh cấu trúc và thứ tự của các component con.

3. Ví dụ:
   ```jsx
   const Menu = ({ children }) => {
     const [activeIndex, setActiveIndex] = useState(0);
     return (
       <MenuContext.Provider value={{ activeIndex, setActiveIndex }}>
         {children}
       </MenuContext.Provider>
     );
   };
   Menu.Item = ({ children, index }) => {
     const { activeIndex, setActiveIndex } = useContext(MenuContext);
     return (
       <div onClick={() => setActiveIndex(index)}>
         {children}
       </div>
     );
   };

   // Sử dụng
   <Menu>
     <Menu.Item index={0}>Home</Menu.Item>
     <Menu.Item index={1}>About</Menu.Item>
   </Menu>
   ```

## Composite Pattern

1. Mục đích:
   - Tạo ra cấu trúc cây của các component.
   - Cho phép xử lý các component đơn lẻ và nhóm component theo cách thống nhất.

2. Đặc điểm:
   - Định nghĩa giao diện chung cho tất cả các component (lá và nhánh).
   - Cho phép xây dựng cấu trúc phức tạp từ các component đơn giản.
   - Thường được sử dụng để tạo ra các layout hoặc cấu trúc dữ liệu phức tạp.

3. Ví dụ:
   ```jsx
   const Container = ({ children }) => <div>{children}</div>;
   const Item = ({ content }) => <div>{content}</div>;

   // Sử dụng
   <Container>
     <Item content="Item 1" />
     <Container>
       <Item content="Nested Item 1" />
       <Item content="Nested Item 2" />
     </Container>
   </Container>
   ```

## Sự khác biệt chính

1. Mục đích:
   - Compound: Tạo ra API linh hoạt cho các component có quan hệ chặt chẽ.
   - Composite: Xây dựng cấu trúc cây của các component có thể lồng nhau.

2. Quan hệ giữa các component:
   - Compound: Các component con thường phụ thuộc vào component cha.
   - Composite: Các component có thể độc lập và được sử dụng một cách nhất quán.

3. Sử dụng state:
   - Compound: Thường sử dụng shared state thông qua React Context.
   - Composite: Mỗi component có thể quản lý state của riêng mình.

4. Linh hoạt:
   - Compound: Linh hoạt trong việc tùy chỉnh hành vi và giao diện.
   - Composite: Linh hoạt trong việc xây dựng cấu trúc phức tạp.