# 🚀 Hướng dẫn deploy lên GitHub Pages

Repo này được cấu hình để chạy ngay lập tức tại `https://nhatminhtrange.github.io`.

## ✅ Cách 1 — Deploy bằng giao diện web (dễ nhất, không cần Git)

### Bước 1: Tạo repository mới
1. Đăng nhập GitHub với tài khoản **nhatminhtrange**
2. Truy cập: https://github.com/new
3. Đặt tên repo CHÍNH XÁC: **`nhatminhtrange.github.io`**
   - ⚠️ Tên phải khớp với username + `.github.io`, nếu không sẽ không hoạt động
4. Chọn **Public**
5. **KHÔNG** tích "Add a README" (vì mình sẽ upload sẵn)
6. Bấm **Create repository**

### Bước 2: Upload toàn bộ file
1. Trong repo vừa tạo, bấm **"uploading an existing file"** (hoặc "Add file" → "Upload files")
2. Kéo thả TẤT CẢ các file trong thư mục này vào:
   - `index.html`
   - `404.html`
   - `README.md`
   - `LICENSE`
   - `.nojekyll`  ← file ẩn, nhớ kéo cả file này (nếu không thấy, bấm Ctrl+H để hiện file ẩn)
3. Cuộn xuống, bấm **Commit changes**

### Bước 3: Bật GitHub Pages
1. Trong repo, vào tab **Settings** (góc phải trên cùng)
2. Cuộn xuống menu bên trái, bấm **Pages**
3. Phần "Build and deployment":
   - **Source**: chọn `Deploy from a branch`
   - **Branch**: chọn `main` / `/ (root)`
4. Bấm **Save**

### Bước 4: Chờ ~1-2 phút
Truy cập: **https://nhatminhtrange.github.io**

🎉 Xong!

---

## ✅ Cách 2 — Deploy bằng Git command line

Mở Terminal/CMD trong thư mục này và chạy:

```bash
# Khởi tạo Git
git init
git add .
git commit -m "Initial site"

# Đặt branch chính là main
git branch -M main

# Kết nối tới repo trên GitHub
# (Tạo repo rỗng tên nhatminhtrange.github.io trên github.com trước)
git remote add origin https://github.com/nhatminhtrange/nhatminhtrange.github.io.git

# Push
git push -u origin main
```

Sau đó vào **Settings → Pages** trên GitHub để bật như Bước 3 ở Cách 1.

---

## 🌐 Custom Domain (tuỳ chọn)

Nếu sau này bạn mua tên miền riêng (ví dụ `minhnhat.dev`):

1. Tạo file tên `CNAME` (không có đuôi mở rộng) trong repo
2. Nội dung file chỉ có 1 dòng: tên miền của bạn, ví dụ:
   ```
   minhnhat.dev
   ```
3. Cấu hình DNS ở nhà cung cấp tên miền:
   - Thêm 4 bản ghi A trỏ về:
     - `185.199.108.153`
     - `185.199.109.153`
     - `185.199.110.153`
     - `185.199.111.153`
   - Hoặc CNAME `www` → `nhatminhtrange.github.io`

---

## 📝 Cập nhật nội dung sau này

Chỉ cần sửa `index.html` rồi:

**Qua giao diện web:** Mở file trên GitHub → bấm cây bút (Edit) → sửa → Commit.

**Qua Git:**
```bash
git add .
git commit -m "Update content"
git push
```

GitHub Pages sẽ tự deploy lại sau ~1 phút.

---

## 🛠 Cấu trúc file

```
nhatminhtrange.github.io/
├── index.html       # Trang chính
├── 404.html         # Trang lỗi 404 (đồng bộ phong cách)
├── README.md        # Mô tả repo (hiện trên GitHub)
├── LICENSE          # Giấy phép MIT
├── .nojekyll        # Tắt Jekyll, serve HTML thuần
└── DEPLOY.md        # File này
```

## ❓ Gặp lỗi?

- **Web hiện trang lỗi/404 sau khi bật Pages:** Chờ 2-3 phút và refresh (Ctrl+Shift+R) để xoá cache.
- **Tên repo sai:** Phải CHÍNH XÁC là `nhatminhtrange.github.io`, không thêm dấu hay viết hoa.
- **File `.nojekyll` không thấy khi upload:** Trên máy Mac/Linux nhấn `Cmd+Shift+.` hoặc Windows bấm Ctrl+H để hiện file ẩn.
