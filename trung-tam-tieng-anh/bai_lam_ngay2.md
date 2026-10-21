# BÀI LÀM – ÔN TẬP NGÀY 2

- **Họ tên: Nguyễn Quỳnh Chi**
- **Lớp:CNTT2**
- **Link repository:https://github.com/chiqn2k8elsa-cyber/HN-KS26-CNTT2_Nhap-mon-CNTT_OnTap-Ngay2**
- **Hệ điều hành (Windows/macOS):Windows**

## Bài 1. Lọc log thủ công

### Lệnh đã chạy

```shell
#### Get-content logs/access.log
#### select-string "ERROR" logs/access.log > logs/error_report.txt
#### get-content logs/error_report.txt

```

### 2 dòng lỗi đầu tiên trong error_report.txt

```text
logs\access.log:4:2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
logs\access.log:6:2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)

```

## Bài 2. Đếm bằng pipeline

### Lệnh

```shell
#### get-content logs/access.log | select-string "WARNING" | Measure-Object
#### get-content logs/payment.log | select-string "ERROR" | Measure-Object

```

### Kết quả đếm (Windows: giá trị Count; macOS: con số in ra)

```text
WARNING trong access.log: Count: 4
ERROR trong payment.log: Count: 3
```

## Bài 3. Chạy script auto_warning (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
#### Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
#### .\auto_warning.ps1

```

### Nội dung file logs/warning_report.txt

```text
=== CANH BAO THANH TOAN ===

2025-10-18 09:19:13 [WARNING] Cong thanh toan phan hoi cham
2025-10-18 09:28:16 [WARNING] Nhieu lan nhap sai ma OTP
2025-10-18 09:43:01 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:46:22 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:49:43 [WARNING] So du vi gan bang hoc phi


```

## Bài 4. Báo cáo tổng hợp

### Các lệnh đã chạy

```shell
#### ni logs/tong_hop_ngay2.txt
#### get-content logs/access.log | select-string "ERROR" >> logs/tong_hop_ngay2.txt
#### get-content logs/payment.log | select-string "WARNING" | Measure-Object >> logs/tong_hop_ngay2.txt

```

### Nội dung file logs/tong_hop_ngay2.txt

```text
=== TONG HOP ACCESS LOG ===

2025-10-18 08:17:59 [ERROR] Khong tim thay trang 
/lich-thi (404)
2025-10-18 08:25:55 [ERROR] Het thoi gian cho 
(timeout)
2025-10-18 08:33:51 [ERROR] Ket noi may chu du 
lieu that bai
2025-10-18 08:37:19 [ERROR] Ket noi may chu du 
lieu that bai
2025-10-18 08:49:43 [ERROR] Het thoi gian cho 
(timeout)
2025-10-18 08:53:11 [ERROR] Het thoi gian cho 
(timeout)




Count    : 5
Average  : 
Sum      : 
Maximum  : 
Minimum  : 
Property : 

```

## Bài 5. Câu hỏi ngắn

- **a)Lệnh ... > file và ... >> file khác nhau:**
**Lệnh ... > file là: ghi đè lên nội dung đã viết trước đó làm mất đi nội dung cũ thay thế nội dung mình vừa viết vào hoặc tạo file mới**
**Lệnh ... >> file là: ghi tiếp vào nội dung trước đó mà nội dung cũ vẫn được giữ nguyên**
- **b)Nếu lệnh thứ hai dùng > thay cho >>, nội dung file tong_hop_ngay2.txt thì sẽ đè lên nội dung đã viết trước đó làm mất dòng tiêu đề === TONG HOP ACCESS LOG ===** 
- **c)Vì đường dẫn tương đối giúp script chạy trên máy khác mà không cần sửa lại đường dẫn file**

## Tự chấm (điền sau khi có đáp án)

- **Điểm tự chấm:** ..../100
- **Lỗi mình đã mắc và cách sửa:**
