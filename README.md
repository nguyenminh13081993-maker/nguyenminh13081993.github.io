# Flappy Bird + Quiz (Mobile-first)

Bộ file đã tối ưu cho màn hình điện thoại và sẵn sàng deploy GitHub Pages hoặc nhúng iframe.

## Cấu trúc
- `index.html` — Game (canvas) + Quiz, **đã tối ưu responsive** và phát sự kiện sang `scoreboard.html` qua `BroadcastChannel`.
- `scoreboard.html` — Bảng điểm realtime (mở trên màn hình lớn). Lắng nghe điểm từ tab game.
- (Tuỳ chọn) Bạn có thể đổi tên Google Form ở biến `FORM_URL` trong `index.html` để nhận điểm.

> QR trong game dùng Google Chart API để tạo nhanh mã QR từ URL trang game.

## Deploy GitHub Pages
1. Tạo repo, đặt 2 file `index.html` và `scoreboard.html` ở thư mục gốc.
2. Push lên GitHub, bật Pages: **Settings → Pages → Deploy from branch** (branch `main`), Folder `/ (root)`.
3. Chờ Pages build xong, bạn sẽ có URL dạng `https://<user>.github.io/<repo>/`.
4. Mở `scoreboard.html` trên màn hình lớn (trình duyệt desktop), còn người chơi mở `index.html` (trên điện thoại).

## Nhúng vào website khác (iFrame)
Dán đoạn sau vào trang của bạn:
```html
<iframe src="https://<user>.github.io/<repo>/" style="width:100%;max-width:420px;border:0;aspect-ratio:420/680" loading="lazy"></iframe>
```
> `aspect-ratio` giúp giữ đúng tỷ lệ khung game; trên mobile khung sẽ co giãn theo chiều rộng.

## Tuỳ biến nhanh
- **Google Form nhận điểm:** trong `index.html`, sửa hằng `FORM_URL` với các `entry.<id>` tương ứng câu hỏi Form của bạn.
- **Bộ câu hỏi:** phần `QUESTIONS` ngay trong file, với `triggerPipe` là mốc ống sẽ hiện câu hỏi.
- **Tốc độ/độ khó:** `pipeSpeed`, `pipeGap`, `spawnEvery` trong `CONFIG`.

## Lưu ý
- Realtime scoreboard dùng `BroadcastChannel` ⇒ game và scoreboard cần mở **trên cùng thiết bị/domain** để trình duyệt cho phép truyền kênh nội bộ. Cách dùng phổ biến: mở `scoreboard.html` trên PC, mở `index.html` trên **cùng domain** bằng trình duyệt trên PC (hoặc trong cùng kiosk) — hoặc đơn giản hơn, bật **Chế độ demo** để trình chiếu.
- Trên iOS Safari cũ không có `BroadcastChannel`, khi đó scoreboard vẫn chạy nhưng sẽ không nhận điểm realtime (dùng demo).

Chúc chơi vui! 🎮
