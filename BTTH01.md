# Phân tích bố cục trang chủ tlu.edu.vn

> Nguồn: https://tlu.edu.vn/ (Trường Đại học Thủy lợi)
> Phân tích theo tư duy bố cục: chỉ dùng `div`, xác định thẻ lồng nhau, đặt tên; sau đó phân tích Flexbox, kiểu nội dung và phần tử HTML.

**Lưu ý:** phần phân tích dựa trên nội dung văn bản và hình ảnh của trang, không có mã CSS. Vì vậy phần Flexbox là suy luận từ thứ tự và loại nội dung. Các khối lặp lại trong dữ liệu (danh sách tin xuất hiện nhiều lần) là do slider nhân bản phần tử để chạy vòng lặp.

---

## Phần 1 — Sơ đồ bố cục (chỉ dùng `div`)

```
div.page
├── div.header
│   └── div.header-inner
│       ├── div.logo                      (logo trường)
│       ├── div.nav                       (menu chính)
│       │   └── div.nav-item  ×8          (Giới thiệu, Tin tức, Tuyển sinh, Đào tạo,
│       │       │                          Nghiên cứu, Hợp tác QT, Sinh viên, eTLU)
│       │       ├── div.nav-title
│       │       └── div.dropdown
│       │           └── div.dropdown-item ×n
│       └── div.tools
│           ├── div.search                (ô/nút Tìm kiếm)
│           └── div.lang-switch           (VN | EN + cờ)
│
├── div.main
│   │
│   ├── div.hero                          (banner đầu trang)
│   │   └── div.hero-track
│   │       └── div.hero-slide ×n         (ảnh banner và 2 video)
│   │
│   ├── div.section-news                  (Tin tức – Thông báo – Sự kiện)
│   │   ├── div.news-main
│   │   │   ├── div.section-head          ("Tin Tức")
│   │   │   └── div.carousel
│   │   │       ├── div.carousel-prev     (‹)
│   │   │       ├── div.carousel-track
│   │   │       │   └── div.news-card ×8
│   │   │       │       ├── div.card-thumb
│   │   │       │       ├── div.card-tag      ("Tin tức chung", "Hot")
│   │   │       │       ├── div.card-title
│   │   │       │       ├── div.card-excerpt
│   │   │       │       └── div.card-date
│   │   │       └── div.carousel-next     (›)
│   │   └── div.news-side
│   │       ├── div.notice-box            (Thông Báo)
│   │       │   ├── div.section-head
│   │       │   └── div.notice-item ×6
│   │       │       ├── div.notice-title
│   │       │       └── div.notice-date
│   │       └── div.event-box             (Sự Kiện)
│   │           ├── div.section-head
│   │           └── div.event-item ×n
│   │               ├── div.event-thumb
│   │               ├── div.event-date    ("19 Tháng 11")
│   │               └── div.event-title
│   │
│   ├── div.section-stats                 (Những Con Số Ấn Tượng)
│   │   ├── div.section-head
│   │   ├── div.stats-list
│   │   │   └── div.stat-item ×5
│   │   │       ├── div.stat-number
│   │   │       └── div.stat-label
│   │   └── div.stats-photo
│   │
│   ├── div.section-topics                (lưới 4 chuyên mục)
│   │   ├── div.topic-card  (Tuyển Sinh)
│   │   │   ├── div.topic-thumb
│   │   │   ├── div.topic-title
│   │   │   ├── div.topic-desc
│   │   │   ├── div.topic-links           (Đại học / Thạc sĩ / Tiến sĩ)
│   │   │   └── div.topic-cta             ("Đăng ký ngay")
│   │   ├── div.topic-card  (Đào Tạo)     ┐
│   │   ├── div.topic-card  (Sinh Viên)   ├ mỗi thẻ: div.topic-head +
│   │   └── div.topic-card  (Cựu SV)      ┘ div.topic-thumb + div.topic-title + div.topic-excerpt
│   │
│   ├── div.section-units                 (Các đơn vị đào tạo, KHCN)
│   │   ├── div.section-head
│   │   └── div.units-body
│   │       ├── div.units-list
│   │       │   └── div.unit-item ×11     (Khoa KT&QL, Khoa CNTT, Phân hiệu…)
│   │       └── div.unit-detail
│   │           ├── div.unit-desc
│   │           └── div.unit-cta          ("Khám phá Khoa…")
│   │
│   ├── div.section-intl                  (Hợp Tác Quốc Tế)
│   │   ├── div.section-head
│   │   └── div.intl-body
│   │       ├── div.post-featured         (ảnh + tag + tiêu đề + ngày)
│   │       └── div.post-list
│   │           └── div.post-item ×6      (tag + tiêu đề + ngày)
│   │
│   ├── div.section-research              (Nghiên Cứu — cùng cấu trúc section-intl)
│   │   ├── div.section-head
│   │   └── div.research-body
│   │       ├── div.post-featured
│   │       └── div.post-list
│   │
│   ├── div.section-partners              (Mạng Lưới Đối Tác)
│   │   ├── div.section-head
│   │   ├── div.partners-intro
│   │   └── div.logo-track
│   │       └── div.logo-item ×n
│   │
│   ├── div.section-community             (Vì Cộng Đồng — carousel thẻ tin)
│   │   ├── div.section-head
│   │   └── div.carousel
│   │       └── div.news-card ×n
│   │
│   └── div.section-gallery               (Khoảnh Khắc TLU)
│       ├── div.section-head
│       └── div.gallery-grid
│           └── div.gallery-item ×13
│
└── div.footer
    ├── div.footer-top
    │   ├── div.footer-brand
    │   │   ├── div.footer-logo
    │   │   ├── div.footer-contact        (địa chỉ, email, điện thoại)
    │   │   └── div.footer-social         (Facebook, YouTube, Instagram, TikTok)
    │   ├── div.footer-col                (Giới thiệu)
    │   ├── div.footer-col                (Truy cập nhanh)
    │   ├── div.footer-col                (Theo dõi TLU)
    │   └── div.footer-map                ("Tải bản đồ tương tác")
    └── div.footer-bottom                 (© 2026 … Phát triển bởi…)
```

