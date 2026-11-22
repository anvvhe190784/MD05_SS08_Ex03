# Bài 3: Các lệnh CLI Build & Push Image lên GitHub Container Registry (GHCR)

## 1. Tạo Personal Access Token (PAT Classic)
- Vào **GitHub -> Settings -> Developer settings -> Personal access tokens -> Tokens (classic)**.
- Tạo token với quyền tối thiểu cho GHCR: `write:packages`, `read:packages`, `delete:packages` (và `repo` nếu cần liên kết repo private).

## 2. Đăng nhập GHCR qua Docker CLI (không dùng mật khẩu GitHub chính)
```bash
export CR_PAT=<YOUR_GITHUB_PAT>
echo $CR_PAT | docker login ghcr.io -u anvvhe190784 --password-stdin
```
Kết quả mong đợi: `Login Succeeded`.

## 3. Build và gắn tag chuẩn namespace GHCR (`1.0.0`)
*(Lưu ý: tên owner/image trên GHCR bắt buộc viết thường toàn bộ).*
```bash
docker build -t ghcr.io/anvvhe190784/payment-service:1.0.0 .
```

## 4. Push Image lên GHCR
```bash
docker push ghcr.io/anvvhe190784/payment-service:1.0.0
```

## 5. URL Package trên GitHub Profile
- https://github.com/anvvhe190784?tab=packages
- `ghcr.io/anvvhe190784/payment-service:1.0.0`
