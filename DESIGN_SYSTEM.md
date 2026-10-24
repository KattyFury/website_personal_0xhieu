# Luật thiết kế — 0xhieu.xyz

> Chốt 2026-10-24. Site theo **design system nguyen0xhieu** (Figma `hieu` `IPyKVg7ylGw1mjMRyYVrL7` · bản đọc nhanh: Design System artifact), với 1 biến thể riêng cho site này:
> **ĐEN thay vai trò 0x Blue** (iconic là mèo đen) · **nền TRẮNG** (mắt kính trắng của mèo) · **VÀNG MẮT MÈO** cho chi tiết thiết kế.
> Code ở khối `<style>` duy nhất trong `index.html`, viết theo thành phần, cùng thứ tự các mục dưới đây. Mọi luật ở design system gốc mà file này không nhắc → làm theo gốc.
> **Khoảng cách:** user chốt **gọn theo 16** (đệm box 16, navbar → nội dung 16). Bảng "Website 1440" trong design system gốc (section 96 · khối 64 · đệm thẻ 32/24) **KHÔNG áp** cho site này.

---

## 1. Màu

| Token | Mã | Dùng cho |
|---|---|---|
| `--ground` | `#FFFFFF` | Nền trang |
| `--ink` | `#000000` | Màu chủ đạo: chữ chính · icon · **nút chính** (nền đen chữ trắng) · toggle đang chọn · thẻ rank S/A/B/C · viền focus 2px |
| `--grey` | `#4B5568` | Chữ phụ (mô tả, bullet, nhãn) — mã design system, 7.5:1 |
| `--muted` | `#8B95A8` | Meta, placeholder, ngày, chữ tắt. **Không** dùng cho chữ cần đọc để làm theo |
| `--mist` | `#ECF0F8` | Box phẳng · dòng danh sách · ô nhập · header card Work rank S/A/B/C · hover dòng bảng |
| `--line` | `#DCE3EE` | Kẻ mảnh · viền ô nhập · **nền nút tắt** |
| `--amber` | `#FFA111` | **Vàng mắt mèo** (lấy đúng từ `icon.png`): khối, chấm, vạch. **Chữ trên nền vàng luôn đen** (10.4:1), không bao giờ trắng |
| `--amber-text` | `#965E00` | Vàng **sẫm** cùng hue, cho CHỮ vàng: 5.4:1 trên trắng · 4.7:1 trên mist · 4.8:1 trên `--amber-soft` |
| `--amber-soft` | `#FFF1DB` | Nền nhạt vàng: header card · header bảng · ô kết quả · hover nút phụ |

- Chỉ 3 cấp chữ: `ink` · `grey` · `muted`. Không thêm cấp xám thứ 4.
- Tắt (disabled): nền `--line`, chữ `--muted`, bỏ shadow. **Không giảm opacity.**
- Không gradient (solid là mặc định của design system; nếu sau này thêm thì tối đa 1 vùng/màn).
- **Tối đa 2 màu đi kèm/màn:** vàng mắt mèo (màu THIẾT KẾ) + đỏ (màu NGỮ NGHĨA duy nhất: nguy hiểm, lỗi, xoá — `--red-text #C42B3F` chữ, `--red-soft #FDE8EB` nền badge/ô). Rank Work **không** tô mỗi rank 1 màu — rank phân biệt bằng chữ.
- **Số liệu KHÔNG tô vàng.** Số cần chú ý nhấn bằng **đậm 700 ink**; số nguy hiểm = đỏ.

**Vàng mắt mèo xuất hiện ở đâu** (chỉ chỗ mang nghĩa hoặc nhận diện, không rải trang trí):
- Vạch dưới tab nav đang chọn · vòng quanh ảnh đại diện · chấm timeline · chấm "Available for" · gạch chân khi hover tiêu đề box.
- Nền `--amber-soft`: header box Valuation, header bảng altcoin, header + dải Daily của card `$`.
- Chữ `--amber-text`: link (timeline, popup) · hover tên site / tab nav / tiêu đề màn / tên dự án.
- Viên `--amber` chữ đen: thẻ `rank: $` · nút `$` đang chọn ở thanh lọc.

