How Blockchain Works

- Student: Chu An Bình
- GitHub: https://github.com/AnBinhChu
- Submitted: 22/10/2026
- Commit: https://github.com/AnBinhChu/Dev-lock-bootcamp

## 1. Summary
1. Giải thích một smart contract bằng  ví dụ vé sự kiện.
2.  Phân biệt coin, token, stablecoin và NFT.
3. Đọc được phép tính phí giao dịch đơn giản.
4. Nhận ra EVM, SVM và WASM ở đúng vai trò.
## 2. Topic notes
1. Giải thích một smart contract bằng  ví dụ vé sự kiện.
- Smart contract là một chương trình.
 + Smart contract: Mã lệnh và dữ liệu nằm trên blockchain, thực thi theo quy tắc khi có lời gọi hợp lệ.( hợp đồng thông minh)
- Smart contract có giới hạn:

| Chương trình làm được | Ứng dụng vẫn cần |
| :--- | :--- |
| Kiểm tra dữ liệu và quyền gọi hàm. | Dữ liệu bên ngoài qua oracle hoặc bên cung cấp. |
| Cập nhật trạng thái theo mã lệnh. | Người vận hành, giao diện và quy tắc xử lý sự cố. |

 + Một số hệ thống có quyền quản trị hoặc cơ chế nâng cấp.
2.  Phân biệt coin, token, stablecoin và NFT.
- Native coin và token:

| Tiêu chí | Native coin | Token |
| :--- | :--- | :--- |
| **Thuộc về** | Tài sản gốc của mạng | Tài sản do chương trình quản lý |
| **Ví dụ** | ETH trên Ethereum<br>SOL trên Solana | USDC, token thành viên, NFT |
| **Trả phí mạng** | Thường dùng coin gốc | Thường cần coin gốc của mạng |
 + Ví dụ trên Ethereum: ETH là coin, USDC là token.
- Token giống như một sổ số dư.
 Ví dụ bảng số dư điểm CLB:
 *Lan: 70
 *Minh: 30
 *Tổng cung: 100 điểm đang tồn tại
  ->Ví dụ giao dịch: Khi gửi 10 điểm, Lan còn 60, Minh có 40, và tổng cung vẫn là 100.(Tổng cung được giữ nguyên)
- Mint, transfer và burn

| Thao tác | Điều thay đổi | Tổng cung ví dụ |
| :--- | :--- | :--- |
| Mint 20 | Tạo thêm 20 token | 100 thành 120 |
| Transfer 10 | Chuyển 10 token giữa hai ví | Giữ ở 120 |
| Burn 5 | Hủy 5 token đang tồn tại | 120 còn 115 |

 + Quyền mint và burn phụ thuộc thiết kế của token.
- Giá không phụ thuộc vào tổng cung mà phụ thuộc vào nhu cầu của thị trường.
- Stablecoin hướng tới một mức giá tham chiếu:
 + Stablecoin: Token được thiết kế để báo theo giá trị tham chiếu, thường là một đơn vị tiền tệ.(VD: Mục tiêu 1 token xấp xỉ 1 USD)
 + Stablecoin là một dạng tiền thực tế trên mạng lưới của blockchain.
- Điều giữ stablecoin gần mức neo:

| Thiết kế | Cơ chế chính | Điểm cần xem |
| :--- | :--- | :--- |
| Dự trữ tiền và tài sản | Phát hành, quy đổi theo điều kiện | Dự trữ và bên phát hành |
| Thế chấp bằng crypto | Khóa tài sản, quản lý mức thế chấp | Biến động và thanh lý |
| Điều tiết bằng thuật toán | Điều chỉnh động lực cung cầu | Khả năng giữ neo khi bị bán mạnh |
 + USDC là một ví dụ thuộc nhóm có dự trữ bằng tiền và tài sản thanh khoản.
- NFT là token có định danh riêng.
 + NFT: Mỗi token có định danh để phân biệt với token khác trong cùng bộ sưu tập hoặc contract.(VD: vé 042 và vé 043 là hai token khác nhau)
- Sở hữu NFT bao gồm:

| Bản ghi trên blockchain | Quyền và nội dung đi kèm |
| :--- | :--- |
| Địa chỉ đang giữ token. | Phụ thuộc điều khoản của bên phát hành. |
| Lịch sử chuyển token. | Ảnh hoặc metadata có thể nằm ngoài blockchain. |
 + NFT không tự trao bản quyền tác phẩm hay bảo đảm sự kiện diễn ra.
 3. Đọc được phép tính phí giao dịch đơn giản.
 - Gas và phí giao dịch:
  + Gas đo công việc chưa thực thi: Phí giao dịch phụ thuộc lượng gas đã dùng và đơn giá gas thực trả.(Trên Ethereum, phí thực thi được thanh toán bằng ETH)
- Một phép tính phí:
- Ví dụ minh họa trên Ethereum L1
 21.000 × 20 gwei = 0,00042 ETH
 + Gas đã dùng × đơn giá thực trả
 + 1 gwei = 0,000000001 ETH
- Giao dịch thất bài có mất phí?

| Chưa gửi lên mạng | Đã vào block, thực thi lỗi |
| :--- | :--- |
| Người dùng bấm từ chối trong ví. | Thay đổi trạng thái của thao tác bị hoàn tác. |
| Không có giao dịch on-chain từ thao tác đó. | Gas đã tiêu thụ vẫn có thể bị tính phí. |
+ “Ví báo lỗi” chưa đủ để biết đã tốn phí hay chưa.
- Ví có token nhưng chưa gửi được
 + Lan có 100 USDC trên Ethereum, nhưng không có ETH. Điều gì có thể cản việc chuyển?**
 *Giả sử ví thông thường và không có bên tài trợ phí.*
> Không thể chuyển vì thiếu phí gas là ETH.
4. Nhận ra EVM, SVM và WASM ở đúng vai trò.
- EVM, SVM và WASM

| Tên | Cách hiểu nhập môn | Ví dụ |
| :--- | :--- | :--- |
| EVM | Ethereum Virtual Machine<br>Thực thi mã EVM | Ethereum và các mạng tương thích |
| SVM | Solana Virtual Machine<br>Thực thi chương trình Solana | Solana, chương trình biên dịch sBPF |
| WASM | Định dạng mã WebAssembly và mô hình thực thi | Một số nền tảng như CosmWasm |

 + WASM là công nghệ chung. Mỗi blockchain bổ sung quy tắc riêng.
- Cùng gọi là token, cách triển khai có thể khác

| Trong hệ EVM | Trên Solana |
| :--- | :--- |
| ERC-20 là chuẩn giao diện cho token thay thế được. | Token Program quản lý nhiều loại token. |
| Mỗi tài sản thường có địa chỉ contract riêng. | Mint account xác định một loại token. |

 + Địa chỉ, công cụ và cách tính phí cần khớp với mạng sử dụng.
- Bài tập ghép đúng khái niệm:
 + ETH trên Ethereum: coin
 + Vé 042 có thể chuyển nhượng: NFT
 + Tạo thêm 100 điểm thành viên: mint
 + USDC bám theo USD: stablecoin
 + Chuyển vé từ Lan sang Minh: transfer
* Ba câu kiểm tra cuối buổi:
- Burn có bảo đảm giá tăng không? Vì sao? Không, vì giá phụ thuộc vào cả lực cầu (demand); nếu cầu giảm hoặc burn token chưa lưu thông thì giá vẫn không tăng.
- Mua NFT của một ảnh có tự có bản quyền ảnh không? Không, mua NFT chỉ xác nhận quyền sở hữu token trên blockchain chứ không tự động đi kèm bản quyền tác giả (copyright) trừ khi có thỏa thuận riêng.
- Giao dịch revert sau khi vào block có thể mất phí không? Có, giao dịch bị revert vẫn tiêu tốn tài nguyên tính toán của thợ đào/validator nên bạn vẫn phải trả phí gas.

## 3. Work completed



## 4. Evidence
https://drive.google.com/file/d/1UgwORVGTvGTB2r56y6ton571reSYXFzW/view?usp=sharing
## 5. Blockers
 

## 6. Takeaway


