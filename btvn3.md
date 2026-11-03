# Phần 1: Báo cáo phân tích

Box model của `#lesson-content` (soi bằng F12, tab Computed):

```
+-------------------------------+
| margin: -10 / 15              |
|  +-------------------------+  |
|  | border: 1               |  |
|  |  +-------------------+  |  |
|  |  | padding: 12 / 10  |  |  |
|  |  |  +-------------+  |  |  |
|  |  |  | 840 x 600   |  |  |  |
|  |  |  +-------------+  |  |  |
|  |  +-------------------+  |  |
|  +-------------------------+  |
+-------------------------------+
```

**Nguyên nhân đè:**
- Hai khung đều width 65%, cộng lại 130% nên không đủ chỗ.
- margin-right -20px kéo khung kia vào đè lên.
- content-box nên padding và border cộng thêm vào chiều rộng.

**Nếu chỉ đổi margin mà không xem padding:** khung vẫn to hơn dự tính nên vẫn tràn.

# Phần 2: Thiết kế giải pháp

```css
div#lesson-content { box-sizing: border-box; width: 65%; margin-right: 20px; }
div#video-list { box-sizing: border-box; width: 30%; }
```

- 65% + 30% + margin 20px nhỏ hơn 100% nên hai khung nằm cạnh nhau.
- margin đổi từ -20px thành 20px để tách hai khung.
- border-box để padding và border không làm tràn.