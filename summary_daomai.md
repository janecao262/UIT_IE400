# TỔNG HỢP NỘI DUNG TÀI LIỆU NGHIÊN CỨU CHUYÊN ĐỀ TỐT NGHIỆP


---

## 1. "Dự báo rời bỏ khách hàng" và "Machine Learning"
*(Customer Churn Prediction using Machine Learning)*

### 1.1. Bản chất bài toán
- **Định danh thuật toán:** Đây là một bài toán **Phân loại nhị phân (Binary Classification)** trong Machine Learning.
- **Mục tiêu:** Sử dụng dữ liệu lịch sử (hành vi giao dịch, tương tác, lịch sử thanh toán) để dự báo xác suất một khách hàng dừng sử dụng sản phẩm BNPL trong tương lai gần.
- **Đầu ra nhãn:**
  - `1`: Khách hàng rời bỏ (Churn)
  - `0`: Khách hàng tiếp tục ở lại/hoạt động (Retention)

### 1.2. Giá trị nghiệp vụ (Business Value)
- **Tối ưu chi phí:** Chi phí thu hút một khách hàng mới (**CAC - Customer Acquisition Cost**) trong Fintech đắt gấp **5–7 lần** chi phí giữ chân một khách hàng hiện hữu (**CRC - Customer Retention Cost**).
- **Chủ động can thiệp:** Việc dự báo sớm giúp doanh nghiệp chuyển từ thế *bị động* sang *chủ động* (tặng voucher, hạ lãi suất phạt, gửi thông báo nhắc nhở cá nhân hóa) cho các nhóm khách hàng có nguy cơ cao trước khi họ rời đi.

### 1.3. Quy trình xử lý chuẩn trong Machine Learning
1. **Tiền xử lý & Trích xuất đặc trưng (Feature Engineering):** Làm sạch dữ liệu, mã hóa biến phân loại, tính toán các chỉ số hành vi.
2. **Xử lý mất cân bằng dữ liệu (Imbalanced Data Handling):** Lượng khách hàng rời bỏ thường chiếm tỷ lệ rất nhỏ  (<15%), đòi hỏi áp dụng kỹ thuật **SMOTE** để nhân bản lớp thiểu số.
3. **Huấn luyện & Đánh giá:** So sánh các thuật toán (Logistic Regression, Random Forest, XGBoost) dựa trên các độ đo **F1-Score** và **AUC-ROC**.

---

## 2. "Phân tích Cohort" AND "Tỷ lệ giữ chân khách hàng"
*(Cohort Analysis & Customer Retention Rate)*

### 2.1. Khái niệm Cohort Analysis
- **Định nghĩa:** Là phương pháp chia người dùng thành các nhóm nhỏ (**Cohorts**) dựa trên một **đặc tính hoặc sự kiện chung** xảy ra trong một khoảng thời gian cố định.
- **Ứng dụng BNPL:** Nhóm các khách hàng thực hiện giao dịch BNPL đầu tiên theo cùng một tháng (ví dụ: *Cohort Tháng 1/2026*, *Cohort Tháng 2/2026*...).

### 2.2. Theo dõi Tỷ lệ giữ chân (Retention Rate)
- **Đường cong suy giảm (Decay Curve):** Theo dõi mức độ "rụng" của khách hàng qua từng mốc thời gian: Tháng 0 (100 %), Tháng 1 (MoM_1), Tháng 2 (MoM_2)...
- **Biểu đồ nhiệt (Heatmap):** Sử dụng ma trận Cohort để phát hiện ra mốc thời gian khách hàng ngưng sử dụng nhiều nhất (thường xảy ra vào tháng thứ 1 sau khi hết các chương trình ưu đãi tân thủ).

### 2.3. Phân tích Cohort đa chiều
- **Theo Danh mục thanh toán (Payment Category):** So sánh tỷ lệ giữ chân giữa người dùng mua *Thời trang* vs người dùng mua *Điện tử/Đồ công nghệ*.
- **Theo Kênh khuyến mãi:** So sánh chất lượng và độ gắn bó của khách hàng đến từ các chiến dịch Marketing khác nhau.

---

## 3. "Ứng dụng XGBoost trong phân loại tài chính"
*(Applying XGBoost in Financial Classification)*

### 3.1. Bản chất thuật toán XGBoost
- **Khái niệm:** **XGBoost (Extreme Gradient Boosting)** thuộc họ thuật toán *Gradient Boosting Decision Tree (GBDT)*.
- **Cơ chế:** Xây dựng chuỗi các cây quyết định tuần tự, trong đó cây phía sau tập trung học và giảm thiểu sai số (loss) của các cây phía trước.

### 3.2. Lý do XGBoost là thuật toán hàng đầu cho dữ liệu bảng Fintech
- **Hiệu năng cao với quan hệ phi tuyến:** Xử lý cực tốt các mối quan hệ phức tạp, không theo đường thẳng giữa hạn mức, tần suất giao dịch và hành vi thanh toán trễ.
- **Kiểm soát Quá khớp (Overfitting):** Tích hợp sẵn cơ chế phạt Regularization (L_1, L_2), giúp mô hình đạt độ ổn định cao khi kiểm thử trên dữ liệu thực tế.
- **Xử lý giá trị khuyết (Missing Values):** Tự động tìm hướng phân nhánh tối ưu cho các ô dữ liệu bị trống mà không bắt buộc phải xóa dòng.
- **Trích xuất tầm quan trọng đặc trưng (Feature Importance):** Cho phép xuất ra danh sách các biến hành vi có ảnh hưởng quyết định nhất đến nguy cơ rời bỏ của khách hàng.

---

## 4. "Dự báo Churn khách hàng thẻ tín dụng / Fintech"
*(Credit Card & Fintech Customer Churn Prediction)*

### 4.1. Sự tương đồng giữa BNPL và Thẻ tín dụng
- Cả hai đều là sản phẩm **tín dụng tiêu dùng ngắn hạn dựa trên hạn mức**.
- Quy trình chung: Cấp hạn mức -> Thực hiện giao dịch -> Đợi kỳ sao kê/đáo hạn ->Thanh toán.

### 4.2. Các nhóm đặc trưng (Features) quan trọng trong Fintech/BNPL
- **Hành vi tín dụng & Thanh toán:**
  - Số lần thanh toán trễ hạn (Overdue count).
  - Số lần phát sinh phí phạt.
  - Tỷ lệ sử dụng hạn mức (Credit Utilization = Dư nợ / Hạn mức).
- **Hành vi giao dịch (Mô hình RFM):**
  - **Recency:** Số ngày kể từ lần giao dịch BNPL gần nhất.
  - **Frequency:** Tần suất phát sinh đơn hàng BNPL trung bình mỗi tháng.
  - **Monetary:** Giá trị đơn hàng trung bình (AOV).
- **Tương tác ứng dụng:** Tần suất mở app ví điện tử, sự thay đổi danh mục chi tiêu.

### 4.3. Đặc thụ gán nhãn Churn trong BNPL
- Khách hàng không bấm nút "Hủy tài khoản" mà chỉ đơn thuần ngừng phát sinh giao dịch mới.
- **Quy tắc gán nhãn:** Khách hàng được coi là Churn nếu không phát sinh bất kỳ giao dịch BNPL mới nào trong vòng > 60 hoặc 90 ngày tính đến thời điểm chốt dữ liệu.
---

