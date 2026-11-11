# Hướng dẫn: Landing page sản phẩm + mã QR cho triển lãm (GitHub Pages)

Tài liệu này ghi lại **toàn bộ quy trình từ đầu đến cuối** đã dùng để đưa 4 trang giới thiệu sản phẩm (FOLLOWER, INSIDER, VERTI AI, CITADEL) lên mạng và tạo mã QR in standee, catalogue, tờ rơi. Làm lại cho sản phẩm/triển lãm khác chỉ cần đi đúng các bước bên dưới.

---

## 0. Hiện trạng

| Sản phẩm | Link (QR trỏ tới) | File trong repo | Mã QR |
|---|---|---|---|
| FOLLOWER | https://toancodervn.github.io/trienlambk/follower/ | `follower/index.html` | `qr/qr_follower.svg` |
| INSIDER | https://toancodervn.github.io/trienlambk/insider/ | `insider/index.html` | `qr/qr_insider.svg` |
| VERTI AI | https://toancodervn.github.io/trienlambk/vertiai/ | `vertiai/index.html` | `qr/qr_vertiai.svg` |
| CITADEL | https://toancodervn.github.io/trienlambk/citadel/ | `citadel/index.html` | `qr/qr_citadel.svg` |

<p>
  <img src="qr/qr_follower.svg" width="160" alt="QR FOLLOWER">
  <img src="qr/qr_insider.svg" width="160" alt="QR INSIDER">
  <img src="qr/qr_vertiai.svg" width="160" alt="QR VERTI AI">
  <img src="qr/qr_citadel.svg" width="160" alt="QR CITADEL">
</p>

*(Từ trái sang: FOLLOWER, INSIDER, VERTI AI, CITADEL)*

- Repo: `toancoderVN/trienlambk` (Public), GitHub Pages bật từ nhánh `main`, thư mục `/ (root)`.
- File gửi nhà in: **`.svg`** trong thư mục `qr/`. File `.png` chỉ để xem trước / chèn slide.
- Cả 4 mã là **QR tĩnh**, mức sửa lỗi **Q (~25%)**, đã quét thử bằng 2 bộ giải mã (OpenCV, ZXing).
- Font các trang: chữ thường **Be Vietnam Pro**, tiêu đề **Lora** (nhúng sẵn trong file, đủ dấu tiếng Việt).

### Ấn phẩm in đã làm

| Ấn phẩm | File | Ghi chú |
|---|---|---|
| Standee A5 (15 × 19 cm) | `Standee_FOLLOWER_HORSEAI.pptx`, `Standee_INSIDER_HORSEAI.pptx`, `Standee_VERTIAI_HORSEAI.pptx`, `Standee_CITADEL_HORSEAI.pptx` | Từ file `Template Standee A5 san pham trien lam (15 x 19 cm).pptx`: điền tên, dòng mô tả, đơn vị triển lãm và mã QR (cạnh ~3,4 cm) |
| Catalogue A4 2 mặt | `Poster Follower A4 (QR).pdf`, `Poster Insider A4 (QR).pdf`, `Poster Verti AI – A4 2 mặt (QR).pdf` | Mặt sau: khối "Giấy chứng nhận quyền tác giả" đã thay bằng mã QR (cạnh ~2,9 cm) |

*(Các file này lưu trên máy, trong folder chuẩn bị triển lãm; không đưa lên repo.)*

---

## 1. Trang có chạy liên tục không? Khi nào thì dừng?

**Có, chạy liên tục, không cần làm gì thêm.** GitHub Pages chỉ phục vụ file tĩnh (HTML/CSS/JS/ảnh), không có server riêng, nên:

- Không "ngủ" khi ít người vào, không có thời gian dùng thử, không hết hạn.
- Không tốn phí (tài khoản miễn phí + repo Public).
- Mã QR là QR **tĩnh**: link nằm thẳng trong mã, không đi qua dịch vụ trung gian nào, nên mã không bao giờ "chết".

**Trang/QR chỉ ngừng hoạt động khi chính mình làm một trong các việc sau:**