Có thêm `div.mobile-menu` (menu dạng accordion, nội dung trùng menu chính) chỉ hiện trên màn hình nhỏ.

---

## Phần 2 — Tư duy Flexbox cho từng thành phần

**Nguyên tắc chung:** `div.page` là cột dọc (`flex-direction: column`, `min-height: 100vh`). `div.main` có `flex: 1` để footer luôn nằm dưới đáy. Mỗi section là một khối xếp dọc, bên trong là các flex container nhỏ xếp hàng.

| Thành phần | Container flex | Căn chỉnh / chia không gian | Ý đồ thiết kế |
|---|---|---|---|
| `div.header-inner` | `display:flex; flex-direction:row` | `align-items:center; justify-content:space-between` | Logo trái, menu giữa, công cụ phải trên một hàng. |
| `div.logo` | item | `flex-shrink:0` | Logo không bị co khi menu dài. |
| `div.nav` | `display:flex; gap` | `flex:1; justify-content:center` | 8 mục menu chia đều, chiếm phần không gian còn lại. |
| `div.nav-item` | `display:flex; flex-direction:column` + `position:relative` | — | Tiêu đề trên, `div.dropdown` (absolute) xổ xuống khi hover. |
| `div.tools` | `display:flex; gap` | `align-items:center` | Ô tìm kiếm và nút ngôn ngữ nằm cùng hàng. |
| `div.hero-track` | `display:flex` (hàng, không wrap) | `overflow:hidden` ở cha, `flex:0 0 100%` ở mỗi slide | Mỗi slide rộng đúng 100%, trượt ngang bằng `transform`. |
| `div.news-main` + `div.news-side` | `display:flex; gap` | `align-items:flex-start`; main `flex:2`, side `flex:1` | Bố cục 2 cột: tin chính rộng, cột phụ hẹp. Mobile đổi sang `column` hoặc `wrap`. |
| `div.carousel` | `display:flex; align-items:center` | Hai nút ‹ › hai đầu, track `flex:1; overflow:hidden` | Nút giữ kích thước cố định, track chiếm phần còn lại. |
| `div.carousel-track` | `display:flex; gap` | `flex:0 0 calc(100%/n)` cho từng card | Card cùng kích thước, trượt ngang. |
| `div.news-card` | `display:flex; flex-direction:column` | Ảnh trên, nội dung dưới; `div.card-date` có `margin-top:auto` | Ngày luôn nằm đáy card dù tiêu đề dài ngắn khác nhau. |
| `div.notice-item` | `display:flex; justify-content:space-between` | `gap`; title `flex:1`, date `flex-shrink:0` | Tiêu đề bên trái co giãn, ngày bên phải cố định. |
| `div.event-item` | `display:flex; gap` | `align-items:center`; thumb `flex-shrink:0` | Ảnh nhỏ bên trái, tiêu đề bên phải; `event-date` là badge định vị tuyệt đối trên ảnh. |
| `div.stats-list` | `display:flex; flex-wrap:wrap` | `justify-content:space-around`; mỗi item `flex:1 1 160px` | 5 số liệu chia đều một hàng, tự xuống dòng khi hẹp. |
| `div.stat-item` | `display:flex; flex-direction:column; align-items:center` | — | Số lớn trên, nhãn nhỏ dưới, căn giữa. |
| `div.section-topics` | `display:flex; flex-wrap:wrap; gap` | Mỗi card `flex:1 1 calc(25% - gap)` (hoặc Grid) | 4 chuyên mục cùng kích thước, tự rớt hàng theo màn hình. |
| `div.topic-card` (Tuyển sinh) | `display:flex; flex-direction:column` | `justify-content:space-between` | Nút "Đăng ký ngay" luôn dính đáy card. |
| `div.units-body` | `display:flex; gap` | `align-items:stretch`; list `flex:0 0 30%`, detail `flex:1` | Kiểu tab dọc: danh sách khoa bên trái cố định, nội dung chi tiết bên phải. |
| `div.units-list` | `display:flex; flex-direction:column` | `gap` | 11 đơn vị xếp dọc như menu. |
| `div.intl-body`, `div.research-body` | `display:flex; gap` | `post-featured` `flex:1.2`, `post-list` `flex:1` | Bài nổi bật to bên trái, danh sách bài bên phải. |
| `div.post-list` | `display:flex; flex-direction:column` | `gap`, các item `flex:1` | Các dòng bài đều nhau theo chiều cao khối. |
| `div.logo-track` | `display:flex; gap` | `align-items:center`; chạy ngang kiểu marquee | Logo xếp hàng ngang, cuộn vô hạn. |
| `div.gallery-grid` | `display:flex; flex-wrap:wrap; gap` | `flex:1 1 25%` (hoặc Grid/masonry) | Ảnh xếp lưới tự xuống dòng. |
| `div.footer-top` | `display:flex; flex-wrap:wrap; gap` | `justify-content:space-between`; brand `flex:2`, mỗi col `flex:1` | Thương hiệu rộng hơn, 3 cột liên kết đều nhau; mobile xuống 1 cột. |
| `div.footer-social` | `display:flex; gap` | — | Biểu tượng mạng xã hội xếp hàng. |
| `div.footer-bottom` | `display:flex; justify-content:center` (hoặc `space-between`) | — | Dòng bản quyền. |

