---
Created: 15:33 19-12-2024
tags:
  - issue
---
Link relate:
- 

---

TLDR: 

Tôi sẽ giải thích các syntax cơ bản của Jest thông qua các ví dụ:

1. **Test Suite và Test Case cơ bản**
```javascript
describe('Nhóm test cho tính năng Login', () => {  // Test suite
  // Test case đơn lẻ
  test('Login thành công với email và password đúng', () => {
    expect(login('user@example.com', 'password123')).toBe(true);
  });

  // Có thể dùng it thay cho test - cùng ý nghĩa
  it('Báo lỗi khi password sai', () => {
    expect(login('user@example.com', 'wrong')).toBe(false);
  });
});
```

2. **Matchers phổ biến**
```javascript
test('Demo các matchers', () => {
  // So sánh bằng
  expect(2 + 2).toBe(4);               // So sánh chính xác
  expect({name: 'test'}).toEqual({name: 'test'});  // So sánh object

  // Kiểm tra truthiness
  expect(null).toBeNull();             // Kiểm tra null
  expect(undefined).toBeUndefined();   // Kiểm tra undefined
  expect(value).toBeTruthy();          // Kiểm tra truthy
  expect(value).toBeFalsy();           // Kiểm tra falsy

  // So sánh số
  expect(value).toBeGreaterThan(3);    // Lớn hơn
  expect(value).toBeLessThan(5);       // Nhỏ hơn
  expect(value).toBeGreaterThanOrEqual(3.5); // Lớn hơn hoặc bằng

  // Kiểm tra string
  expect('hello').toMatch(/ll/);       // Match với regex
  expect('hello').toContain('ell');    // Chứa substring

  // Kiểm tra array
  expect(['apple', 'banana']).toContain('apple');  // Chứa phần tử
  expect(array).toHaveLength(2);       // Kiểm tra độ dài

  // Kiểm tra exception
  expect(() => {
    throwError()
  }).toThrow();                        // Kiểm tra có throw error
});
```

3. **Setup và Teardown**
```javascript
describe('User API', () => {
  // Chạy một lần trước tất cả test
  beforeAll(() => {
    return initDatabase();
  });

  // Chạy trước mỗi test case
  beforeEach(() => {
    return initTestUser();
  });

  // Chạy sau mỗi test case
  afterEach(() => {
    return clearTestUser();
  });

  // Chạy một lần sau tất cả test
  afterAll(() => {
    return closeDatabase();
  });

  test('test case 1', () => {
    // test logic
  });
});
```

4. **Async Testing**
```javascript
// Promise
test('async test với promise', () => {
  return fetchData().then(data => {
    expect(data).toBe('data');
  });
});

// Async/Await
test('async test với async/await', async () => {
  const data = await fetchData();
  expect(data).toBe('data');
});

// Callback
test('async test với callback', done => {
  fetchData(data => {
    expect(data).toBe('data');
    done();
  });
});
```

5. **Mock Functions**
```javascript
test('mock function demo', () => {
  // Tạo mock function
  const mockFn = jest.fn();
  
  // Thiết lập giá trị trả về
  mockFn.mockReturnValue(42);
  
  // Hoặc mockImplementation
  mockFn.mockImplementation(scalar => scalar * 2);
  
  // Kiểm tra mock
  expect(mockFn).toHaveBeenCalled();           // Đã được gọi
  expect(mockFn).toHaveBeenCalledTimes(2);     // Số lần gọi
  expect(mockFn).toHaveBeenCalledWith(expect.any(Number)); // Kiểm tra tham số
});
```

6. **Snapshot Testing**
```javascript
test('snapshot demo', () => {
  const user = {
    name: 'John',
    age: 30
  };
  expect(user).toMatchSnapshot();
});
```

7. **Skip và Only**
```javascript
describe('test group', () => {
  test.skip('bỏ qua test này', () => {
    // không chạy
  });

  test.only('chỉ chạy test này', () => {
    // chỉ test này chạy trong nhóm
  });
});
```

Đây là những syntax cơ bản nhất của Jest. Việc nắm vững các syntax này sẽ giúp bạn viết test hiệu quả hơn. Bạn có thể hỏi thêm về bất kỳ phần nào bạn muốn tìm hiểu sâu hơn.