| Hành động | Hậu quả |
|---|---|
| Đổi tên tài khoản GitHub `toancoderVN` | Cả 4 link đổi → **toàn bộ QR hỏng** |
| Đổi tên repo `trienlambk` | Cả 4 link đổi → **toàn bộ QR hỏng** |
| Đổi tên / xóa thư mục `follower/`, `insider/`, `vertiai/`, `citadel/` | QR của sản phẩm đó hỏng (404) |
| Đổi tên / xóa file `index.html` trong thư mục | QR của sản phẩm đó hỏng |
| Chuyển repo sang **Private** | Tài khoản miễn phí sẽ tắt Pages → **toàn bộ QR hỏng** |
| Tắt GitHub Pages (Settings → Pages → None) | **Toàn bộ QR hỏng** |
| Xóa repo / xóa tài khoản, hoặc tài khoản bị khóa | **Toàn bộ QR hỏng** |

Các trường hợp ngoài ý muốn (rất hiếm): GitHub gặp sự cố toàn cầu (thường vài phút), hoặc vượt giới hạn băng thông mềm 100 GB/tháng (mỗi trang ~1–2 MB → khoảng 50.000+ lượt mở/tháng, dư sức cho triển lãm).

> 💡 Sửa **nội dung** bên trong `index.html` thì thoải mái, QR không bị ảnh hưởng. Chỉ không được đổi **tên/đường dẫn**.

### Mã QR đã cố định chưa? In tờ rơi được chưa?

**Đã cố định, in được.** Mã QR chỉ chứa đường dẫn, không chứa nội dung trang, nên sau này sửa trang thế nào thì mã đã in vẫn dùng được. Trước khi in số lượng lớn, làm theo **mục 9** (thông số in) và **mục 14** (checklist).

---

## 2. Làm lại từ đầu: tổng quan

```
[QR in trên poster] → https://<username>.github.io/<repo>/<thu-muc>/ → <thu-muc>/index.html trong repo
      (cố định)                       (cố định)                          (nội dung sửa được)
```

1. Chuẩn bị tài khoản GitHub + file HTML.
2. Chốt tên: username, repo, thư mục cho từng sản phẩm.
3. Tạo repo Public.
4. Đưa file HTML vào đúng `<thu-muc>/index.html`.
5. Bật GitHub Pages.
6. Kiểm tra link.
7. Tạo mã QR tĩnh và quét thử.
8. Gửi in.

---

## 3. Chuẩn bị

### 3.1. Tài khoản GitHub
- Tài khoản miễn phí tại https://github.com là đủ.
- Nên dùng tài khoản **ổn định lâu dài**, không có kế hoạch đổi tên.
- Nếu dùng tài khoản tổ chức (org) mà các repo khác đang Private: repo landing page vẫn phải để **Public** (trừ khi org dùng gói GitHub Team/Enterprise).

### 3.2. File HTML
- Mỗi sản phẩm **một file HTML**.
- Tốt nhất là file **tự chứa** (font, ảnh, CSS nhúng sẵn trong file, như 4 file hiện tại) → không lo lỗi đường dẫn.
- Nếu có file đi kèm (CSS, ảnh), dùng **đường dẫn tương đối**: `./style.css`, `./images/a.jpg`. **Không** dùng `/style.css` (trang nằm trong thư mục con nên sẽ lỗi).
- Nén ảnh xuống vài trăm KB, vì khách quét bằng 4G trong hội trường.

### 3.3. Chốt tên (sau khi in QR thì KHÔNG được đổi)

| Thông tin | Đang dùng | Gợi ý |
|---|---|---|
| Username | `toancoderVN` | Trong link GitHub tự viết thường: `toancodervn` |
| Tên repo | `trienlambk` | Ngắn, viết thường, không dấu, không khoảng trắng |
| Thư mục từng sản phẩm | `follower`, `insider`, `vertiai`, `citadel` | Ngắn, viết thường, không dấu |

> 💡 Link càng ngắn → mã QR càng thưa → càng dễ quét.

---

