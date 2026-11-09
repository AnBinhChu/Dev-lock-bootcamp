How Blockchain Works

- Student: Chu An Bình
- GitHub: https://github.com/AnBinhChu
- Submitted: 22/10/2026
- Commit: https://github.com/AnBinhChu/Dev-lock-bootcamp

## 1. Summary
1. Consensus & Byzantine (Cơ chế đồng thuận)
2. PoW - PoS - Finality
3. Trilemma - Layer 1/2
4. Account - UTXO
5. Mô hình triển khai
6. Bài toán cấp bằng

## 2. Topic notes
1. Consensus & Byzantine (Cơ chế đồng thuận)
- Là cơ chế để các node thống nhất một trạng thái chung, kể cả khi có node lỗi hoặc gian lận - nối lại bài toán Byzantine
- Mạng lưới chỉ an toàn khi số lượng node lỗi không được lớn hơn ⅓ lần tổng số node
- Là cơ chế giúp cho mạng lưới cùng đi đến 1 kết quả.
2. PoW - PoS - Finality
- Proof of Work: 
 + Cơ chế: Cạnh tranh bằng năng lượng tính toán.   
 + Quy trình: Thử nonce -> Băm block -> So target -> Thử lại.Miner tìm nonce sao cho giá trị hash < target.   
 + Thưởng: Người tìm ra trước sẽ được thêm block và nhận thưởng. 
- Proof of Stake:
 + Cơ chế: Bảo đảm bằng tài sản ký quỹ (Validator khóa coin làm tài sản đảm bảo).
 + Quy trình:
   * Validator được chọn để đề xuất block.
   * Các validator khác tiến hành xác thực.
   * Nếu gian lận -> chịu phạt (slashing).
+ Đặc điểm: Dùng động lực kinh tế để thay thế cho cuộc đua tiêu thụ điện.
- So sánh PoW và PoS:
| Tiêu chí | Proof of Work (PoW) | Proof of Stake (PoS) |
| :--- | :--- | :--- |
| **Tài nguyên** | Điện & máy đào | Coin ký quỹ |
| **Người tạo block** | Miner | Validator |
| **An ninh** | Chi phí tính toán | Slashing |
| **Năng lượng** | Cao | Thấp hơn |
| **Finality** | Xác suất | Thường nhanh hơn |
3. Trilemma - Layer 1/2
- Blockchain Trilemma:Một mạng lưới Blockchain rất khó đạt cả 3 yếu tố cùng lúc.
 + Phi tập trung.
 + Bảo mật.
 + Khả năng mở rộng.
- Layer 1/2:
 + Layer 1: Đảm nhận chức năng Đồng thuận - Dữ liệu - Bảo mật.
 + Layer 2: Đảm nhận chức năng Xử lý nhanh - Gom giao dịch.
-> Ẩn dụ đường bộ:
 + Layer 1 giống như cao tốc chính.
 + Layer 2 giống như đường gom: giúp xử lý bớt lượng xe (giao dịch) rồi mới nhập kết quả về lại cao tốc chính.
4. Account - UTXO
- Account - Based: Giống số dư tài khoản ngân hàng. Trạng thái được cập nhật trực tiếp.
- UTXO: Giống các tờ tiền chưa tiêu. Giao dịch dùng đầu vào, tạo đầu ra mới.
5. Mô hình triển khai
| Tiêu chí | Public | Private | Permissioned |
| :--- | :--- | :--- | :--- |
| **Đặc điểm chung** | Mở cho mọi người | Một tổ chức kiểm soát | Liên minh cùng quản trị |
| **Quyền Đọc** | Công khai | Giới hạn | Tùy chính sách |
| **Quyền Ghi** | Không cần cấp phép | Nội bộ | Được cấp quyền |
| **Cơ chế Tin cậy** | Kinh tế mạng | Tổ chức | Nhiều bên |
6. Bài toán cấp bằng
* Đề bài: Các trường muốn cấp và thu hồi bằng trên blockchain. Nên chọn kiểu cấu trúc nào?
- Kiến trúc giải pháp:
 + Liên minh các trường hợp tác với nhau.
 + Dùng Permissioned chain (Chuỗi liên minh) để quản lý.
 + Neo Merkle root lên Public chain.
- Quản lý dữ liệu: Dữ liệu cá nhân không đưa lên chain. Public chain chỉ lưu giữ bằng chứng để bất kỳ ai cũng có thể kiểm chứng.
## 3. Work completed



## 4. Evidence
https://drive.google.com/file/d/1o0z5UnPGyJA1yyLZQMLZ-TQ3cMuKODmk/view?usp=sharing
## 5. Blockers
 

## 6. Takeaway


