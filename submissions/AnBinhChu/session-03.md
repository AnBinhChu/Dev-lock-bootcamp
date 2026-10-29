How Blockchain Works

- Student: Chu An Bình
- GitHub: https://github.com/AnBinhChu
- Submitted: 22/10/2026
- Commit: https://github.com/AnBinhChu/Dev-lock-bootcamp

## 1. Summary
1. Hashing
2. Public & Private  Key
3. Digital Signature
4. Address & Wallet
5. Seed Phrase
6. Wallet Security

## 2. Topic notes
1. Hashing - Hàm băm
Biến dữ liệu có độ dài bất kỳ thành chuỗi đầu ra có độ dài cố định.
VD: trên đầu vào chuỗi có độ dài 256 thì đầu ra cũng 256 ( độ dài chuỗi đầu vào và đầu ra bằng nhau không thay đổi)
* Có thể coi hàm băm là dấu vân tay của dữ liệu.
- Hashing được dùng ở:
 + Định danh giao dịch (tạo mã duy nhất cho mỗi transaction).
 + Liên kết block (mỗi block tham chiếu hash của block trước).
 + Merkle Tree ( tóm tắt và xác minh hàng nghìn giao dịch).
 + Proof of Work (Tìm hash thỏa điều kiện của mạng).
- 5 tính chất của một hàm băm:
 + Tính một chiều.
 + Tính xác định.
 + Tính toán nhanh.
 + Hiệu ứng tuyết lở (sự khác nhau nhỏ nhất cũng cho kết quả mã hash khác nhau).
 + Kháng xung đột (như cái vân tay rất khó để 2 đầu vào khác nhau cho ra mã hash giống nhau).
2. Public & Private  Key
- Mã hóa đối xứng:
 + Sử dụng quy tắc dịch sang phải k kí tự (0<k<=26) 
 + Nếu khóa bí mật bị lộ, dữ liệu mã hóa có thể bị giải mã bởi bất kỳ ai có khóa đó.
- Mã hóa bất đối xứng:
 + Người gửi sử dụng public key của người nhận để khóa thông tin gửi và chỉ có duy nhất private key của người nhận mới mở dược thông tin
3. Digital Signature - Chữ ký số:
- Giao dịch được gửi lên mạng lấy kết quả xác minh theo đa số.
- Public key xác minh giống Private key thì thông qua.
- Xác minh đúng người gửi và kiểm tra trên đường truyền có bị thay đổi gì không.
4. Address & Wallet
- Từ Private key đến Address:
 + Một chuỗi biến đổi một chiều tạo nên danh tính nhận tài sản.
- Wallet:
 + Hot Wallet: Kết nối internet, tiện dụng, nhanh, rủi ro tấn công cao hơn.
 + Cold Wallet: Khóa được giữ ngoại tuyến, phủ hợp lưu trữ dài hạn, an toàn hơn nếu dúng đúng.
 -> Ví không chứa Coin.






## 3. Work completed



## 4. Evidence
https://drive.google.com/file/d/19sfoq_ZGZEuGdQWaXodOpxEBDVWAO-MO/view?usp=sharing


## 5. Blockers
 

## 6. Takeaway


