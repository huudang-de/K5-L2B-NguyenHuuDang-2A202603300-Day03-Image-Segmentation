# Báo cáo thực hành Day 3 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên [LMS](https://aithucchien.vinuni.edu.vn). Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu.

- Mã học viên theo lớp: 2A202603300
- Họ và tên: Nguyễn Hữu Đăng
- Ngày / CVAT local: 11/11/2026
- Công cụ đã dùng: CVAT local (Brush / Polygon / AI tools)

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task                     | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| ------------------------ | -------------------- | ---------------------: | --------------------------------: |
| easy_semantic            | easy_semantic.zip    |                  3 / 3 |                                20 |
| medium_instance          | medium_instance.zip  |                  3 / 3 |                                32 |
| hard_panoptic            | hard_panoptic.zip    |                  2 / 2 |                                30 |
| cp1_holes                | cp1_holes.zip        |                  1 / 1 |                                 3 |
| cp2_slice                | cp2_slice.zip        |                  1 / 1 |                                 3 |
| cp5_occlusion            | cp5_occlusion.zip    |                  1 / 1 |                                 3 |
| cp3_thin                 | cp3_thin.zip         |                  1 / 1 |                                 3 |
| cp4_curb                 | cp4_curb.zip         |                  1 / 1 |                                 3 |
| cp6_coverage             | cp6_coverage.zip     |                  1 / 1 |                                 3 |
| **Tổng tối đa** |                      |                        |                     **100** |

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: Task `medium_instance`, ảnh `000000181542.jpg`, cụm xe máy ở góc phải phía bà cô mặc áo dài qua đường.
- Class và quy tắc tôi dùng để chọn biên: Class motorcycle , Tôi dùng công cụ draw a mask để tô bám sát đường viền của xe, có hai vật thể person ở giữa nên tô làm 2 lần, bánh xe chỉ ô bánh và lan hoa không tô hết cả khoảng trống trong bánh xe.
- Nếu dùng gợi ý sau đó: vùng gợi ý sai/đúng, hành động sửa/giữ và lý do: Không dùng gợi ý, *vẽ hoàn toàn bằng Draw a mask thủ công theo đúng quy tắc biên trên*.
- Nếu không dùng gợi ý: ghi “không dùng”; vẫn giải thích một quyết định gán nhãn của mình.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: Task `medium_instance`, ảnh 000000458325.jpg, vùng người chính giữa khung ảnh đang trượt ván
- Lỗi thuộc loại: thừa vật
- Bằng chứng tôi nhìn thấy: Trong danh sách class là persion, tôi quên tô cả ván trượt.
- Quy tắc và hành động sửa: Dùng tẩy phần ván trượt, giữa lại đúng chỉ persion.
- Sau sửa đã Save và export lại chưa?: Đã bấm Save trong CVAT và export lại file `medium_instance.zip` vào thư mục `submissions/`.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| 1. `easy_semantic` (ảnh `817bca71-00000000.jpg`, lối driveway bê tông vào gara) | - Cách 1: Gán road vì xe ô tô chạy vào sân.<br>- Cách 2: Gán sidewalk vì nằm sau gờ bó vỉa, ngang cốt vỉa hè. | Quy tắc chuẩn BDD100K: road chỉ tính lòng đường chính. Lối vào nhà (driveway) nằm ngoài mép bó vỉa (curb) nên tính vào vỉa hè. | Quyết định: Gán sidewalk cho toàn bộ các đoạn driveway bê tông dẫn vào nhà; chỉ gán road cho lòng đường nhựa sẫm màu lưu thông chung. |
| 2. `medium_instance` (ảnh `000000181542.jpg`, tà áo dài trắng che bánh xe máy) | - Cách 1: Gộp tà áo vào mask xe máy hoặc khoét tà áo.<br>- Cách 2: Tà áo thuộc person; xe máy bị che thì dừng biên ở mép áo. | Quy tắc Instance: Quần áo thuộc về person. Với vật bị che (motorcycle), chỉ vẽ phần nhìn thấy thực tế, không vẽ đè xuyên qua tà áo. | Quyết định: Vẽ trọn vẹn tà áo dài vào mask người phụ nữ (person); mask xe máy (motorcycle) dừng biên sát mép tà áo, chỉ vẽ phần lộ ra ngoài. |
| 3. `hard_panoptic` (ảnh `000000460147.jpg`, xe lồng chở ô tô 2 tầng ở giữa đường) | - Cách 1: Gộp cả xe lồng và ô tô trên giá thành 1 instance truck.<br>- Cách 2: Xe kéo là truck, từng ô tô con trên giá là instance car riêng. | Quy tắc Panoptic: Nhận diện theo đặc trưng hình thái thị giác (visual semantics). Các xe con trên giá có đầy đủ cấu trúc của một chiếc car. | Quyết định: Gán truck cho đầu xe kéo và khung sắt rơ-moóc; gán car riêng cho từng chiếc xe con được chở ở tầng trên và tầng dưới. |
