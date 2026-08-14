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
- **Quality Gate 12 điểm**: Kiểm tra chất lượng trước khi xuất đầu ra.

## Cấu trúc

```
tvpl/
├── SKILL.md                          # Định nghĩa skill + quy trình PDCA
├── resources/
│   ├── legal-system.md               # Thứ bậc, hiệu lực, xung đột VBQPPL
│   ├── cross-reference-guide.md      # Tra chéo 3 chiều
│   ├── citation-format.md            # Chuẩn trích dẫn + template SOT
│   ├── search-sources.md             # Nguồn tin cậy + cú pháp tìm kiếm
│   └── domains/
│       ├── 01-dan-su.md              # Dân sự & Gia đình
│       ├── 02-hinh-su-hanh-chinh.md  # Hình sự & Hành chính
│       ├── 03-doanh-nghiep-lao-dong.md # Doanh nghiệp & Lao động
│       ├── 04-dat-dai-xay-dung.md    # Đất đai & Xây dựng
│       ├── 05-thue-tai-chinh.md      # Thuế & Tài chính
│       └── 06-chuyen-nganh-khac.md   # Chuyên ngành khác
```

## Sử dụng

Kích hoạt skill khi user đề cập đến các vấn đề pháp lý như:

- `pháp luật`, `tư vấn luật`, `tranh chấp`, `bị kiện`, `nghị định`
- `tôi phải làm gì`, `luật quy định thế nào`, `xử lý tình huống này`
- `muốn khiếu nại`, `đòi bồi thường`, `thành lập công ty`

### Luồng làm việc chính

1. **Bước 0**: Định danh 5 trục + khởi tạo `legal_research_[chủ_đề]/legal_phase_X.md`.
2. **Bước 1**: Chạy PDCA Cascade — tra cứu, so khớp, lưu vết IPO, cập nhật bảng SOT.
3. **Bước 2**: Đóng gói Phase + tạo `legal_report_[chủ_đề].md` với cấu trúc 5 phần.

## Yêu cầu

- Tool tra cứu web (`search_web`, `read_url_content`) để tìm nguồn VBQPPL.
- Bắt buộc trích dẫn nguyên văn có tọa độ từ các nguồn đã được xác minh.

## Disclaimer

> Nội dung tư vấn mang tính tham khảo, không thay thế ý kiến pháp lý chính thức từ luật sư hoặc cơ quan có thẩm quyền.

## License

© 2026 phongsun01. Được phát hành công khai trên GitHub.
