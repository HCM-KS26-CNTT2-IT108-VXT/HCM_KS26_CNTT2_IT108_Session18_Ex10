
# BÀI 10: ĐÁNH GIÁ ĐA GIẢI PHÁP XÁC THỰC ĐA YẾU TỐ (2FA)

## Phần 1: Phân tích 2 giải pháp xác thực

### Câu 1. Phân tích 3 yếu tố xác thực danh tính số.

- **Something You Know:** Thứ mình biết, ví dụ mật khẩu hoặc mã PIN.
- **Something You Have:** Thứ mình sở hữu, ví dụ điện thoại hoặc thiết bị bảo mật.
- **Something You Are:** Đặc điểm sinh học, ví dụ vân tay hoặc khuôn mặt.

Khi sử dụng 2FA:
- Mật khẩu thuộc yếu tố Something You Know.
- Mã OTP từ ứng dụng Authenticator thuộc yếu tố Something You Have.

### Câu 2. Giải thích nguyên lý hoạt động của TOTP.

- TOTP là thuật toán tạo mã OTP dựa trên thời gian.
- Ứng dụng và máy chủ cùng lưu một khóa bí mật.
- Hai bên sử dụng khóa bí mật và thời gian hiện tại để tạo mã giống nhau.
- Mã thường thay đổi sau mỗi 30 giây.

Authenticator vẫn tạo được mã khi bật Chế độ Máy bay vì không cần Internet hay sóng điện thoại, chỉ cần đồng hồ trên thiết bị hoạt động chính xác.

## Phần 2: Lập bảng so sánh và ra quyết định

### Câu 3. So sánh SMS OTP và TOTP Authenticator

| Tiêu chí | SMS OTP | TOTP Authenticator |
|---|---|---|
| Chống SIM Swapping và nghe lén SS7 | Kém, có thể bị chiếm đoạt số điện thoại hoặc nghe lén tin nhắn | Tốt hơn, không phụ thuộc SIM và mạng viễn thông |
| Sử dụng khi Offline / Nước ngoài | Cần sóng điện thoại để nhận mã | Tạo mã khi không có Internet hoặc sóng điện thoại |
| Độ tiện dụng và chi phí | Dễ sử dụng nhưng doanh nghiệp tốn phí gửi SMS | Dễ sử dụng, thường miễn phí |
| Rủi ro khi mất điện thoại | Có thể làm lại SIM nhưng vẫn có nguy cơ bị chiếm đoạt | Cần Backup Codes hoặc bản sao lưu an toàn để khôi phục |

### Câu 4. PixelForge Studio nên lựa chọn giải pháp nào? Vì sao?

PixelForge Studio nên chọn TOTP Authenticator làm phương thức xác thực cho đội ngũ kỹ sư.

Lý do:
- Bảo mật tốt hơn SMS OTP, hạn chế nguy cơ bị tấn công SIM Swapping.
- Có thể tạo mã khi không có Internet hoặc sóng điện thoại.
- Phù hợp với nhân viên thường xuyên đi công tác nước ngoài.
- Không tốn chi phí gửi tin nhắn SMS.

Đây là lựa chọn phù hợp để bảo vệ tài khoản GitHub Enterprise và hệ thống thanh toán của công ty.

## Phần 3: Quản lý rủi ro và Backup Codes

### Câu 5. Mục đích của Backup Codes, 2 vị trí lưu trữ an toàn và 1 sai lầm cần tránh.

**Mục đích:**

Backup Codes là các mã dự phòng dùng để đăng nhập khi bị mất điện thoại hoặc không thể sử dụng ứng dụng Authenticator.

**Hai vị trí lưu trữ an toàn:**

1. In ra giấy và cất trong két sắt tại văn phòng.
2. Lưu trong két sắt số Bitwarden đã được bảo vệ bằng mật khẩu mạnh.

**Sai lầm cần tránh:**

Không chụp ảnh hoặc gửi Backup Codes vào nhóm chat, mạng xã hội hay email thông thường vì có thể bị đánh cắp.



