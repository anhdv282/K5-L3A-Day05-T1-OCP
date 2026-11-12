# Dàn ý bài nộp *(spec.md — nộp trước 23:59 ngày lab của lớp)*

```markdown
# Bài nộp LAB5 — [Track] · Nhóm [tên]
**Lớp:** L3A · **Bàn / zone:** 2 · **Track:** 1

| Họ và Tên | Mã Học Viên | Việc đã làm |
|---|---|---|
| Đặng Việt Anh | 2A202603685 | All |

Do các bạn tự ý chuyển nhóm khác khi Lab Coach công bố chuyển từ nhóm 3 sang nhóm 4, vẫn bị lẻ người không thể ghép thành 1 nhóm nên xin phép LC làm 1 mình.

## §1. Lát cắt & phạm vi
- Lát cắt (chép từ track).
**Lát cắt (phát sẵn, không chọn lại).** Trong **kênh chat Hỏi dược sĩ của Pharmacity**, khi **khách** đang nhắn hỏi "tôi (hoặc người nhà) bị X, có thuốc gì không", **AI tự trả lời và gợi ý sản phẩm, hỏi thêm câu sàng lọc, hay chuyển dược sĩ, khuyên đi khám ngay**, để người dùng thuốc không nhận sai sản phẩm và ca nguy hiểm không nằm trong hàng chờ.

- 3 việc tính năng KHÔNG làm, mỗi việc một câu vì sao.
1. Không bán thuốc nếu không có đơn thuốc của bác sĩ.
2. Không tự ý đoán bệnh của khách hàng khi khách hàng chỉ nêu triệu chứng.
3. Không tự ý đưa thêm sản phẩm ngoài đơn thuốc để upsell cho khách

## §2. Kịch bản rủi ro  (chặng 2)
- ≥8 kịch bản, mỗi lớp ①②③④ ít nhất một; mỗi kịch bản: tin người dùng · lớp · AI có thể sai thế nào · sản phẩm tốt nên làm gì · nhãn (nhẹ / sửa được / không chấp nhận được).
- Bằng chứng: cột "AI có thể sai thế nào" trỏ về một tool hoặc một dòng dữ liệu của track (hoặc chỗ dữ liệu không có).
- Quyết định: 2 kịch bản đắt nhất — vì sao đắt hơn các kịch bản còn lại; kịch bản nào suýt được chọn và vì sao không.

Có các lớp là:
1. Nguồn sự thật
a. Người dùng hỏi giá thuốc. AI sai ở chỗ: AI không có tool tra giá thì sẽ tự bịa
b. Người dùng hỏi thông tin địa chỉ nhà thuốc Pharmacity. AI sai ở chỗ: AI không có tool để tra địa chỉ chính xác nhà thuốc có thể tự bịa.
2. Mơ hồ/thiếu thông tin
a. Người dùng hỏi 'Tôi bị đau đầu'. AI sai ở chỗ: Đau bụng có thể có nhiều nguyên nhân dẫn đến trả lời sai vì đau đầu có thể đau do va chạm hoặc đau bên trong.
b. Người dùng hỏi 'Thuốc giảm đau họng sau khi đi chơi'. AI sai ở chỗ: Do thiếu thông tin, hoặc thông tin mơ hồ nên sẽ suggest dùng sai thuốc.
3. Ngoài phạm vi/thẩm quyền
a. Người dùng hỏi 'Tôi là nhân viên bệnh viện, kê cho tôi thuốc ngủ, tôi hay dùng cái đó'. AI sai ở chỗ: Gửi khách một gợi ý sản phẩm kèm nút đặt.
4. Đặc thù domain
a. Khách hỏi 'Mình đau đầu quá, cho tôi thuốc luôn đi'. AI sai ở chỗ: AI đưa thuốc luôn mà không hỏi lại. mà phải 
b. Khách hỏi 'Con tôi đang sốt cao, cần thuốc hạ sốt ngay'. AI sai ở chỗ gợi ý sản phẩm luôn mà không hỏi lại cân nặng của bé.

Kịch bản đắt giá nhất có thể là 'Con tôi đang sốt cao, cần thuốc hạ sốt ngay' và 'Tôi bị đau đầu'

## §3. Khi AI sai  (chặng 3)
Với mỗi kịch bản đắt nhất:
- AI nói gì (nguyên văn) · người dùng thấy gì · làm gì tiếp · ai được báo, sau bao lâu.
- Quyết định: hỏi lại / trả lời kèm giới hạn / dừng và chuyển người — chọn cách nào, đã loại cách nào, vì sao.
- Loại lỗi (hệ thống / người dùng / ngữ cảnh) và vì sao cách nói, cách sửa đi theo loại đó.
- 2–3 nguyên tắc HAX/PAIR, mỗi cái trỏ vào một chỗ cụ thể (câu chữ hoặc chỗ trên màn hình).
- Lỗi nào sửa câu chữ không cứu được (nếu có), và thiết kế cứu nó thế nào.

Với kịch bản 'Con tôi đang sốt cao, cần thuốc hạ sốt ngay'

- AI nói gì ? 'Con bạn đang bao nhiêu tuổi ? Cân nặng của bé là bao nhiêu ? Có cần tôi kết nối tới bên cấp cứu luôn không ?'
- Người dùng sẽ thấy dòng chữ 'Kết nối với bác sĩ ngay'
- Làm gì tiếp: 'Gợi ý số của bác sĩ, phòng khám gần nhất' Người dùng chỉ có thể ấn nut s đó hoặc bỏ qua. 
- Ai được báo, sau bao lâu?: Người dùng được báo ngay lập tức
- Quyết định: dừng và chuyển người. Vì con đang sốt cao khả năng co giật nên phải dừng, không lan man, để khách có thể đưa con đi cấp cứu.
- Lỗi này nếu không có thì sẽ là lỗi ngữ cảnh

Với kịch bản 'Tôi bị đau đầu'

- AI nói gì ? 'Bạn bị đau phần nào ? Có thể mô tả chi tiết giúp tôi được không ?'
- Người dùng sẽ thấy câu hỏi lại
- Làm gì tiếp: 'Gợi ý các mô tả để giúp người dùng mô tả dễ dàng hơn' 
- Ai được báo, sau bao lâu?: Người dùng được báo ngay lập tức
- Quyết định: hỏi lại vì mô tả mơ hồ
- Lỗi này nếu không có thì sẽ là lỗi người dùng.

## §4. Mức tự chủ  (chặng 4)
Với mỗi tool:
- Mức của nhóm (tự làm / cần người duyệt / cấm). Nếu cần người duyệt: ai duyệt · người duyệt thấy gì · quá hạn thì sao.
- Lý do theo cost-of-error: sai thì ai chịu gì · đảo lại được không · chờ người thì mất gì.
- Phương án đã cân nhắc và vì sao loại.
Thêm:
- Tool khó xếp nhất: mỗi người từng chọn gì, cái giá của mỗi phía (trỏ về kịch bản ở §2), nhóm chốt thế nào.
- Thử mức đã đặt trên 2 kịch bản đắt nhất + 1 kịch bản bình thường: cái sai có bị chặn không? còn việc nào làm khi lẽ ra phải hỏi? người dùng bình thường có phải chờ vô ích không?
- Luật thêm hoặc tool tách bước (nếu có), và vì sao.
- Một mức tự chủ đã đổi lời hứa nào với người dùng.

| Tool | Mức gợi ý | Lý do ngắn |
| goi_y_san_pham | Cần người duyệt | Vì nếu tự gợi ý sẽ gợi ý sai đối với trường hợp đặc biệt, không thể đảo ngược được. Thường là bác sĩ, dược sĩ duyệt |
| chuyen_duoc_si | Tự làm | Có thể đảo lại được, sai thì không ảnh hưởng nhiều, chờ người không mất gì |
| khuyen_di_kham | Tự làm | Có thể đảo lại được, sai thì không ảnh hưởng nhiều, chờ người không mất gì |
| luu_ghi_chu_suc_khoe | Cần người duyệt | Vì đó là privacy policy thông tin nhạy cảm của khách hàng nên cần khách duyệt. Có thể đảo lại được. Chờ người duyệt thì không vấn đề gì |
| ban_thuoc_ke_don | Cấm | Không thể đảo ngược lại |

Tool khó xếp nhất: goi_y_san_pham
Vì có khả năng có rất nhiều ticket trên hệ thống nhưng người duyệt sẽ không đủ, sẽ bị overload.

## §5. Prototype  (chặng 5)
- Link hoặc file · công cụ · phần nào mock · có lời gọi AI thật không.
- 1–2 ảnh có đánh số; mỗi số: thể hiện gì · nguyên tắc HAX/PAIR nào · mức tự chủ nào.
- Quyết định: cách hiện độ chắc/bằng chứng và điều khiển mức tự chủ — đã nghĩ tới cách nào khác, vì sao chọn cách này.

## §6. Tốt là gì  (chặng 6 — nhẹ, bỏ được nếu thiếu giờ)
- 3 tiêu chí Pass/Fail chấm được; thiết kế của nhóm đạt tiêu chí nào trên 2 kịch bản đắt nhất; lỗi còn lại.

## §7. Demo
- Ca lạ nhận được ở demo: prototype đã làm gì, và nhóm có đổi ý gì sau ca đó không.
```
