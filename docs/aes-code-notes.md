# Ghi chú cấu trúc code AES CBC

## 1. File `encrypt.cpp`

Vai trò chính:

- đọc plaintext từ bàn phím
- pad plaintext về bội số của 16 byte bằng zero padding
- đọc khóa từ `keyfile`
- dùng IV cố định
- gọi `KeyExpansion`
- mã hóa từng block 16 byte bằng AES-128 theo chế độ CBC
- ghi IV + ciphertext ra `message.aes` dưới dạng binary

Các hàm chính:

- `AddRoundKey`
- `SubBytes`
- `ShiftRows`
- `MixColumns`
- `Round`
- `FinalRound`
- `AESEncrypt`

## 2. File `decrypt.cpp`

Vai trò chính:

- đọc IV + ciphertext từ `message.aes` dưới dạng binary
- đọc khóa từ `keyfile`
- gọi `KeyExpansion`
- giải mã từng block 16 byte theo CBC
- loại bỏ padding và in plaintext

Các hàm chính:

- `SubRoundKey`
- `InverseMixColumns`
- `ShiftRows` theo chiều ngược
- `SubBytes` dùng inverse S-box
- `InitialRound`
- `AESDecrypt`

## 3. File `structures.h`

Vai trò chính:

- chứa S-box và inverse S-box
- chứa bảng tra cứu dùng cho MixColumns và InverseMixColumns
- chứa `rcon`
- triển khai `KeyExpansionCore`
- triển khai `KeyExpansion`

## 4. Gợi ý cải tiến cho sinh viên

- Sinh IV ngẫu nhiên thay vì cố định.
- Tách phần AES core ra `aes.h` và `aes.cpp`.
- Tách CLI ra `main.cpp`.
- Dùng PKCS#7 padding thay cho zero padding.
- Thêm test vector chuẩn AES.