## 4. Tạo repo

1. Vào https://github.com/new (hoặc nút **+** → **New repository**).
2. **Owner**: chọn tài khoản (cá nhân hoặc tổ chức).
3. **Repository name**: `trienlambk`.
4. **Description** (tùy chọn): ghi chú nhắc "QR đã in – không đổi tên repo/thư mục".
5. **Visibility**: **Public**.
6. **Add README**: bật **On** (để repo có sẵn nhánh `main`).
7. Bấm **Create repository**.

---

## 5. Đưa file HTML lên đúng thư mục

Mục tiêu là cấu trúc:

```
trienlambk/
├── follower/index.html
├── insider/index.html
├── vertiai/index.html
├── citadel/index.html
├── qr/  (ảnh mã QR)
├── HUONG-DAN.md
└── README.md
```

### Cách A (đã dùng): upload rồi đổi tên trên web — không cần cài gì

1. Trong repo, bấm **Add file → Upload files**.
2. Kéo thả file, ví dụ `FOLLOWER_gioi_thieu_san_pham.html`, rồi bấm **Commit changes**.
3. Bấm vào file vừa upload → bấm biểu tượng **bút chì (Edit)**.
4. Ở ô tên file phía trên, xóa tên cũ rồi gõ **`follower/index.html`**. Dấu `/` sẽ tự tạo thư mục `follower`.
5. Bấm **Commit changes…** → **Commit changes**.
6. Lặp lại cho từng sản phẩm (`insider/index.html`, `vertiai/index.html`, `citadel/index.html`).

### Cách B: kéo thả nguyên thư mục
Trên máy, tạo sẵn thư mục `follower/` chứa file `index.html` (đổi tên file trước), rồi kéo **cả thư mục** vào trang **Upload files**. GitHub giữ nguyên cấu trúc thư mục.

### Cách C: dùng Git (cho người quen dòng lệnh)
```bash
git clone https://github.com/toancoderVN/trienlambk.git
cd trienlambk
mkdir -p follower && cp /duong/dan/FOLLOWER_gioi_thieu_san_pham.html follower/index.html
git add . && git commit -m "Them trang follower" && git push
```

> ⚠️ Tên file trong thư mục **bắt buộc** là `index.html` (viết thường), thì link `.../follower/` mới mở thẳng được trang.

---

## 6. Bật GitHub Pages

1. Vào repo → **Settings** → **Pages** (cột trái).
2. **Source**: `Deploy from a branch`.
3. **Branch**: chọn `main`, thư mục `/ (root)` → **Save**.
4. Đợi 1–2 phút. Có thể theo dõi ở tab **Actions** (workflow `pages-build-deployment` chuyển sang ✅).

Từ giờ, **mỗi lần commit** lên `main`, trang tự cập nhật sau khoảng 1 phút.

---

## 7. Kiểm tra link

Mở trên điện thoại (dùng **4G**, không dùng wifi):

```
https://toancodervn.github.io/trienlambk/follower/
https://toancodervn.github.io/trienlambk/insider/
https://toancodervn.github.io/trienlambk/vertiai/
https://toancodervn.github.io/trienlambk/citadel/
```

Link chạy đúng rồi mới tạo QR.

---

## 8. Tạo mã QR tĩnh

> ⚠️ **Bắt buộc QR tĩnh (static).** Nhiều web tạo QR miễn phí mặc định tạo **QR động**: link đi qua server của họ và **ngừng chạy sau 7–14 ngày** nếu không trả phí. Không dùng loại này.

### Cách A (đã dùng): Python + segno, có tự kiểm tra

```bash
pip install segno opencv-python-headless zxing-cpp
```

