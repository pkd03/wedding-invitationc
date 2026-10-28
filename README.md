# Hướng Dẫn Sử Dụng & Tùy Chỉnh Thiệp Cưới Online (Wedding Invitation)

Trang web thiệp cưới tĩnh được xây dựng với **HTML5, Tailwind CSS (CDN) và JavaScript thuần**, giao diện chuẩn **Mobile-first**, phong cách **Pastel & Champagne Gold** sang trọng.

---

## 📁 Cấu trúc thư mục
```text
/
├── index.html   # File mã nguồn toàn bộ giao diện, âm nhạc, hiệu ứng & kịch bản
└── README.md    # Hướng dẫn chi tiết tùy chỉnh và xuất bản (Deploy)
```

---

## 🛠️ Hướng Dẫn Tùy Chỉnh Nội Dung (Trong file `index.html`)

Bạn có thể mở file `index.html` bằng bất kỳ trình soạn thảo nào (VS Code, Notepad, Sublime Text...) và tìm các mục sau để chỉnh sửa:

### 1. Thay đổi tên Cô Dâu & Chú Rể
- Tìm từ khóa `Minh Quân` và `Thùy Chi` trong file `index.html` và thay bằng tên thật của hai bạn (ở các phần: Màn hình mở thiệp, Banner chính, Giới thiệu gia đình, Footer).

### 2. Thay đổi ngày cưới & Bộ đếm ngược (Countdown Timer)
- Đến dòng **JavaScript** (gần cuối file):
  ```javascript
  const WEDDING_DATE = new Date("2026-11-28T09:00:00+07:00").getTime();
  ```
  Thay `"2026-11-28T09:00:00+07:00"` thành ngày & giờ cưới của bạn theo định dạng `YYYY-MM-DDTHH:mm:ss+07:00`.

### 3. Thay đổi hình ảnh & Album ảnh cưới
- Tìm thẻ `<img>` của ảnh đại diện và mảng `galleryImages` trong phần script:
  ```javascript
  const galleryImages = [
    {
      src: "link_anh_1.jpg",
      caption: "Mô tả ảnh 1"
    },
    // ...
  ];
  ```
  > **Mẹo:** Bạn có thể upload ảnh lên [Imgur](https://imgur.com), [Postimages](https://postimages.org) hoặc tạo thư mục `images/` ngay trong dự án rồi điền đường dẫn tương đối (ví dụ: `images/anh-1.jpg`).

### 4. Thay đổi mã QR Mừng Cưới (VietQR)
- Bạn có thể tạo link ảnh QR ngân hàng tự động theo chuẩn **VietQR** siêu tiện lợi:
  ```html
  <!-- Cú pháp: https://img.vietqr.io/image/<Mã-Ngân-Hàng>-<Số-Tài-Khoản>-compact.png -->
  <!-- Ví dụ MB Bank: -->
  <img src="https://img.vietqr.io/image/MB-0987654321-compact.png?accountName=TRAN%20MINH%20QUAN" alt="QR MB Bank">
  
  <!-- Ví dụ Techcombank: -->
  <img src="https://img.vietqr.io/image/TCB-1903888888-compact.png?accountName=NGUYEN%20THUY%20CHI" alt="QR Techcombank">
  ```
- Thay đổi số tài khoản hiển thị và số trong hàm `copyToClipboard('SỐ_TÀI_KHOẢN', this)`.

### 5. Thay đổi nhạc nền (Background Music)
- Tìm thẻ `<audio id="wedding-music">`:
  ```html
  <source src="đường_dẫn_file_nhac.mp3" type="audio/mpeg">
  ```
  Bạn có thể thay bằng file `.mp3` bạn yêu thích (để cùng thư mục hoặc dán link online).

### 6. Tích hợp lưu RSVP vào Google Sheets (Tùy chọn)
Hiện tại form RSVP lưu dữ liệu trực tiếp vào bộ nhớ trình duyệt `localStorage` và hiển thị sổ lưu bút ngay lập tức. Nếu muốn thu thập danh sách khách mời về file Excel / Google Sheets:
- Tạo một Google Form hoặc Formspree (miễn phí tại [formspree.io](https://formspree.io)).
- Đặt thuộc tính `action="URL_FORMSPREE"` và `method="POST"` trong thẻ `<form id="rsvp-form">`.

---

## 🚀 Hướng Dẫn Deploy (Đưa lên mạng hoàn toàn miễn phí)

### Cách 1: Netlify Drop (Nhanh nhất - Không cần tài khoản hoặc chỉ mất 30 giây)
1. Truy cập [app.netlify.com/drop](https://app.netlify.com/drop).
2. Kéo thả toàn bộ thư mục chứa file `index.html` vào khung tải lên của Netlify.
3. Trang web sẽ trực tiếp online trong vòng 5 giây kèm đường link dạng `https://ten-ngau-nhien.netlify.app`. Bạn có thể đổi tên miền con theo ý muốn trong phần *Site settings > Change site name*.

### Cách 2: Vercel
1. Đăng nhập [vercel.com](https://vercel.com).
2. Chọn **Add New Project** -> Import repository từ GitHub (hoặc dùng Vercel CLI: gõ lệnh `npx vercel` trong thư mục này).
3. Bấm **Deploy**.

### Cách 3: GitHub Pages
1. Tạo một repository mới trên GitHub (chế độ Public).
2. Tải file `index.html` lên repository.
3. Vào mục **Settings** -> **Pages** -> Tại mục *Branch*, chọn `main` và thư mục `/ (root)` -> Bấm **Save**.
4. Sau 1 phút, thiệp cưới của bạn sẽ có link: `https://<ten-user>.github.io/<ten-repo>/`.

---
*Chúc hai bạn có một ngày cưới thật trọn vẹn, ngập tràn hạnh phúc và đong đầy yêu thương!* ❤️

