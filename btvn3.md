# Phần 1: Báo cáo phân tích

Soi bằng F12, chọn khung "Nội dung bài học", xem tab Computed. (số liệu là ví dụ)

```
+-------------------------------------+
| margin: 0 (dưới: -20px)             |
|  +-------------------------------+  |
|  | border: 2px                   |  |
|  |  +-------------------------+  |  |
|  |  | padding: 20px           |  |  |
|  |  |  +-------------------+  |  |  |
|  |  |  | content 600 x 300 |  |  |  |
|  |  |  +-------------------+  |  |  |
|  |  +-------------------------+  |  |
|  +-------------------------------+  |
+-------------------------------------+
```

- content: chữ, hình bên trong
- padding: khoảng cách trong viền
- border: đường viền
- margin: khoảng cách ngoài viền, cách khung khác

**Nguyên nhân đè:**
- box-sizing là content-box nên tổng kích thước = 600 + 40 + 4 = 644px, bị tràn.
- margin-bottom âm (-20px) kéo khung dưới lên đè.

**Nếu chỉ đổi margin không xem padding:** khung vẫn to hơn dự tính nên vẫn tràn, và margin 2 khung sát nhau bị gộp (margin collapse) nên khoảng cách không như mong muốn.

# Phần 2: Thiết kế giải pháp

```css
.noi-dung-bai-hoc {
  box-sizing: border-box;
  width: 100%;
  padding: 16px;
  border: 1px solid #ccc;
  margin-bottom: 20px;
}

.danh-sach-video {
  box-sizing: border-box;
  margin-top: 0;
}
```

- border-box: width đã tính cả padding và border, hết tràn.
- margin-bottom từ -20px thành 20px: hai khung tách ra.