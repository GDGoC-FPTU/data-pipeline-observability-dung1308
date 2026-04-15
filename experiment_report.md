# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-2A202600219
**Name:** Nguyễn Tiến Dũng
**Date:** 15/04/2026

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Based on my data, the best choice is Laptop at $1200. | 10/10 | Category đúng và giá được áp dụng giảm giá đúng. |
| Garbage Data (`garbage_data.csv`) | Based on my data, the best choice is Nuclear Reactor at $999999. | 3/10 | Nó xác định được category, nhưng giá cả không hợp lệ và không được áp dụng giảm giá, và tại sao Nuclear Reactor lại được đặt vào electronics ? Nuclear Reactor nên để category khác. |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

(Viet nhan xet cua ban o day — it nhat 50 tu)

(Hay phan tich cac van de nhu Duplicate IDs, wrong data types, outliers, null values
va giai thich tai sao chung anh huong den ket qua cua Agent.)
Nếu dùng Agent thật, khi dùng Garbage Data thay vì processed_data, Agent trả lời sai. Lý do là:
- Duplicate IDs:  Khi garbage_data chứa 2 dòng có cùng một ID là 1, Agent sẽ bị bối rối là hai dòng đó là cùng 1 sản phẩm hoặc coi 2 dòng đó là dòng bị lỗi và bỏ qua.
- Wrong data types: Row chứa id = 2, giá trị trong cột price không cùng data type so với các dòng khác. Lỗi này sẽ làm phức tạp hóa về giá trị, agent có thể nghĩ rằng "ten dollars" chỉ là 1 text hay coi string đó là lỗi hoặc giá trị theo cách chuyển đổi giá ngoại tệ,
- outliers: Giá trị $999999 là một giá trị vô lý. Giá trị này thường xuất hiện khi không tìm được giá trị. Do giá trị này quá lớn nên Agent mới trả lời "the best choice is Nuclear Reactor at $999999"
- null values: Thông thường, người ta dự tính đến tình huống này, các trường có giá trị null nên bị bỏ qua hoặc thay thế bằng một giá trị mặc định mà không ảnh hưởng nhiều đến câu trả lời của Agent. Nếu không làm như vậy, Agent sẽ phân vân và trả lời sai.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** (Dong y hay khong? Giai thich ngan gon.)

Đồng ý
Quality Data > Quality Prompt là điều tôi có thể khẳng định là đúng. Lý do là vì:
- Quality Prompt: Chỉ giải quyết được phần "ngọn", chỉ truy xuất dữ liệu và tổng hợp lại.
- Quality Data: Giải quyết tận "gốc" (tính chính xác của logic nghiệp vụ).
Khi Data chuẩn (đúng kiểu dữ liệu, không trùng ID, không giá trị rỗng), AI Agent sẽ hoạt động ổn định và ít gặp lỗi logic hơn ngay cả khi Prompt chỉ ở mức trung bình.