**Số liệu Valuation:** số thường ink 400 · ×TGE ≥ 13, ×ATH tuần đầu (`×TGE → ×ATH`), narrative median ≥ 13 = **đậm 700 ink** · ×ATM ≥ 15 trong bảng = viên `--red-soft` chữ `--red-text` · ×ATM trong box Vùng nguy hiểm = chữ đỏ · badge FAKE PUMP/PUMP LÁO = viên `--red-soft` chữ đỏ · ×ATM < 1, ×ATL, đáy-trước-đỉnh = grey · ngày TGE = muted (meta).
- Chấm `--amber` 8px cạnh ticker có vcFDV ≥ $300M.

**Rank (Work):** card `$` = header + Daily nền `--amber-soft`, thẻ `rank: $` nền vàng chữ đen. Card S/A/B/C = header + Daily nền `--mist`, thẻ `rank: S` nền đen chữ trắng. Thanh lọc: nút đang chọn đen chữ trắng (`$` vàng chữ đen).

## 2. Chữ

Font hệ thống Apple (`-apple-system, BlinkMacSystemFont, 'SF Pro Text', system-ui…`), máy khác tự lùi. Không webfont ngoài. Chỉ dùng **đúng các style web của design system** (bảng dưới), cỡ tối thiểu 14, **không ngoại lệ**. Letter-spacing theo bảng Inter: 14 −.006em · 16 −.011em · 18 −.014em · 20 −.017em · 24 −.019em · 32+ −.022em. Không VIẾT HOA giãn chữ.

| Style | Cỡ / dòng / đậm | Dùng cho |
|---|---|---|
| web-h2 → web-mobile-h2 | 40/48 700 → mobile 32/40 | Tên người ở hero — duy nhất |
| web-h3 | 24/32 600 | Tiêu đề màn · tiêu đề mục CV · châm ngôn hero (mobile châm ngôn 20/28) |
| web-h4 | 20/28 600 | Tiêu đề card/box · vai trò timeline · tên site · tiêu đề popup — desktop lẫn mobile |
| web-lead | 18/28 400 | Câu niềm tin ở hero (mobile 16/24) |
| web-body / nav-button | 16/24 (400 / 600) | Thân bài · bullet · caption · tab nav · nút 48 · ô nhập |
| web-caption / label | 14/20 (400 / 600) | Dòng danh sách · task · thẻ · header + số trong bảng (cả mobile) · nút nhỏ 40 · nhãn form · tab nav mobile |

Tiêu đề màn dài (VI Valuation) trên màn hẹp: `fitIntroTitles()` lùi **theo thang** 24/32 → 20/28 → 18/28 → 16/24 → 14/20 tới khi vừa 2 dòng — không bao giờ ra cỡ lẻ, không cắt "…".

## 3. Thành phần

| Thành phần | Spec |
|---|---|
| **Navbar** | cao 64 (mobile 56) · trắng mờ blur · kẻ dưới `--line` · logo mèo 32 (mobile 24, giữ nguyên hình, không bo thêm) + tên site 20/600 · tab 16/600 cách 32 (mobile 14, cách 16), đang chọn chữ đen + vạch vàng 4px rộng bằng chữ |
| **Box nổi** | trắng · **radius 16** · `--shadow` (không viền) · hover nhích 2px. Áp cho: card Work · box Valuation · bảng altcoin · ảnh Highlights · popup |
| **Header card** | cao 48 · nền `--amber-soft` · icon + tiêu đề web-h4 canh TRÁI · đệm 16 |
| **Header card Work** | luôn 2 hàng, đệm 8/16. Hàng 1: logo 24 + tên 20 canh TRÁI · icon X + Discord (nút tròn 32, icon 20, cách 8, ẩn nếu chưa có link) canh PHẢI · ⋮ admin. Hàng 2: dãy **thẻ** viên trắng cao 24 đệm 8 chữ 14/600, icon cách chữ 8 — potential · narrative · `rank: S`, cách mép card 16 thẳng mép logo. Chữ thẻ viết thường hết, chỉ "AI" + chữ rank viết hoa (`tagCase()`, chỉ đổi lúc hiện), tự xuống dòng, không cắt chữ |
| **Dòng danh sách** (box Valuation · task Work · danh sách admin) | nền `--mist` · **cao tối thiểu 56** · radius 16 · đệm ngang 16 · chữ 14 · cách nhau 8. Box Valuation: **nhãn TRÁI, giá trị PHẢI** (`.list-row`): nhãn grey (hoặc dòng chính ink 600 + dòng phụ grey — vd `STABLE` / `TGE 08/12/25`, `layer-1` / `12 dự án`), giá trị ink 600. Không viết tắt kiểu `SL:02`, không dấu `:` sau nhãn |
| **Dòng bấm được** (task Work) | như dòng danh sách; hover nền `--amber-soft` + ô mũi tên tròn 32 nền đen. Trong dải Daily nền dòng là trắng |
| **Nhãn nhóm** (Work) | cao 32 · icon 16 đen + chữ 14/600 grey + kẻ mảnh kéo hết ngang |
| **Tiêu đề mục** (CV) | icon 24 + chữ 24 + kẻ mảnh kéo hết ngang |
| **Nút chính** | cao 48 đệm 24 · radius 16 · nền đen chữ trắng 16/600 · shadow. **Nút đứng một mình trên mobile rộng cố định 296** (vd "Dự đoán FDV TGE") |
| **Nút phụ** | như nút chính nhưng trắng chữ đen · shadow · hover nền `--amber-soft` (Twitter/Telegram/Email cao 48; Admin = nút nhỏ cao 40 đệm 16 chữ 14) |
| **Nút icon** | 40×40 radius 16, icon 20 (camera, [+]) |
| **Toggle VI/EN · thanh lọc rank** | máng `--mist` radius pill, **không đệm/khe trong** — viên chiếm trọn máng: toggle cao 40 (viên 40), thanh lọc cao 48 (viên 48) · viên đang chọn đen chữ trắng |
| **Ô nhập** | cao 48 đệm 16 · nền `--mist` · viền `--line` 1px · radius 16 · khi chọn viền 2px đen |
| **Thẻ / badge** | cao 24 · đệm ngang 8 · radius pill (×ATM nguy hiểm, FAKE PUMP, thẻ Work) |
| **Icon** | **Lucide 1.59.0** (ISC), nét 2, cỡ 16/20/24, tô `currentColor`. SVG inline (`WTE_ICON` + `wteIcon()` trong JS); riêng camera/plus là file SVG dùng CSS mask ở `::before`. Icon thương hiệu X/Discord lấy từ Tabler (Lucide không có) |

