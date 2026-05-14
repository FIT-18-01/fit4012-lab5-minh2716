# Report 1 page - Lab 5 AES-128 CBC

## Mục tiêu

Bài thực hành giúp sinh viên hiểu quy trình mã hóa và giải mã AES-128 ở chế độ CBC, bao gồm xử lý block 128-bit, mở rộng khóa, các phép biến đổi theo vòng, cơ chế padding đơn giản và vai trò của IV trong CBC.

## Cách làm / Method

Repo sử dụng 3 file mã nguồn chính: `encrypt.cpp`, `decrypt.cpp`, `structures.h`. File `encrypt.cpp` thực hiện mã hóa plaintext theo chế độ CBC với IV cố định và ghi IV + ciphertext ra `message.aes`. File `decrypt.cpp` đọc `message.aes` để lấy IV và ciphertext, giải mã theo CBC. File `structures.h` chứa S-box, inverse S-box, các bảng tra cứu nhân trong GF(2^8), RCon và hàm KeyExpansion.

Repo được cấu trúc theo mẫu starter repo của FIT4012 Lab 5: có `Makefile`, `CMakeLists.txt`, thư mục `tests/`, `logs/`, `scripts/` và GitHub Actions CI.

## Kết quả / Result

Chương trình có thể biên dịch bằng Makefile hoặc CMake. Khi chạy mẫu với plaintext `hello FIT4012 AES`, chương trình tạo file `message.aes` chứa IV và ciphertext, sau đó chương trình giải mã đọc file này và khôi phục lại plaintext ban đầu kèm các byte padding `0x00` ở cuối block.

Các test cơ bản gồm: biên dịch, round-trip encrypt/decrypt, plaintext nhiều block, sai khóa và ciphertext bị sửa đổi.

## Kết luận / Conclusion

Bài lab minh họa luồng xử lý AES-128 CBC và giúp sinh viên hiểu mối quan hệ giữa mã hóa, giải mã, key expansion, padding và IV. Hạn chế hiện tại là dùng IV cố định thay vì ngẫu nhiên; có thể mở rộng bằng cách sinh IV ngẫu nhiên, dùng PKCS#7 padding và thêm test vector chuẩn AES.