```python
import segno, cv2, zxingcpp

links = {
    "follower": "https://toancodervn.github.io/trienlambk/follower/",
    "insider":  "https://toancodervn.github.io/trienlambk/insider/",
    "vertiai":  "https://toancodervn.github.io/trienlambk/vertiai/",
    "citadel":  "https://toancodervn.github.io/trienlambk/citadel/",
}

for name, url in links.items():
    qr = segno.make(url, error="q")                 # mức sửa lỗi Q (~25%)
    qr.save(f"qr_{name}.svg", scale=10, border=4)   # vector -> gửi nhà in
    qr.save(f"qr_{name}.png", scale=30, border=4)   # ảnh xem trước

    # Kiểm tra: đọc lại ảnh bằng 2 bộ giải mã khác nhau
    img = cv2.imread(f"qr_{name}.png")
    ok1 = cv2.QRCodeDetector().detectAndDecode(img)[0] == url
    ok2 = [r.text for r in zxingcpp.read_barcodes(img)] == [url]
    print(name, "OpenCV:", ok1, "| ZXing:", ok2)
```

Nếu một mã chỉ đọc được bằng 1 bộ giải mã, thử đổi mẫu mặt nạ: `segno.make(url, error="q", mask=0)` (thử các số 0–7) cho tới khi cả hai đều `True`. Mã đang dùng: FOLLOWER `mask=0`, INSIDER `mask=4`, VERTI AI `mask=2`, CITADEL `mask=2`.

Muốn chèn logo vào giữa mã thì đổi `error="q"` thành `error="h"`.

### Cách B: Canva / Figma
- **Canva**: **Apps** → tìm **QR Code** → dán link → kéo vào thiết kế.
- **Figma**: dùng một plugin tạo QR.

Dù dùng cách nào, **quét thử** trước khi gửi in.

---

## 9. Thông số in (poster, tờ rơi)

| Hạng mục | Khuyến nghị |
|---|---|
| Định dạng gửi nhà in | **SVG** (vector) |
| Lề trắng quanh mã | Tối thiểu 4 ô (đã có sẵn trong file) |
| Kích thước | Cạnh mã ≥ 1/10 khoảng cách quét. Đứng cách 2 m → mã ≥ 20 cm; cầm điện thoại sát → 4–5 cm là đủ |
| Tờ rơi | Cạnh mã **tối thiểu ~3 cm**, tốt nhất **4 cm** |
| Màu | **Mã đen trên nền trắng.** Không đảo màu, không tô màu theo tông poster |
| Mức sửa lỗi | Q (đang dùng), hoặc H nếu chèn logo / poster dễ lóa, nhăn |
| Ghi chú | In tên sản phẩm ngay dưới mã để khách biết mã nào của sản phẩm nào |

---

## 10. Cập nhật nội dung sau này (QR giữ nguyên)

**Cách 1 – Thay cả file:**
1. Vào thư mục sản phẩm (ví dụ `follower/`).
2. **Add file → Upload files**, kéo file HTML mới đã **đổi tên thành `index.html`** vào → **Commit changes** (ghi đè file cũ).

**Cách 2 – Sửa vài chữ:** mở `follower/index.html` → biểu tượng **bút chì** → sửa → **Commit changes**.

Sau ~1 phút trang cập nhật. Trên điện thoại có thể cần tải lại trang (kéo xuống để refresh) để xóa cache.

---

## 11. Người khác chỉnh sửa HTML (làm đẹp, sửa nội dung)

**Không ảnh hưởng gì tới mã QR.** Sửa chữ, đổi màu, thêm ảnh hay làm lại toàn bộ giao diện đều được; khách quét sẽ thấy bản mới sau khoảng 1 phút.

### 11.1. Cấp quyền sửa
Repo nằm trong tài khoản cá nhân `toancoderVN`, nên người khác chưa sửa trực tiếp được. Chọn một trong hai cách:

- **Cách 1 – Gửi file:** người sửa gửi file HTML mới cho chủ repo, chủ repo upload theo **mục 10**.
- **Cách 2 – Mời vào repo:** **Settings → Collaborators → Add people**, nhập username GitHub của người đó. Họ nhận email mời, chấp nhận xong là sửa được. Gửi kèm tài liệu này cho họ (đặc biệt mục 10, 11 và 13).

### 11.2. Quy tắc bắt buộc cho người sửa

