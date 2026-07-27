# Case: Personal Finance AI Agent

## 1. Case ví dụ

**Nhân vật:** Tiến, nhân viên văn phòng có thu nhập khoảng **15–20 triệu đồng/tháng**, sống cùng gia đình nên không mất nhiều chi phí thuê nhà nhưng vẫn phải hỗ trợ:

- Tiền chợ
- Tiền điện nước
- Tiền học phí
- Chi phí phát sinh
- Chi phí cá nhân
- Tiền liên hoan, gặp gỡ bạn bè

Vấn đề là các khoản chi không cố định, khiến Tiến khó biết mình đang **chi tiêu vừa phải hay vung tay quá trán**, đồng thời khó dự đoán cuối tháng còn bao nhiêu tiền.

---

## 2. Vì sao đây là ví dụ tốt?

- Có **actor cụ thể**: người đi làm.
- Có **workflow lặp lại**: nhận lương → chi tiêu → hỗ trợ gia đình → tiết kiệm.
- Có **bottleneck rõ ràng**: không kiểm soát được tốc độ chi tiêu.
- Có **dữ liệu lịch sử** để áp dụng machine learning.
- Có thể dùng **LightGBM** để dự đoán và phân loại.
- Có thể dùng **AI Agent** để phân tích và đưa ra khuyến nghị.
- Có metric đo lường được: tỷ lệ tiết kiệm, tỷ lệ vượt ngân sách, F1, ROC-AUC.

---

## 3. Individual Problem Scan

| # | Problem | Dấu hiệu |
|---|---|---|
| 1 | Không biết tiền đang đi đâu | Nhiều khoản chi nhỏ bị quên |
| 2 | Khó cân bằng hỗ trợ gia đình và tiết kiệm | Mỗi tháng tiết kiệm khác nhau |
| 3 | Không biết tổng chi cuối tháng | Chỉ biết sau khi đã tiêu |
| 4 | Không biết có đang vung tay quá trán | Không có hệ thống đánh giá |
| 5 | Không dự đoán được nguy cơ thiếu tiền | Phát hiện quá muộn |
| 6 | Khó điều chỉnh ngân sách | Phải tự tính toán thủ công |

---

## 4. Top 3 Problems

| Rank | Problem | Vì sao chọn |
|---|---|---|
| 1 | Không biết có đang vung tay quá trán | Có thể dùng ML để phân loại |
| 2 | Không dự đoán được tổng chi tiêu | Có thể dùng LightGBM |
| 3 | Khó cân bằng gia đình – cá nhân – tiết kiệm | AI Agent có thể cá nhân hóa |

---

## 5. Actor

### Primary Actor

- Người đi làm

### Secondary Actor

- Gia đình

### AI System

- Personal Finance AI Agent

### Machine Learning Model

- LightGBM

---

## 6. Thời điểm / Bối cảnh

Bài toán xảy ra trong quá trình quản lý tài chính hàng ngày và hàng tháng.

Đặc biệt tập trung vào:

- Đầu tháng: nhận lương và lập kế hoạch
- Trong tháng: phát sinh các khoản chi
- Giữa tháng: đánh giá tốc độ chi tiêu
- Cuối tháng: dự báo số tiền còn lại
- Trước khoản chi lớn: đánh giá khả năng chi trả
- Cuối tháng: phân loại hành vi chi tiêu
- Tháng tiếp theo: điều chỉnh kế hoạch

---

## 7. Current Workflow

```text
Nhận lương
    ↓
Tự lập ngân sách
    ↓
Chi tiêu
    ↓
Hỗ trợ gia đình
    ↓
Chi phí phát sinh
    ↓
Liên hoan / gặp bạn bè
    ↓
Kiểm tra số dư
    ↓
Cuối tháng tổng hợp
    ↓
Tiết kiệm phần còn lại
```

### Bottleneck

Người dùng thường phản ứng sau khi vấn đề đã xảy ra.

Không biết sớm:

- Có đang chi quá nhanh không?
- Cuối tháng có vượt thu nhập không?
- Có đạt mục tiêu tiết kiệm không?

---

## 8. Success Metrics

| Metric | Target |
|---|---|
| Tỷ lệ tháng vượt ngân sách | Giảm |
| Tỷ lệ tiết kiệm | Tăng |
| Thời gian lập kế hoạch tài chính | Giảm |
| Độ chính xác dự đoán tổng chi tiêu | Tăng |
| F1-Score phân loại hành vi chi tiêu | > 0.80 |
| ROC-AUC | > 0.85 |

---

## 9. Non-AI Alternative

Các giải pháp truyền thống:

- Excel / Google Sheets
- App quản lý chi tiêu
- Quy tắc 50/30/20
- Tự lập ngân sách
- Checklist chi tiêu

### Hạn chế

- Không dự đoán tương lai
- Không học từ hành vi cá nhân
- Không phát hiện sớm nguy cơ vượt ngân sách
- Không đưa ra khuyến nghị theo ngữ cảnh

---

## 10. AI Hypothesis

Xây dựng **Personal Finance AI Agent** có khả năng:

- Theo dõi thu nhập và chi tiêu
- Tự động phân loại giao dịch
- Phân tích lịch sử tài chính
- Dự đoán tổng chi tiêu
- Phân loại hành vi chi tiêu
- Cảnh báo nguy cơ vượt ngân sách
- Đề xuất mức tiết kiệm
- Mô phỏng các kịch bản tài chính

