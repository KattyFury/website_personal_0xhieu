# Luật thiết kế — 0xhieu.xyz

> Chốt 2026-10-24. Site theo **design system nguyen0xhieu** (Figma `hieu` `IPyKVg7ylGw1mjMRyYVrL7` · bản đọc nhanh: Design System artifact), với 1 biến thể riêng cho site này:
> **ĐEN thay vai trò 0x Blue** (iconic là mèo đen) · **nền TRẮNG** (mắt kính trắng của mèo) · **VÀNG MẮT MÈO** cho chi tiết thiết kế.
> Code ở khối `<style>` duy nhất trong `index.html`, viết theo thành phần, cùng thứ tự các mục dưới đây. Mọi luật ở design system gốc mà file này không nhắc → làm theo gốc.

---

## 1. Màu

| Token | Mã | Dùng cho |
|---|---|---|
| `--ground` | `#FFFFFF` | Nền trang |
| `--ink` | `#000000` | Màu chủ đạo: chữ chính · icon · **nút chính** (nền đen chữ trắng) · toggle đang chọn · viền focus 2px |
| `--grey` | `#4D4D4D` | Chữ phụ (mô tả, bullet, nhãn) — 8.4:1 |
| `--muted` | `#8C8C8C` | Meta, placeholder, ngày, chữ tắt. **Không** dùng cho chữ cần đọc để làm theo |
| `--mist` | `#F2F2F2` | Box phẳng · dòng chip chỉ-đọc · ô nhập · hover dòng bảng |
| `--line` | `#E0E0E0` | Kẻ mảnh · viền ô nhập · **nền nút tắt** |
| `--amber` | `#FFA111` | **Vàng mắt mèo** (lấy đúng từ `icon.png`): khối, chấm, vạch. **Chữ trên nền vàng luôn đen** (10.4:1), không bao giờ trắng |
| `--amber-text` | `#9C6200` | Vàng **sẫm** cùng hue, cho CHỮ vàng trên trắng (5.0:1) và trên `--amber-soft` (4.5:1) |
| `--amber-soft` | `#FFF1DB` | Nền nhạt vàng: header card · header bảng · ô kết quả · hover nút phụ |

- Chỉ 3 cấp chữ: `ink` · `grey` · `muted`. Không thêm cấp xám thứ 4.
- Tắt (disabled): nền `--line`, chữ `--muted`, bỏ shadow. **Không giảm opacity.**
- Không gradient (solid là mặc định của design system; nếu sau này thêm thì tối đa 1 vùng/màn).

**Vàng mắt mèo xuất hiện ở đâu** (chỉ chỗ mang nghĩa hoặc nhận diện, không rải trang trí):
- Vạch dưới tab nav đang chọn · vòng quanh ảnh đại diện · chấm timeline · chấm "Available for" · gạch chân khi hover tiêu đề box.
- Nền `--amber-soft`: header card Valuation, header bảng altcoin, header + dải Daily của card rank `$`.
- Chữ `--amber-text`: link trong timeline · hover tên site / tab nav / nút chữ · ×TGE ≥ 13 · ×ATH ca list sàn tạo ATH tuần đầu · số trong box Hệ số TGE · ×ATM trong Vùng nguy hiểm · narrative hot.
- Viên `--amber` chữ đen: ×ATM ≥ 15 trong bảng · badge FAKE PUMP · rank `$`.
- Chấm `--amber` 8px cạnh ticker có vcFDV ≥ $300M.

**Màu rank** (Work — bộ màu đi kèm của design system; ngoại lệ có chủ đích với luật "≤ 2 màu đi kèm/màn" vì rank là data):

| Rank | Badge | Nền header + Daily |
|---|---|---|
| `$` | `--amber`, chữ **đen** | `--amber-soft` |
| `S` | purple `#7B4DF2`, chữ trắng | purple-soft `#EFE9FE` |
| `A` | cyan-text `#087089`, chữ trắng | cyan-soft `#E0F5FA` |
| `B` | green-text `#0B7A45`, chữ trắng | green-soft `#E3F5EC` |
| `C` | `--grey`, chữ trắng | `--mist` |

## 2. Chữ

Font hệ thống Apple (`-apple-system, BlinkMacSystemFont, 'SF Pro Text', system-ui…`), máy khác tự lùi. Không webfont ngoài. Cỡ **số chẵn, tối thiểu 14**. Letter-spacing theo bảng Inter: 14 −.006em · 16 −.011em · 18 −.014em · 20 −.017em · 24 −.019em · 32+ −.022em. Không VIẾT HOA giãn chữ nữa.

