# 📧 Hướng dẫn Setup EmailJS cho Form Liên hệ

## 🚀 Bước 1: Tạo tài khoản EmailJS

1. Truy cập [https://www.emailjs.com/](https://www.emailjs.com/)
2. Đăng ký tài khoản miễn phí
3. Xác thực email

## ⚙️ Bước 2: Tạo Email Service

1. Vào **Email Services** trong dashboard
2. Click **Add New Service**
3. Chọn **Gmail** (hoặc email provider khác)
4. Đăng nhập Gmail của bạn (`nvngon2604@gmail.com`)
5. Copy **Service ID** (ví dụ: `service_xxxxxxx`)

## 📝 Bước 3: Tạo Email Template

1. Vào **Email Templates**
2. Click **Create New Template**
3. Thiết lập template như sau:

### Template Settings:
- **Template Name**: `portfolio_contact`
- **Subject**: `{{subject}} - Liên hệ từ Portfolio`

### Template Content:
```html
Chào Nguyễn Văn Ngôn,

Bạn có tin nhắn mới từ portfolio:

Tên: {{from_name}}
Email: {{from_email}}
Chủ đề: {{subject}}

Nội dung:
{{message}}

---
Tin nhắn được gửi từ portfolio website.
Reply to: {{reply_to}}
```

4. Save template và copy **Template ID** (ví dụ: `template_xxxxxxx`)

## 🔑 Bước 4: Lấy Public Key

1. Vào **Account** → **General**
2. Copy **Public Key** (ví dụ: `xxxxxxxxxxxxxxxx`)

## 🔧 Bước 5: Cập nhật Code

Mở file `script.js` và thay thế các giá trị sau:

```javascript
// Dòng 3: Thay YOUR_PUBLIC_KEY
emailjs.init("YOUR_PUBLIC_KEY"); 
// Thành:
emailjs.init("xxxxxxxxxxxxxxxx"); // Public key của bạn

// Dòng 184: Thay YOUR_SERVICE_ID và YOUR_TEMPLATE_ID
emailjs.send('YOUR_SERVICE_ID', 'YOUR_TEMPLATE_ID', templateParams)
// Thành:
emailjs.send('service_xxxxxxx', 'template_xxxxxxx', templateParams)
```

## ✅ Bước 6: Test Form

1. Mở website portfolio
2. Điền form liên hệ
3. Gửi tin nhắn
4. Kiểm tra email `nvngon2604@gmail.com`

## 🎯 Tính năng đã tích hợp:

### ✅ Validation:
- Kiểm tra đầy đủ thông tin
- Validate email format
- Hiển thị thông báo lỗi

### ✅ UX Features:
- Loading spinner khi gửi
- Disable button khi đang gửi
- Thông báo thành công/lỗi
- Reset form sau khi gửi thành công

### ✅ Email Content:
- Tên người gửi
- Email người gửi
- Chủ đề
- Nội dung tin nhắn
- Reply-to email

## 🔒 Bảo mật:

- EmailJS sử dụng API key công khai (an toàn)
- Không lưu trữ thông tin nhạy cảm
- Rate limiting tự động
- Spam protection

## 📊 Monitoring:

- Theo dõi email trong EmailJS dashboard
- Xem logs gửi email
- Thống kê số lượng email

## 🆘 Troubleshooting:

### Lỗi thường gặp:
1. **Invalid Service ID**: Kiểm tra Service ID
2. **Invalid Template ID**: Kiểm tra Template ID  
3. **Invalid Public Key**: Kiểm tra Public Key
4. **Email not received**: Kiểm tra spam folder

### Debug:
- Mở Developer Tools (F12)
- Xem Console để debug
- Kiểm tra Network tab

---

**Lưu ý**: EmailJS miễn phí cho 200 email/tháng. Đủ cho portfolio cá nhân!