**Luật bo góc** (design system gốc): **16** cho mọi box, dòng, ô nhập và nút · **pill** cho thẻ, badge, toggle, hình tròn. Không dùng radius nào khác.

## 4. Lưới

Mọi khoảng cách là **bội số của 8** — không có khe/đệm 2, 4, 6, 12. Lưới web 1440: **lề 120 · 12 cột · rãnh 24 · nội dung 1200** (code: `--content 1200` + lề tối thiểu `--gutter 48`, nên ở 1440 tự ra 120). Mobile ≤ 640: lề 16.

- **Navbar → nội dung: 16** ở mọi tab, desktop lẫn mobile.
- **Dọc CV:** mục cách nhau 48 (mobile 32) · tiêu đề mục → nội dung 16 · hero: tên → châm ngôn 24 → nút 24 · timeline item cách 32.
- **Dọc Valuation/Work:** hàng tiêu đề → nội dung 16 · bảng → 3 box 24 · nhóm rank cách 48 (mobile 32).
- **Trong box:** **đệm 16** mọi box/card/popup (desktop lẫn mobile) · header 48 → đệm 16 → dòng 56 → khe 8 → … → đệm đáy 16.

| Chỗ | Chia |
|---|---|
| Valuation — 3 box | 3 × 384 (4 cột lưới), rãnh 24, box cao 328 = header 48 + 16 + thân 248 + 16. Thân: Vùng nguy hiểm/Narrative = 4 dòng 56 + 3 khe 8 (thiếu thì `padRows()` đệm dòng trống, thừa thì cuộn); Hệ số TGE = 3 dòng + nút 48 cách 16 |
| Valuation — bảng | 7 cột theo % (cột mép 13.855%, 5 cột giữa 14.458%), header 48, dòng 40, cao tối đa 432. **Mobile:** ẩn Narrative · TGE · ×ATL, còn 4 cột 22 / 20 / 36 / 22 % (×ATH dạng "đáy → đỉnh" cần rộng nhất), chữ vẫn 14 |
| Work | card cùng rank 2 × 588 (6 cột lưới), rãnh 24; khác rank cách 48 (mobile 32) |
| CV — Highlights | 3 × 384, rãnh 24, ảnh 3:2 |
| CV — timeline | 3 cột `128 / 64 / nội dung`, chấm vàng 16 canh giữa dòng đầu (flex, không số lệch), item cách 32; bullet rộng tối đa 680 |

Màn ≤ 1024: 3 cột → 2. Màn ≤ 640: mọi lưới → 1 cột.
