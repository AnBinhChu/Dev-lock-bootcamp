How Blockchain Works

- Student: Chu An Bình
- GitHub: https://github.com/AnBinhChu
- Submitted: 22/10/2026
- Commit: https://github.com/AnBinhChu/Dev-lock-bootcamp

## 1. Summary
1. Một dApp hoạt động như thế nào
2. Hiểu yêu cầu xuất hiện trong ví
3. Những ứng dụng thường gặp
4. Thực hành tạo danh sách đăng ký
5. Gọi hàm và đối chiếu kết quả
6. Thử trên Sepolia và đọc giao dịch
## 2. Topic notes
1. Một dApp hoạt động như thế nào

* **Khái niệm:** dApp là ứng dụng có phần chức năng được thực hiện bằng chương trình trên blockchain (smart contract). Giao diện vẫn là website quen thuộc, kết hợp với máy chủ, cơ sở dữ liệu và dịch vụ bên thứ ba; mức độ phi tập trung cần xét từng thành phần.
* **Luồng xử lý:** `Giao diện → Ví ký → RPC gửi → Hợp đồng thực thi → Blockchain ghi kết quả`
* **Cơ chế đọc/ghi:** Chỉ xem dữ liệu (ví dụ tổng số đăng ký) có thể đọc qua RPC mà không cần kết nối ví. Hệ thống lớn dùng **indexer** để tổng hợp dữ liệu và sự kiện nhanh hơn (dữ liệu giao diện có thể chậm hơn trạng thái trên chuỗi).

| Thành phần | Vai trò trong ví dụ |
| :--- | :--- |
| **Frontend** | Hiển thị nút và tạo yêu cầu gọi đúng hàm. |
| **Wallet** | Giúp người dùng kiểm tra và ký yêu cầu. |
| **Smart contract** | Kiểm tra điều kiện rồi cập nhật trạng thái. |
| **Blockchain và nút mạng** | Xử lý giao dịch, duy trì trạng thái và lịch sử theo quy tắc mạng. |
| **Dịch vụ phụ trợ** | Cung cấp dữ liệu, tìm kiếm hoặc lưu phần nội dung ngoài chuỗi. |

* **Lưu ý độc lập:** Website gặp lỗi không nhất thiết làm hợp đồng ngừng hoạt động; ngược lại, website chạy tốt không bảo đảm hợp đồng của nó an toàn.

---

2. Hiểu yêu cầu xuất hiện trong ví

* **Connect:** Cho website biết địa chỉ được chọn và mạng đang dùng. Chưa tự chuyển tài sản nhưng địa chỉ có thể liên kết với lịch sử giao dịch công khai.
* **Sign message:** Ký thông điệp (ví dụ chứng minh quyền kiểm soát địa chỉ khi đăng nhập). Không thấy phí mạng không có nghĩa yêu cầu ký luôn vô hại vì chữ ký có thể dùng để cấp quyền chi tiêu hoặc hoàn tất lệnh sau đó.
* **Send transaction:** Ký yêu cầu thực hiện hành động làm thay đổi trạng thái trên mạng (ví dụ `register()`), khác với hàm chỉ đọc dữ liệu (`totalRegistered`).
* **Approve:** Cấp quyền cho địa chỉ hoặc hợp đồng khác sử dụng token trong giới hạn nhất định (*allowance*). **Ngắt kết nối website không tự thu hồi quyền đã cấp trên chuỗi.**

| Trạng thái | Có thể hiểu như thế nào |
| :--- | :--- |
| **Chưa ký hoặc đã từ chối** | Yêu cầu chưa được bạn chấp thuận; kiểm tra xem có transaction hash hay chưa. |
| **Pending** | Giao dịch đã được gửi nhưng chưa được ghi nhận vào khối theo thông tin đang xem. |
| **Success** | Giao dịch thực thi thành công. Đọc lại trạng thái hoặc sự kiện để đối chiếu đúng kết quả mong muốn. |
| **Failed** | Giao dịch đã thất bại. Nếu được đưa vào khối, vẫn có thể tốn phí xử lý. |

* **Kiểm tra giao dịch:** Dùng **transaction hash** tra cứu trên trình khám phá mạng (tránh nhầm địa chỉ hợp đồng với mã giao dịch).

---

3. Những ứng dụng thường gặp

