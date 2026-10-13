# Tư Vấn Pháp Luật (tvpl)

Skill tư vấn pháp luật Việt Nam cho agent — vận hành theo cơ chế **PDCA Cascade-Driven**: khởi tạo Tọa độ & SOT thô, chạy vòng lặp Tra cứu – So khớp – Mở rộng, rồi tư vấn đường lối xử lý dựa trên Source of Truth trích dẫn nguyên văn.

## Tính năng

- **Định danh vấn đề theo 5 trục**: Đối tượng, Hành vi, Tác động, Phạm vi, Thời điểm.
- **PDCA Cascade**: Vòng lặp Plan – Do – Check – Act để nuôi lớn SOT (Source of Truth) từ thô đến hoàn chỉnh.
- **Cross-reference 3 chiều**: Tra chéo VB gốc – sửa đổi – Nghị định/Thông tư hướng dẫn theo chiều xuống, ngang và thời gian.
- **Trích dẫn nguyên văn có tọa độ**: Chuẩn `[Cấp VB] [Số hiệu] – Điều – Khoản – Điểm`.
- **Xử lý xung đột pháp lý**: Lex Superior / Lex Posterior / Lex Specialis.
- **Lưu vết bất biến**: Immutable Multi-file Ledger theo từng Phase (`legal_phase_X.md`).
- **Báo cáo tư vấn 5 phần**: `legal_report_[chủ_đề].md` (Tóm tắt, SOT, Phân tích phương án, Khuyến nghị & Lộ trình, Cảnh báo).
- **Fast Path siêu tốc (§0)**: Hỗ trợ tra cứu nhanh tình trạng hiệu lực văn bản trong 3 bước mà không cần khởi tạo phase hay report.
- **Quality Gate 12 điểm**: Kiểm tra chất lượng trước khi xuất đầu ra.

## Cấu trúc

```
tvpl/
├── SKILL.md                          # Định nghĩa skill + quy trình PDCA
├── LICENSE                           # Giấy phép mã nguồn mở (MIT)
├── README.md                         # Tài liệu giới thiệu & hướng dẫn sử dụng
├── resources/
│   ├── legal-system.md               # Thứ bậc, hiệu lực, xung đột VBQPPL (Luật Ban hành VBQPPL 2025)
│   ├── cross-reference-guide.md      # Tra chéo 3 chiều
│   ├── citation-format.md            # Chuẩn trích dẫn + template SOT chuẩn
│   ├── search-sources.md             # Nguồn tin cậy, cú pháp tìm kiếm & Fast Path
│   ├── adversarial-patterns.md       # Tổng hợp bẫy pháp lý & kịch bản phản đề
│   ├── template_phase.md             # Template mẫu file lưu vết nghiên cứu (legal_phase_X.md)
│   ├── template_report.md            # Template mẫu báo cáo tư vấn chính thức (legal_report.md)
│   └── domains/                      # Bản đồ quy trình theo lĩnh vực chuyên sâu
│       ├── 01-dan-su.md              # Dân sự & Gia đình
│       ├── 02-hinh-su-hanh-chinh.md  # Hình sự & Hành chính
│       ├── 03-doanh-nghiep-lao-dong.md # Doanh nghiệp & Lao động
│       ├── 04-dat-dai-xay-dung.md    # Đất đai & Xây dựng
│       ├── 05-thue-tai-chinh.md      # Thuế & Tài chính
│       ├── 06-chuyen-nganh-khac.md   # Chuyên ngành khác (SHTT, Môi trường, An ninh mạng...)
│       ├── 07-dau-thau.md            # Đấu thầu & Mua sắm công (Luật ĐT 2023, NĐ 214/2025)
│       └── 08-hanh-chinh-khieu-nai.md # Hành chính & Khiếu nại, Kiến nghị đấu thầu
```

## Sử dụng

Kích hoạt skill khi user đề cập đến các vấn đề pháp lý như:

- `pháp luật`, `tư vấn luật`, `tranh chấp`, `bị kiện`, `nghị định`
- `tôi phải làm gì`, `luật quy định thế nào`, `xử lý tình huống này`
- `muốn khiếu nại`, `đòi bồi thường`, `thành lập công ty`, `kiến nghị đấu thầu`

### Luồng làm việc chính

1. **Fast Path**: Tra cứu hiệu lực văn bản thuần túy $\to$ Trả lời ngay 2-3 dòng, không sinh file.
2. **Bước 0**: Định danh 5 trục + khởi tạo `legal_research_[chủ_đề]/legal_phase_X.md` (dựa theo `template_phase.md`).
3. **Bước 1**: Chạy PDCA Cascade — tra cứu, so khớp, rà soát bẫy `adversarial-patterns.md`, lưu vết IPO, cập nhật bảng SOT.
4. **Bước 2**: Đóng gói Phase + tạo `legal_report_[chủ_đề].md` (dựa theo `template_report.md`) với cấu trúc 5 phần.

## Yêu cầu Môi trường & Runtime Tools

Skill được thiết kế mang tính portable (độc lập runtime), yêu cầu môi trường hỗ trợ:
- **Công cụ tra cứu web**: Bất kỳ tool web search / fetch nào (ví dụ: `search_web`, `web_search`, `read_url_content`, `web_fetch`).
- **Công cụ tương tác**: Giao tiếp hỏi đáp với người dùng (`ask_question` hoặc tương tác trực tiếp qua hội thoại).
- **Công cụ tập tin**: Tạo và đọc file tương đối trong workspace (`write_file`, `read_file`, `skill_view`).

## Disclaimer

> Nội dung tư vấn mang tính tham khảo sơ bộ, không thay thế ý kiến pháp lý chính thức từ luật sư có chứng chỉ hành nghề hoặc cơ quan Nhà nước có thẩm quyền.

## License

Dự án được phân phối dưới giấy phép [MIT License](LICENSE).
