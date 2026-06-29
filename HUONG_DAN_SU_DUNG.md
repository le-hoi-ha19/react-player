# Hướng dẫn sử dụng Repo react-player (Forked)

Repo này đã được tùy chỉnh để bạn có thể sử dụng trực tiếp qua link GitHub thay vì phải cài đặt bản public từ `npm`.

## 1. Những thay đổi đã được thực hiện
- **Bỏ `dist/` khỏi `.gitignore`**: Thông thường, thư mục mã nguồn biên dịch `dist/` bị ẩn khỏi Git vì khi đăng lên npm họ mới pack vào. Việc bỏ ignore giúp thư mục `dist/` được lưu trên GitHub.
- **Thêm `prepare: npm run build`**: Vào `package.json`. Kể từ bây giờ, bất cứ khi nào có người chạy `yarn install` hoặc `npm install` chứa link git này, nếu trên máy họ chưa có `dist`, script này sẽ tự động chạy để tạo thư mục `dist/` nhằm tránh lỗi `Module not found`.
- **Đã build sẵn thư mục `dist/`**: Mã nguồn TypeScript đã được build thành công thành JavaScript ES Module.

## 2. Việc bạn cần làm ngay bây giờ
Bạn cần lưu lại (commit) các thay đổi này và đẩy (push) lên GitHub của bạn:

```bash
# Đảm bảo bạn đang đứng ở thư mục react-player
cd /home/hale/develop/cloud-door/react-player

# Xem trạng thái các file đã thay đổi (package.json, .gitignore, dist/...)
git status

# Thêm tất cả file thay đổi
git add .

# Commit thay đổi
git commit -m "build: fix git install build missing dist files"

# Đẩy lên nhánh master của github
git push origin master
```

## 3. Cách cập nhật lại project Cloud Door Web

Trong thư mục dự án `cloud_door_web`, file `package.json` đã được trỏ đến repo này:
```json
"react-player": "git+https://github.com/le-hoi-ha19/react-player.git"
```

Bất cứ khi nào bạn sửa code trong repo `react-player` này và push lên GitHub, để dự án `cloud_door_web` nhận code mới, bạn chỉ cần mở terminal tại `cloud_door_web` và chạy:

```bash
yarn upgrade react-player
# Hoặc
yarn install
```

Lúc này dự án chính của bạn sẽ luôn cập nhật được những thay đổi tuỳ chỉnh mới nhất từ repo này mà không bao giờ gặp lỗi `Can't resolve 'react-player'` nữa!
