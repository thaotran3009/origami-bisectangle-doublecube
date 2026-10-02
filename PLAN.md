# Kế hoạch thực hiện: Origami và sức mạnh giải quyết bài toán cổ điển

## Định dạng kỹ thuật

Tiểu luận được biên soạn bằng **LaTeX** (dùng engine `xelatex` hoặc `pdflatex`), vì:

- Tiêu chuẩn vàng trong học thuật: Xử lý công thức toán học, căn lề, đánh số phương trình và tham chiếu chéo chính xác tuyệt đối.
- Hỗ trợ gói **TikZ**: Cho phép vẽ trực tiếp đồ thị tiếp tuyến parabol và sơ đồ nếp gấp (crease pattern) bằng code vector ngay trong file nguồn, giữ độ sắc nét tối đa khi in/xuất PDF.
- Quản lý tài liệu tham khảo đồng bộ và chuẩn hóa qua BibTeX (`.bib`).
- Quản lý mã nguồn dạng văn bản thuần bằng Git dễ dàng; cấu trúc mô-đun hóa thuận tiện qua lệnh `\input{...}` hoặc `\include{...}`.

## Cấu trúc thư mục dự kiến
```
origami-geometric-constructions/
├── README.md
├── PLAN.md
├── main.tex                  # File master, tập hợp toàn bộ các phần
├── sections/
│   ├── 00-mo-dau.tex
│   ├── 01-gioi-han-euclid-va-tien-de-6.tex
│   ├── 02-thuc-nghiem-chia-ba-goc.tex
│   ├── 03-thuc-nghiem-nhan-doi-lap-phuong.tex
│   └── 04-ket-luan.tex
├── assets/
│   ├── figures/              # Sơ đồ vẽ bằng TikZ hoặc file SVG/PDF vector
│   └── photos/               # Ảnh chụp thực tế thao tác gập từng bước
└── bibliography/
└── references.bib        # File trích dẫn BibTeX (Lang, Hull, Abe, Messer, ...)
```
## Quy ước kỹ thuật trong LaTeX

- **Ký hiệu & Môi trường toán**:
  - Dùng chuẩn `amsmath`, `amssymb`, `mathtools`.
  - Macro cho các ký hiệu thường dùng (ví dụ: `\ang{60}` cho $60^\circ$).
  - Môi trường định lý, bổ đề, tiên đề dùng `amsthm` với numbering thống nhất.
- **Vẽ sơ đồ & Hình học (TikZ)**:
  - Tiếp tuyến chung của hai Parabol: Dựng tọa độ chuẩn xác trong môi trường `tikzpicture`.
  - Quy ước nếp gấp: Nét đứt (`dashed` / `dashdotted`) theo chuẩn ký hiệu Origami.
  - Sử dụng tham số `[H]` (gói `float`) để chống trôi hình vẽ qua mục khác.
- **Trích dẫn**: Dùng `biblatex` hoặc BibTeX với citation style dạng số chuẩn IEEE (`\cite{...}`).
- **Bảng số liệu & Sai số**: Dùng `tabularx`, định dạng lề ô vừa khít trang A4, tích hợp `siunitx` để định dạng góc, độ dài và sai số phần trăm.

## Các giai đoạn thực hiện (Lộ trình 2 tuần)

### Giai đoạn 1 — Nghiên cứu lý thuyết & Soạn thảo thực nghiệm (Tuần 1)

- [x] **Ngày 1 – 3: Khung LaTeX, Lý thuyết cơ sở & Tiên đề 6**
  - [x] Khởi tạo khung dự án LaTeX.
  - [x] Phân tích đại số: Vì sao Thước kẻ - Compa dừng ở bậc $2^k$; Tiên đề 6 giải phương trình bậc 3 qua tiếp tuyến chung parabol.
  - [x] Viết xong bản thảo `sections/00-mo-dau.tex` và `sections/01-gioi-han-euclid-va-tien-de-6.tex`.
  - [x] Dựng sơ đồ TikZ minh họa tiếp tuyến chung hai parabol trên hệ trục $Oxy$.
- [x] **Ngày 4 – 5: Soạn thảo quy trình thực nghiệm & Số liệu đo đạc**
  - [x] Viết `sections/02-thuc-nghiem-chia-ba-goc.tex` (phương pháp Abe Hisashi): Hoàn thiện các bước và sơ đồ TikZ chuẩn góc chia 3.
  - [x] Viết `sections/03-thuc-nghiem-nhan-doi-lap-phuong.tex` (phương pháp Peter Messer): Chuẩn hóa theo quy trình gập góc $A \to BC$ và $E \to L_2$, bảng sai số đo đạc đóng khung vừa vặn khổ A4.
- [x] **Ngày 6 – 7: Viết phần kết luận**
  - [x] Hoàn thiện bản thảo `sections/04-ket-luan.tex`.

### Giai đoạn 2 — Rà soát, Biên tập & Đóng gói (Tuần 2)

- [ ] **Ngày 8 – 10: Rà soát tính nhất quán & Cấu hình master file**
  - [ ] Tạo file `main.tex`, `preamble.tex` tích hợp đầy đủ các gói (`tikz`, `tabularx`, `siunitx`, `float`).
  - [ ] Hoàn thiện file trích dẫn `bibliography/references.bib` (Abe, Messer, Lang, Hull).
  - [ ] Nạp các file con vào `main.tex` qua lệnh `\input{...}`.
- [ ] **Ngày 11 – 12: Tinh chỉnh thẩm mỹ & Layout**
  - [ ] Kiểm tra hiển thị hình vẽ TikZ, font chữ tiếng Việt Unicode.
  - [ ] Tinh chỉnh ngắt trang, kiểm tra không bị lỗi tràn lề (Overfull `\hbox`).
- [ ] **Ngày 13 – 14: Đọc soát tổng thể & Xuất bản PDF**
  - [ ] Soát lỗi chính tả và thuật ngữ hình học.
  - [ ] Biên dịch file PDF hoàn chỉnh (~15 trang) và dọn dẹp kho lưu trữ.

## Theo dõi tiến độ từng phần

| STT | Phần / Nội dung | File nguồn | Trạng thái | Hình ảnh / TikZ |
|:---:|---|---|:---:|:---:|
| 0 | Mở đầu | `00-mo-dau.tex` | Đang rà soát | - |
| 1 | Giới hạn Euclid & Bản chất Tiên đề 6 | `01-gioi-han-euclid-va-tien-de-6.tex` | Đang rà soát | ✅ TikZ Parabol Oxy |
| 2 | Thực nghiệm: Chia 3 góc (Abe) | `02-thuc-nghiem-chia-ba-goc.tex` | Đang rà soát | ✅ 3 sơ đồ TikZ thao tác |
| 3 | Thực nghiệm: Dựng $\sqrt[3]{2}$ (Messer) | `03-thuc-nghiem-nhan-doi-lap-phuong.tex` | Đang rà soát | ✅ 3 sơ đồ TikZ + Bảng sai số |
| 4 | Kết luận | `04-ket-luan.tex` | Đang rà soát | - |
| - | Tài liệu tham khảo | `references.bib` | Chưa bắt đầu | - |

## Rủi ro & Biện pháp khắc phục

- **Hiện tượng trôi hình TikZ**: Khắc phục bằng tùy chọn `[H]` của gói `float`.
- **Tràn bảng số liệu khổ A4**: Dùng môi trường `tabularx` với cột giãn linh hoạt `X`, kết hợp `\small` và `siunitx`.
- **Lỗi font tiếng Việt**: Biên dịch bằng `xelatex` hoặc `lualatex` với gói `fontspec`.