* **DeFi và thanh toán:** Dùng hợp đồng để trao đổi tài sản, cho vay hoặc chuyển stablecoin. Cần thống nhất đúng mạng, đúng token, đúng địa chỉ nhận; dữ liệu trên chuỗi chỉ ghi nhận việc chuyển token, còn giao hàng và hoàn tiền vẫn phụ thuộc quy trình bên bán; không qua ngân hàng không có nghĩa là không có rủi ro.
* **NFT và trò chơi:** Vé NFT hoặc vật phẩm game dưới dạng token giúp kiểm tra địa chỉ đang giữ, nhưng việc chấp nhận vé, cách hiển thị, chỉ số, luật sử dụng hay sự tồn tại của máy chủ game vẫn phụ thuộc vào đơn vị tổ chức và nhà phát triển.
* **DAO và quyền quyết định:** Quản trị qua đề xuất và biểu quyết; có DAO thực thi kết quả qua hợp đồng, có DAO chỉ bỏ phiếu để một nhóm thực hiện tiếp. Có token quản trị không mặc nhiên đồng nghĩa với quyền sở hữu cổ phần.
* **Oracle và dữ liệu ngoài chuỗi:** Oracle là cơ chế đưa dữ liệu ngoài chuỗi (tình trạng chuyến bay, giá cả...) vào hợp đồng, không phải bảo đảm tuyệt đối dữ liệu luôn đúng. Hợp đồng có thể chạy đúng mã nhưng cho kết quả sai nếu đầu vào không phản ánh thực tế.

---

4. Thực hành tạo danh sách đăng ký (`ClassroomSeat.sol`)

* **Môi trường:** Sử dụng **Remix VM** trên Remix IDE (môi trường mô phỏng trong trình duyệt có tài khoản và ETH thử sẵn, không cần cài ví hoặc nạp tiền).
* **Cấu trúc hợp đồng `ClassroomSeat`:**
  * `registered`: Lưu trạng thái (`true`/`false`) của từng địa chỉ.
  * `totalRegistered`: Đếm tổng số địa chỉ đã đăng ký.
  * Hàm `register()`: Kiểm tra điều kiện chưa đăng ký (`require(!registered[msg.sender])`), cập nhật trạng thái thành `true`, tăng tổng đếm lên 1 và phát sự kiện `Registered`.
* **Cấu hình biên dịch & triển khai:**
  * Compiler: `0.8.24`, EVM version: `shanghai`, tắt Optimization.
  * Deploy: Environment `Remix VM` (chọn `Osaka`), `Value = 0`.

---

5. Gọi hàm và đối chiếu kết quả trên Remix VM

* **Phân biệt thao tác:** Nút **Transact** bên cạnh `register` gửi giao dịch ghi; nút **Call** bên cạnh `registered` và `totalRegistered` đọc dữ liệu (giữ `Value = 0`).
* **Kiểm chứng quy tắc (mỗi địa chỉ đăng ký một lượt, chưa phải một lượt cho mỗi người):**
  * **Bước 1 (Trước khi đăng ký):** Gọi `totalRegistered` trả về `0`; gọi `registered` với địa chỉ Account 1 trả về `false`.
  * **Bước 2 (Đăng ký lần đầu với Account 1):** Bấm `Transact` ở `register` thành công; đọc lại `registered` thành `true` và `totalRegistered` thành `1`.
  * **Bước 3 (Đăng ký trùng với Account 1):** Bấm `register` lần nữa bị từ chối với lỗi `"Already registered"` (tăng gas không giải quyết được vì đây là quy tắc của hợp đồng).
  * **Bước 4 (Đăng ký với Account 2):** Đổi sang Account 2 và gọi `register` thành công; `totalRegistered` tăng lên `2`.

---

6. Thử trên Sepolia và đọc giao dịch

* **Chuẩn bị:** Dùng ví học tập chính thức, bật hiển thị mạng thử nghiệm và chọn **Ethereum Sepolia** (Chain ID `11155111`), xin Sepolia ETH từ faucet. Tuyệt đối không dùng tiền thật, không đưa khóa riêng hay cụm từ khôi phục cho faucet, website hoặc người hỗ trợ.
* **Kết nối và gửi giao dịch:**
  * Đổi Environment trên Remix sang **Browser Extension** (hoặc *Injected Provider*) và kết nối ví mạng Sepolia.
  * Giữ nguyên cấu hình biên dịch, chọn `ClassroomSeat`, `Value = 0` rồi bấm Deploy; lưu địa chỉ hợp đồng và **transaction hash**.
  * Gọi `register`, xác nhận trên ví và đọc lại `registered`, `totalRegistered` sau khi thành công.
* **Kiểm tra trên trình khám phá mạng:** Dán **transaction hash** vào **Sepolia Etherscan** (`sepolia.etherscan.io`) để đối chiếu **Status** (`Success`), **From**, **To** (hoặc địa chỉ hợp đồng), **Value** (`0`) và **Transaction Fee** (vẫn phát sinh lớn hơn `0` khi gọi `register`).
## 3. Work completed



## 4. Evidence
https://drive.google.com/file/d/1ndBYOC_zfDA3hXtOmIT70uNsAcP9NBBl/view?usp=sharing
## 5. Blockers
 

## 6. Takeaway


