<h1 align="center">📘 Research Collaboration Detection in Data Science  
<br>(Phát hiện nhóm hợp tác trong cộng đồng nghiên cứu Data Science)</h1>

<p align="center">
  <img src="https://img.shields.io/github/languages/top/Nhatnam213/research-collaboration-detection?color=00eaff&label=Python&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/Status-Completed-green?style=flat-square" />
  <img src="https://img.shields.io/badge/Data-OpenAlex-blue?style=flat-square&logo=open-access" />
  <img src="https://img.shields.io/badge/NetworkX-Analysis-yellow?style=flat-square&logo=networkx" />
</p>

---

# 🧩 **1. Giới thiệu (Introduction)**  
Nghiên cứu này tập trung phân tích **mạng đồng tác giả (co-author network)** trong lĩnh vực *Data Science*, sử dụng dữ liệu thu thập từ **OpenAlex API**.  
Mục tiêu của dự án:

- Xây dựng mạng đồng tác giả từ dữ liệu thực (Build co-author graph from OpenAlex).
- Phát hiện cộng đồng bằng Louvain, Leiden, Fast Greedy (Detect communities using 3 algorithms).
- Đánh giá mức độ ảnh hưởng của tác giả bằng các chỉ số centrality (Analyze author influence via centrality metrics).
- Trực quan hóa mạng và các nhóm cộng đồng lớn nhất (Visualize communities and graph structure).

---

# 🗂 **2. Dataset — OpenAlex**  
Nguồn dữ liệu: **OpenAlex (CSDL học thuật mở)**  
- Tập trung vào lĩnh vực *Data Science*, *Machine Learning*, *Artificial Intelligence*  
- Khoảng **2,400 bài báo** được trích xuất  
- Trường thông tin chính:

| Field | Mô tả (Description) |
|-------|----------------------|
| Work_ID | Mã bài báo |
| Title | Tiêu đề |
| Year | Năm công bố |
| Cited_by | Số lượt trích dẫn |
| Authors | Danh sách tác giả |
| Author_IDs | Mã tác giả |
| Concepts | Chủ đề liên quan |

---

---

# 🕸 **4. Xây dựng mạng đồng tác giả (Co-author Network)**  
- Mỗi node = một tác giả  
- Mỗi edge = hai tác giả cùng viết ≥ 1 bài  
- Trọng số cạnh = số lượng bài hợp tác  

👉 Một phần thống kê mạng:

| Statistic | Value |
|----------|--------|
| Nodes | **9,212** |
| Edges | **136,198** |
| Density | 0.0032 |
| Avg Degree | 29.57 |
| Clustering Coefficient | 0.8608 |

---

# 🔍 **5. Thuật toán phát hiện cộng đồng (Community Detection Algorithms)**  

Dự án sử dụng **3 thuật toán phổ biến nhất**:

| Thuật toán | Mô tả ngắn | Ưu điểm | Nhược điểm |
|-----------|------------|---------|------------|
| **Louvain** | Tối ưu modularity lặp (Optimize modularity) | Nhanh, xử lý mạng lớn | Có *resolution limit* |
| **Leiden** | Cải tiến Louvain, đảm bảo cộng đồng liên kết chặt (Well-connected communities) | Ổn định nhất, modularity cao nhất | Tính toán phức tạp hơn |
| **Fast Greedy** | Gom cụm phân cấp bottom-up | Nhanh, đơn giản | Modularity thấp hơn |

---

# 📊 **6. Bảng so sánh thuật toán (Algorithm Comparison Table)**  

| Algorithm | Communities | Modularity Q |
|----------|-------------|--------------|
| **Louvain** | 1,167 | 0.9416 |
| **Leiden** | 1,167 | 0.9418 *(cao nhất)* |
| **Fast Greedy** | 1,164 | 0.9344 |

⭐ **Kết luận:** *Leiden hoạt động tốt nhất*, Louvain gần tương đương, Fast Greedy nhanh nhưng Q thấp hơn.

---

# 🔗 **7. Đánh giá mức tương đồng phân cụm (Cluster Similarity Metrics)**  

| Cặp thuật toán | NMI | ARI |
|----------------|-----|-----|
| Louvain – Leiden | 0.8004 | 0.2263 |
| Louvain – Fast Greedy | 0.7971 | 0.2146 |
| **Leiden – Fast Greedy** | **0.9909** | **0.9119** |

→ Leiden & Fast Greedy cho kết quả gần như giống nhau.

---

# 🌐 **8. Phân tích Centrality (Author Influence Metrics)**  

Dự án sử dụng 4 chỉ số trung tâm (centrality):

| Chỉ số | Ý nghĩa |
|--------|---------|
| **Degree** | Số lượng hợp tác trực tiếp |
| **Betweenness** | Vai trò cầu nối giữa các nhóm |
| **Closeness** | Tính gần gũi trung bình tới mọi nút |
| **Eigenvector** | Ảnh hưởng toàn cục |

Các tác giả ảnh hưởng nhất:

- John P. A. Ioannidis (Betweenness cực cao)
- Chris Mungall (Eigenvector cao nhất)
- Curtis Huttenhower
- Karen Christie
- Susan Holmes  

---

# 🖼 **9. Trực quan hóa (Visualization)**  

- Các cộng đồng được tô màu riêng biệt
- Kích thước node biểu diễn centrality
- Layout Force-directed (Spring layout)

*(Hình trực quan hóa được đặt trong repo)*

---

# 💬 **10. Thảo luận (Discussion)**  

Một số phát hiện chính:

- Mạng có **tính phân cụm rất mạnh** (Q ≈ 0.94)  
- Leiden ổn định nhất khi phát hiện cộng đồng  
- Fast Greedy phù hợp khi cần tốc độ  
- Mạng mang cấu trúc *hub–spoke* (trung tâm–vệ tinh)  
- Một số nhà nghiên cứu đóng vai trò "cầu nối tri thức"  

---

# 🧾 **11. Kết luận (Conclusion)**  

Dự án đã:

✔ Phân tích mạng đồng tác giả Data Science  
✔ Phát hiện cộng đồng bằng 3 thuật toán SOTA  
✔ Trực quan hóa mạng và đánh giá ảnh hưởng tác giả  
✔ Cung cấp góc nhìn toàn diện về hợp tác khoa học  

Hướng phát triển:

- Phân tích mạng động (Dynamic Networks)  
- Ứng dụng Graph Neural Networks (GNNs)  
- Mở rộng phân tích sang nhiều lĩnh vực khoa học khác  

---

# 📚 **12. Tài liệu tham khảo (References)**  
*Danh sách tham khảo chi tiết đã được trình bày trong báo cáo PDF.*

---

# 👨‍💻 **Nhóm thực hiện (Authors)**  
- Hà Thế Anh  
- Nguyễn Nhật Nam  
- Hoàng Quang Minh  
### 🎓 Supervisor  
**Lê Nhật Tùng**  
![Supervisor](https://img.shields.io/badge/Role-Supervisor-blue?style=flat-square)



# 🛠 **3. Quy trình nghiên cứu (Research Pipeline)**  