1. **Giữ đúng tên và đúng chỗ:** bản mới phải tên là **`index.html`** và nằm đúng thư mục cũ (`follower/`, `insider/`, `vertiai/`, `citadel/`).
   - ⚠️ Lỗi hay gặp: upload file với tên khác (ví dụ `FOLLOWER_gioi_thieu_san_pham.html`) → file mới nằm riêng một chỗ, QR vẫn mở trang cũ, trông như "sửa mà không thấy đổi". Cách sửa: xóa file `follower/index.html` cũ trước (mở file → **⋯** → **Delete file** → Commit), rồi đổi tên file mới thành `follower/index.html` theo mục 5 (Cách A, bước 3–5). Trong lúc chưa đổi tên xong (khoảng 1–2 phút), link tạm thời báo lỗi 404 – làm liền tay là được.
2. **Không** đổi tên / xóa thư mục, **không** đổi tên repo, **không** chuyển repo sang Private.
3. Nếu tách CSS / ảnh ra file riêng: đặt chung trong thư mục sản phẩm và dùng **đường dẫn tương đối** (`./style.css`, `./images/a.jpg`), **không** dùng `/style.css`.
4. Nén ảnh xuống vài trăm KB (khách mở bằng 4G).
5. **Giữ font Be Vietnam Pro + Lora** (đã nhúng sẵn). Không đổi sang font không đủ dấu tiếng Việt (ví dụ Caladea từng làm mất dấu ở tiêu đề). Mở thử trên điện thoại, kiểm tra các chữ như "ầ, ổ, ệ, ữ, ợ" hiển thị đúng.

### 11.3. Sau mỗi lần sửa
- Đợi ~1 phút, mở link trên điện thoại để kiểm tra (kéo xuống để tải lại nếu vẫn thấy bản cũ).
- **Lỡ sửa hỏng:** QR vẫn chạy nhưng khách sẽ thấy trang lỗi. GitHub lưu **mọi phiên bản cũ**: mở file → **History** → chọn phiên bản tốt → mở file ở phiên bản đó (nút **⋯ → View file**) → **Raw** → lưu về máy → upload lại đè lên `index.html` theo mục 10.

---

## 12. Thêm sản phẩm mới

1. Upload file HTML → đổi tên thành `<ten-moi>/index.html` (mục 5).
2. Kiểm tra link `https://toancodervn.github.io/trienlambk/<ten-moi>/`.
3. Tạo QR mới (mục 8), đưa ảnh vào thư mục `qr/`, cập nhật bảng ở mục 0.

---

## 13. Những điều KHÔNG được làm sau khi đã in QR

- ❌ Đổi tên tài khoản `toancoderVN`
- ❌ Đổi tên repo `trienlambk`
- ❌ Đổi tên / xóa thư mục `follower`, `insider`, `vertiai`, `citadel`, hoặc file `index.html` bên trong
- ❌ Chuyển repo sang **Private**
- ❌ Tắt GitHub Pages
- ❌ Xóa repo

> 💡 Nếu sau này gắn tên miền riêng (custom domain) cho tài khoản, GitHub tự chuyển hướng link `github.io` cũ sang tên miền mới, nên QR đã in vẫn dùng được.

---

## 14. Checklist trước khi gửi in (poster, tờ rơi)

- [ ] Cả 4 link mở được trên điện thoại
- [ ] Đã quét cả 4 mã bằng **2–3 điện thoại khác nhau** (cả iPhone và Android)
- [ ] Đã quét bằng **4G**, không phải wifi
- [ ] Mỗi mã dẫn **đúng sản phẩm** in bên cạnh trên poster
- [ ] File gửi nhà in là **SVG**, mã đen trên nền trắng, có lề trắng
- [ ] Tờ rơi: cạnh mã **≥ 3 cm** (tốt nhất 4 cm), có **tên sản phẩm** ngay dưới mỗi mã
- [ ] Đã quét thử **bản in mẫu** trước khi in số lượng lớn

---

*Tham khảo giới hạn GitHub Pages: https://docs.github.com/pages/getting-started-with-github-pages/github-pages-limits*