---

## 11. ML + LightGBM

Hệ thống sử dụng 2 bài toán chính:

### LightGBM Regression

Dự đoán:

```text
Tổng chi tiêu cuối tháng
```

### Input features

- Thu nhập
- Chi tiêu hiện tại
- Chi tiêu 7/30 ngày gần nhất
- Chi phí gia đình
- Chi phí cá nhân
- Chi phí xã hội
- Chi phí phát sinh

### LightGBM Classification

Phân loại hành vi:

```text
Label 0 = Chi tiêu vừa phải
Label 1 = Chi tiêu vung tay quá trán
```

Một số feature:

- Income
- Total Spending
- Spending / Income Ratio
- Spending Velocity
- Family Support
- Personal Expense
- Social Expense
- Unexpected Expense
- Saving Rate
- Budget Utilization
- Spending Growth Rate
- Days Remaining

---

## 12. Label Engineering

Ví dụ:

```text
IF
Current Spending > Budget
OR
Predicted Spending > Income
OR
Spending Velocity tăng bất thường
OR
Saving Rate giảm mạnh
THEN
Label = 1
→ Chi tiêu vung tay quá trán
ELSE
Label = 0
→ Chi tiêu vừa phải
```

> Label cần được xây dựng từ business rule hoặc dữ liệu lịch sử có nhãn, đồng thời tránh data leakage.

---

## 13. ML Workflow

```text
Financial Data
      ↓
Data Cleaning
      ↓
Feature Engineering
      ↓
LightGBM
      ↓
┌───────────────┬──────────────────┐
│               │                  │
│ Forecasting   │ Budget Risk      │
│ Regression    │ Classification   │
│               │                  │
└───────┬───────┴───────┬──────────┘
        │               │
        ↓               ↓
 Predicted Spending   Risk Score / Label 0 / 1
        │
        └───────────────┬──────────────┘
                        ↓
                   AI Agent
```

---

## 14. AI Agent Architecture

```text
                    User
                      ↓
          Personal Finance AI Agent
                      ↓
        ┌─────────────┼─────────────┐
        ↓             ↓             ↓
 Transaction      Budget         ML Engine
    Agent          Agent         LightGBM
        ↓             ↓             ↓
        └─────────────┼─────────────┘
                      ↓
              Risk Analysis Agent
                      ↓
             Recommendation Agent
                      ↓
              Scenario Simulation
                      ↓
                User Decision
```

### Vai trò

**Transaction Agent**

- Phân loại giao dịch

**Budget Agent**

- Lập và theo dõi ngân sách

**LightGBM**

- Dự đoán chi tiêu
- Phân loại hành vi

**Risk Analysis Agent**

- Phân tích nguyên nhân rủi ro

**Recommendation Agent**

- Đưa ra khuyến nghị cá nhân hóa

---

## 15. Future Workflow

```text
Nhận lương
    ↓
AI phân tích tài chính
    ↓
Lập ngân sách cá nhân
    ↓
Ghi nhận giao dịch
    ↓
LightGBM dự đoán chi tiêu
    ↓
LightGBM phân loại hành vi
    ↓
AI Agent phân tích
    ↓
Cảnh báo / Khuyến nghị
    ↓
Mô phỏng kịch bản
    ↓
Người dùng quyết định
    ↓
Cập nhật hồ sơ tài chính
```

---

## 16. Example

```text
Income = 18 triệu đồng
Current Spending = 10 triệu đồng
Predicted Monthly Spending = 19.5 triệu đồng
Overspending Probability = 82%
Label = 1
→ Chi tiêu vung tay quá trán
```

AI Agent giải thích:

> “Tốc độ chi tiêu hiện tại cao hơn lịch sử. Chi phí liên hoan và chi phí phát sinh tăng mạnh, khiến tổng chi tiêu dự kiến có thể vượt thu nhập.”

### Recommendation

- Giữ nguyên khoản hỗ trợ gia đình
- Hạn chế chi phí xã hội trong thời gian còn lại
- Tạm hoãn mua sắm không cần thiết
- Bảo đảm các khoản chi thiết yếu
- Điều chỉnh mục tiêu chi tiêu cuối tháng

---

## 17. Human Boundary

AI không tự quyết định người dùng phải tiêu tiền như thế nào.

AI chỉ:

```text
Predict
   ↓
Classify
   ↓
Analyze
   ↓
Recommend
   ↓
Simulate
```

Người dùng vẫn quyết định:

- Hỗ trợ gia đình bao nhiêu
- Chi tiêu bao nhiêu
- Tiết kiệm bao nhiêu
- Có làm theo khuyến nghị hay không

---

## 18. Final Concept

```text
ML / LightGBM
→ Dự đoán và phân loại

AI Agent
→ Hiểu ngữ cảnh, phân tích, giải thích và đề xuất

Human
→ Quyết định và hành động
```

> **Personal Finance AI Agent giúp người dùng không chỉ biết “mình đã tiêu bao nhiêu”, mà còn hiểu “mình đang tiêu như thế nào”, dự đoán “cuối tháng sẽ ra sao” và phát hiện sớm “mình có đang vung tay quá trán hay không”.**
