- Khởi tạo cặp khóa SSH bảo mật phục vụ mục đích xác thực kết nối từ xa.
- Cấu hình liên kết an toàn giữa repository cục bộ với máy chủ GitHub.
- Đẩy (push) mã nguồn và lịch sử commit thành công lên GitHub bằng giao thức SSH.

Để tạo cặp khóa SSH bằng thuật toán Ed25519, em đã sử dụng lệnh sau trong terminal:
```bash
ssh-keygen -t ed25519 -C "daotrongtri21092006@gmail.com"
```
Quá trình tạo khóa thành công, sinh ra 2 tệp:
- Khóa bí mật (Private key): `~/.ssh/id_ed25519` (Giữ bí mật, không chia sẻ)
- Khóa công khai (Public key): `~/.ssh/id_ed25519.pub`

Sau đó, em đã copy nội dung của file public key và thêm vào mục **SSH and GPG keys** trong phần Settings của tài khoản GitHub.
Để kiểm tra kết nối SSH tới GitHub, em sử dụng lệnh:
```bash
ssh -T git@github.com
```

## 3. Liên kết remote repository và đẩy dự án lên GitHub
Sau khi xác thực SSH thành công, em tiến hành tạo một repository mới và cấu hình liên kết remote:

```bash
# Khởi tạo git trong thư mục dự án
git init

# Thêm tất cả các thay đổi
git add .

# Thực hiện commit đầu tiên
git commit -m "up"

# Tạo repository trên GitHub thông qua GitHub CLI và tự động thêm remote origin
gh repo create ChongChi-hub/IT209_Session_04_Bai_03 --public --source=. --remote=origin

# Đẩy dự án lên GitHub thông qua giao thức SSH
git push -u origin main
```

Để kiểm tra cấu hình remote URL đã đúng chuẩn SSH chưa, em dùng lệnh:
```bash
git remote -v
```
Kết quả mong đợi trả về dạng:
```
origin  git@github.com:ChongChi-hub/IT209_Session_04_Bai_03.git (fetch)
origin  git@github.com:ChongChi-hub/IT209_Session_04_Bai_03.git (push)
```

## 4. Đường dẫn URL kho lưu trữ GitHub
- **HTTPS URL:** [https://github.com/ChongChi-hub/IT209_Session_04_Bai_03](https://github.com/ChongChi-hub/IT209_Session_04_Bai_03)
- **SSH URL:** `git@github.com:ChongChi-hub/IT209_Session_04_Bai_03.git`