**Các kỹ thuật Flexbox lặp lại:**

- **Hàng–cột lồng nhau:** `row` ở cấp section, `column` ở cấp card.
- **Phần tử co giãn và cố định:** `flex:1` cho phần co giãn, `flex-shrink:0` cho logo, nút, ngày, ảnh nhỏ.
- **Đẩy phần tử xuống đáy:** `margin-top:auto` hoặc `justify-content:space-between` cho ngày đăng và nút CTA.
- **Responsive:** `flex-wrap:wrap` cùng `flex-basis`, hoặc đổi `flex-direction` bằng media query.

---

## Phần 3 — Kiểu nội dung và phần tử HTML

| Thành phần | Kiểu nội dung | Phần tử HTML đề xuất |
|---|---|---|
| `div.header` | Vùng đầu trang | `<header>` bao ngoài |
| `div.logo` | Ảnh liên kết về trang chủ | `<a href="/">` chứa `<img alt="Trường Đại học Thủy lợi">` |
| `div.nav` | Điều hướng, danh sách phân cấp | `<nav>` > `<ul>` > `<li>` > `<a>` (+ `<ul>` con cho dropdown) |
| `div.search` | Tương tác nhập liệu | `<form>` > `<input type="search">` + `<button>` |
| `div.lang-switch` | Nút chọn ngôn ngữ kèm cờ | `<button>` hoặc `<a>` + `<img>` (cờ) |
| `div.hero-slide` | Hình ảnh/video quảng bá | `<img>` hoặc `<video controls muted autoplay>` / `<source>` |
| `div.section-head` | Tiêu đề khối, có liên kết | `<h2>` chứa `<a>` |
| `div.carousel-prev/next` | Điều khiển | `<button aria-label="Trước/Sau">` |
| `div.news-card` | Thẻ bài viết | `<article>` |
| ↳ `card-thumb` | Ảnh minh họa | `<img>` trong `<a>` (hoặc `<figure>`) |
| ↳ `card-tag` | Nhãn phân loại | `<span>` |
| ↳ `card-title` | Tiêu đề bài | `<h3>` > `<a>` |
| ↳ `card-excerpt` | Đoạn trích | `<p>` |
| ↳ `card-date` | Ngày đăng | `<time datetime="2026-11-25">` |
| `div.notice-box` | Danh sách thông báo | `<section>` > `<ul>` > `<li>` > `<a>` + `<time>` |
| `div.event-item` | Sự kiện có ngày | `<article>` + `<img>` + `<time>` + `<h3><a>` |
| `div.section-stats` | Số liệu thống kê | `<section>`, mỗi mục là `<div>` hoặc `<dl>` với `<dt>` nhãn, `<dd>` số |
| ↳ `stat-number` | Số lớn (có thể chạy counter bằng JS) | `<strong>` hoặc `<span>` |
| ↳ `stats-photo` | Ảnh chân dung | `<figure>` > `<img>` + `<figcaption>` |
| `div.topic-card` | Thẻ chuyên mục | `<article>` hoặc `<section>` |
| ↳ `topic-links` | Danh sách liên kết con | `<ul>` > `<li>` > `<a>` |
| ↳ `topic-cta` | Nút kêu gọi hành động | `<a class="btn">` (là liên kết, không phải `<button>`) |
| `div.units-list` | Danh sách khoa/đơn vị | `<ul>` > `<li>` > `<a>` |
| `div.unit-detail` | Mô tả + nút khám phá | `<p>` + `<a class="btn">` |
| `div.post-featured` | Bài nổi bật | `<article>` + `<img>` + `<h3>` + `<time>` |
| `div.post-list` | Danh sách bài | `<ul>` > `<li>` > `<a>` + `<time>` |
| `div.section-partners` | Giới thiệu và logo đối tác | `<section>`, `<p>`, `<ul>` > `<li>` > `<img>` |
| `div.gallery-grid` | Bộ ảnh | `<ul>` > `<li>` > `<figure>` > `<img>` (hoặc `<img>` trực tiếp) |
| `div.footer` | Chân trang | `<footer>` |
| ↳ `footer-contact` | Địa chỉ, email, điện thoại | `<address>` với `<a href="mailto:">`, `<a href="tel:">` |
| ↳ `footer-col` | Cột liên kết có tiêu đề | `<h3>` + `<ul>` > `<li>` > `<a>` |
| ↳ `footer-social` | Liên kết mạng xã hội | `<ul>` > `<li>` > `<a>` + icon (`<svg>`/`<img>`) |
| ↳ `footer-map` | Bản đồ tương tác tải theo yêu cầu | `<button>` + `<iframe>` (Google Maps) |
| `div.footer-bottom` | Bản quyền | `<p>` (có thể kèm `<small>`) |