| Style | Cỡ / dòng / đậm | Dùng cho |
|---|---|---|
| web-h2 | 40/48 700 (mobile 32/40) | Tên người ở hero — duy nhất |
| web-h3 | 24/32 600 (mobile 20/28) | Tiêu đề màn · tiêu đề mục CV · châm ngôn hero |
| web-h4 | 20/28 600 (mobile 18) | Tiêu đề card/box · vai trò timeline · tên site · tiêu đề popup |
| web-lead | 18/28 | Câu niềm tin ở hero |
| web-body / nav-button | 16/24 (400 / 600) | Thân bài · bullet · caption · tab nav · nút 48 · ô nhập |
| web-caption / label | 14/20 (400 / 600) | Dòng chip · task · badge · header + số trong bảng · nút nhỏ 40 · nhãn form |

**Ngoại lệ duy nhất dưới 14:** bảng altcoin trên mobile (≤ 640) = 12 — 5 cột số trên 361px, 14 thì ×ATH đè ×ATL.

## 3. Thành phần

| Thành phần | Spec |
|---|---|
| **Navbar** | cao 64 (mobile 56) · trắng mờ blur · kẻ dưới `--line` · logo mèo 32 + tên site 20 · tab 16/600 cách 32, đang chọn chữ đen + vạch vàng 4px rộng bằng chữ |
| **Box nổi** | trắng · **radius 16** · `--shadow` (không viền) · hover nhích 2px. Áp cho: card Work · box Valuation · bảng altcoin · ảnh Highlights · popup |
| **Header card** | cao 48 · nền `--amber-soft` (Work: theo màu rank) · icon + tiêu đề web-h4 canh TRÁI · đệm trái 24 |
| **Dòng chỉ-đọc** (box Valuation) | viên `--mist` cao 40, radius pill, chữ 14, đệm ngang 16, cách nhau 8 |
| **Dòng bấm được** (task Work) | như dòng chỉ-đọc; hover nền `--amber-soft` + ô mũi tên tròn nền đen. Trong dải Daily nền dòng là trắng |
| **Nhãn nhóm** (Work) | cao 32 · icon 16 đen + chữ 14/600 grey + kẻ mảnh kéo hết ngang |
| **Tiêu đề mục** (CV) | icon 24 + chữ 24 + kẻ mảnh kéo hết ngang |
| **Nút chính** | cao 48 đệm 24 (popup) / nút nhỏ cao 40 đệm 16 (trong box) · radius 16 · nền đen chữ trắng · shadow |
| **Nút phụ** | như nút chính nhưng trắng chữ đen · shadow · hover nền `--amber-soft` (Twitter/Telegram/Email cao 48, Admin cao 40, Huỷ, Xoá) |
| **Nút icon** | 40×40 radius 16, icon 20 (camera, [+]) |
| **Toggle VI/EN · thanh lọc rank** | máng `--mist` radius pill cao 40 (thanh lọc 48) · viên đang chọn đen chữ trắng (thanh lọc: màu rank) |
| **Ô nhập** | cao 48 đệm 16 · nền `--mist` · viền `--line` 1px · radius 16 · khi chọn viền 2px đen |
| **Icon** | **Lucide 1.59.0** (ISC), nét 2, cỡ 16/20/24, tô `currentColor`. SVG inline (`WTE_ICON` + `wteIcon()` trong JS); riêng camera/plus là file SVG dùng CSS mask ở `::before` |

**Luật bo góc** (design system gốc): **16** cho mọi box, ô nhập và nút · **pill** cho chip, dòng, toggle, badge, hình tròn. Không còn radius 8/24.

## 4. Lưới

Mọi khoảng cách là **bội số của 8**. Lưới web 1440: **lề 120 · 12 cột · rãnh 24 · nội dung 1200** (code: `--content 1200` + lề tối thiểu `--gutter 48`, nên ở 1440 tự ra 120). Mobile ≤ 640: lề 16.

- **Dọc CV:** hero đệm trên 48 (mobile 24) · mục cách nhau 96 (mobile 48) · tiêu đề mục → nội dung 32 (mobile 24).
- **Dọc Valuation/Work:** navbar → hàng tiêu đề 32 (mobile 16) → nội dung 24 (mobile 16).
- **Trong card:** header 48 → đệm 16 → dòng 40 → khe 8 → … → đệm đáy 16–24. Đệm ngang 24 (mobile 16).

| Chỗ | Chia |
|---|---|
| Valuation — 3 box | 3 × 384 (4 cột lưới), rãnh 24, box cao 216 |
| Valuation — bảng | 7 cột theo % (cột mép 13.855%, 5 cột giữa 14.458%), header 48, dòng 40, cao tối đa 432 |
| Work | card cùng rank 2 × 588 (6 cột lưới), rãnh 24; khác rank cách 64 (mobile 32) |
| CV — Highlights | 3 × 384, rãnh 24, ảnh 3:2 |
| CV — timeline | 3 cột `128 / 64 / nội dung`, chấm vàng 16px ở tâm rãnh, item cách 48; bullet rộng tối đa 680 |

Màn ≤ 1024: 3 cột → 2, header card Work xuống 2 hàng (tên/rank hàng 1 · headline hàng 2). Màn ≤ 640: mọi lưới → 1 cột.
