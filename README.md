# OpenWay – Prototype mô phỏng

Website tĩnh một file (`index.html`), không cần build. Mọi dữ liệu địa điểm và GPS đều là giả lập.

## Đưa lên GitHub
```bash
cd openway
git init && git add . && git commit -m "OpenWay prototype"
git branch -M main
git remote add origin https://github.com/<tên-bạn>/openway.git
git push -u origin main
```

## Triển khai Vercel
1. Vào vercel.com → **Add New → Project** → import repo `openway`.
2. Framework Preset: **Other**. Để trống Build Command và Output Directory.
3. Bấm **Deploy**. (Hoặc `npx vercel --prod` trong thư mục dự án.)

## Đã có (theo spec)
- Hai chế độ: Nghe chỉ dẫn / Xem tuyến đường; bản đồ SVG với nét liền / chấm / đứt + nhãn chữ.
- Tương phản: theo hệ thống, vàng/đen, trắng/đen, đen/trắng; cỡ chữ 100–200%.
- Nút ≥ 56px, nút điều hướng chính 64px; nút "Trang chủ" luôn hiển thị.
- Giọng nói (Web Speech 0.75–1.5×), tín hiệu âm ngắn, rung theo mã ON/OFF trong spec.
- GPS sai số > 10 m (mô phỏng) → dừng lệnh rẽ; dữ liệu chưa xác minh → cảnh báo tại điểm quyết định.
- Báo cáo: lưu nháp, bước kiểm tra, nhập giọng nói, trạng thái "Chờ xác minh".
- Tạm dừng / kết thúc (có xác nhận); chỉ dẫn mới không cướp focus.

## Giai đoạn sau (cần dữ liệu và kiểm thử thực tế)
GPS thật (`navigator.geolocation`, kiểm tra `coords.accuracy`), bản đồ thật (MapLibre/OSM), định tuyến tiếp cận, backend lưu báo cáo (Supabase/Firebase), âm thanh không gian, kiểm thử VoiceOver/TalkBack với người dùng thật.

Lưu ý: Vibration API không hoạt động trên iOS Safari; đây là lý do rung luôn đi kèm lời nói.
