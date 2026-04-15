[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23572449&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** 26ai.dungnt@vinuni.edu.vn
**Name:** Nguyễn TIến Dũng

---

## Mo ta

(Mo ta ngan gon bai lab va nhung gi ban da lam)
Tôi chủ yếu sửa file solution.py để nó có thể lọc dữ liệu, chay generate_garbage.py để lấy file data rác và dùng solution.py tạo processed_data.csv.
---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
# Mo ta cach ban chay thi nghiem Clean vs Garbage data
```
- Chạy generate_garbage.py -> Tạo garbage_data.csv
- Sửa solution.py và chạy -> Tạo processed_data.csv
- Chạy agent_simulation.py -> Thêm báo cáo cho experiment_report.md


---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

(Tom tat ket qua: bao nhieu records da xu ly, bao nhieu bi loai, v.v.)
solution.py đã xử lý file raw_data.json và lọc được 3 records, 2 records bị loại
Chạy agent_simulation.py ra kết quả đã nói trên experiment_report.md