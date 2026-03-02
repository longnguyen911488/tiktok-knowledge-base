# Script Structure - Cấu Trúc Video 60 Giây

---

## 📋 THÔNG TIN FILE

**PHẠM VI**: Cấu trúc video hoàn chỉnh (0-60s) cho nội dung giáo dục/khoa học  
**BAO GỒM**: Tích hợp hook, các phase body, kỹ thuật chuyển tiếp, chiến lược mention sản phẩm  
**KHÔNG BAO GỒM**: Quy trình tạo hook (xem `Instruction.md`), các formulas cụ thể (xem `script_formulas.json`)

**MỤC ĐÍCH FILE**:  
Định nghĩa khung cấu trúc cho video giáo dục 60 giây với tính linh hoạt cho việc đưa sản phẩm vào hoặc chỉ deliver value thuần túy.

**VERSION**: 1.0  
**TẠO NGÀY**: 23/01/2026  
**CẬP NHẬT**: 23/01/2026  
**REVIEW TIẾP**: 23/03/2026

---

## ⚠️ TUYÊN BỐ VỀ TÍNH LINH HOẠT CỦA CẤU TRÚC

**QUAN TRỌNG**: Document này cung cấp **NGUYÊN TẮC CHỈ DẪN**, không phải rules cứng nhắc.

### Thứ Tự Ưu Tiên:
1. **Nếu dùng formula từ `script_formulas.json`** → Tuân theo timing của formula chính xác (đã test)
2. **Nếu tạo script mới** → Dùng structure này làm baseline (linh hoạt ±5s mỗi phase được chấp nhận)
3. **Nguyên tắc > Timing**: Trust ladder, quản lý open loop QUAN TRỌNG HƠN số giây chính xác

### Cách Tiếp Cận Dựa Trên Parameter:
Structure này hỗ trợ **HAI CHẾ ĐỘ** điều khiển bởi parameter trong prompt:

Parameter: Product_Include: [True / False]

True → Structure B (Giáo Dục + Giới Thiệu Sản Phẩm)
False → Structure A (Chỉ Giáo Dục - Pure Value)

text

**Khi nào dùng chế độ nào**:
- **False (Chỉ Giáo Dục)**: Giai đoạn xây trust, audience mới, khám phá topic, nội dung awareness
- **True (Có Sản Phẩm)**: Giai đoạn conversion, audience ấm, nội dung solution-focused, launch sản phẩm

---

## PHẦN 1: NỀN TẢNG LÝ THUYẾT

### 1.1. Đường Cong Retention 60 Giây (Retention Curve)

**Khái niệm**: Retention trên TikTok theo patterns drop có thể dự đoán. Hiểu đường cong này giúp bạn thiết kế content duy trì attention.

Retention (%)
100% |●
| ●
70% | ●
| ●___
50% | ●●●
| ●●●___
30% | ●●●___
| ●●●
0% |__________________________
0s 10s 20s 30s 40s 50s 60s

Điểm Drop Chính:
├─ 0-3s: Drop dốc nhất (Hook critical) - Mất 30-50% viewers
├─ 10-15s: Drop thứ hai (Transition phải satisfy curiosity) - Mất 10-15%
├─ 15-45s: Vùng plateau (Value delivery duy trì) - Giảm dần 5-10%
├─ 45-55s: Decision point (Product hoặc CTA) - Có thể tăng hoặc drop tùy execution
└─ 55-60s: Window cuối (Action trigger) - 5-10% cuối hoàn thành

text

**Ý Nghĩa Chiến Lược**:
- **0-10s**: Ngăn hemorrhaging bằng hook mạnh (xem `Instruction.md`)
- **10-15s**: Deliver "aha" moment đầu tiên để satisfy curiosity gap
- **15-45s**: Value delivery theo chunks (tối đa 3 concepts)
- **45-55s**: Conversion window (product) HOẶC commitment ask (follow/save)
- **55-60s**: Củng cố action bằng catchphrase + CTA rõ ràng

**Nguồn**: TikTok Creator Analytics, YouTube retention best practices

---

### 1.2. Hệ Thống Quản Lý Open Loop

**Khái niệm**: Hook mở loops → Body dần dần đóng loops → Outro confirm closure + mở future loop

#### Vòng Đời Của Loop:

MACRO LOOP (Toàn Bộ Video):
Câu Hỏi Hook → Câu Trả Lời Body → Xác Nhận Outro

MICRO LOOPS (Trong Mỗi Phase):
Phase 2: Trả lời một phần (WHY) → Tiếp tục xem
Phase 3: Trả lời sâu (HOW) → Tiếp tục xem
Phase 4: Ứng dụng (WHAT to do) → Hài lòng
Phase 5: Bước tiếp theo → Future engagement

text

#### Ví Dụ Flow:

**Hook (0-10s)**:  
"78% nam giới sau 30 testosterone giảm. Không phải tuổi, không phải stress. Vậy tại sao?"

**[MACRO LOOP MỞ]**: "Tại sao testosterone giảm?"  
**[MICRO LOOP 1]**: "Không phải tuổi/stress thì là gì?"

---

**Transition (10-15s)**:  
"Nguyên nhân thật sự là thiếu kẽm - khoáng chất cơ thể không tự sản xuất."

**[MICRO LOOP 1 ĐÓNG]**: Nguyên nhân = thiếu kẽm  
**[MICRO LOOP 2 MỞ]**: "Tại sao kẽm lại quan trọng đến vậy?"

---

**Body Part 1 (15-25s)**:  
"Kẽm kích hoạt 300+ enzyme trong cơ thể, bao gồm enzyme sản xuất testosterone. Không có kẽm = không có testosterone."

**[MICRO LOOP 2 ĐÓNG]**: Hiểu vai trò kẽm  
**[MICRO LOOP 3 MỞ]**: "Làm sao biết mình thiếu kẽm?"

---

**Body Part 2 (25-35s)**:  
"Dấu hiệu thiếu kẽm: Da xấu, miễn dịch yếu, vết thương lâu lành, và đặc biệt - testosterone thấp."

**[MICRO LOOP 3 ĐÓNG]**: Biết cách nhận diện  
**[MICRO LOOP 4 MỞ]**: "Vậy giải pháp là gì?"

---

**Body Part 3 (35-45s)**:  
"Cơ thể cần 11-15mg kẽm/ngày. Nguồn tốt nhất: Thịt đỏ, hải sản, hạt bí. Hoặc supplement kẽm hữu cơ để hấp thu tối ưu."

**[MICRO LOOP 4 ĐÓNG]**: Biết giải pháp tổng quát

**[ĐIỂM QUYẾT ĐỊNH - HAI ĐƯỜNG ĐI]**:

---

#### **ĐƯỜNG A: Product_Include = False**

**Body Part 4 (45-55s)**:  
"Lưu ý: Kẽm vô cơ (oxide) hấp thu kém (<10%). Chọn kẽm hữu cơ (picolinate, gluconate) với hấp thu >40%. Uống cùng vitamin C tăng hấp thu thêm 30%."

**[EDUCATIONAL DEPTH]**: Thêm value, không mention product

**Outro (55-60s)**:  
"Nhớ lấy, làm đàn ông, khó nhất là giữ được mình. Follow để học thêm về testosterone tự nhiên."

**[MACRO LOOP ĐÓNG]**: Đã trả lời đầy đủ  
**[FUTURE LOOP MỞ]**: "Video tiếp theo về testosterone"

---

#### **ĐƯỜNG B: Product_Include = True**

**Product Introduction (45-55s)**:  
"Có 1 sản phẩm tôi recommend: [Product Name] - kẽm picolinate 15mg + vitamin C. Hấp thu gấp 4 lần kẽm thường. Link mô tả bên dưới."

**[MICRO LOOP 5 MỞ]**: "Sản phẩm này khác gì?"  
**[MICRO LOOP 5 ĐÓNG]**: Giải thích USP ngắn gọn

**Outro (55-60s)**:  
"Nhớ lấy, làm đàn ông, khó nhất là giữ được mình. Check link để tìm hiểu thêm."

**[MACRO LOOP ĐÓNG]**: Có solution cụ thể  
**[CTA]**: Click link (conversion-focused)

---

**Nguyên Tắc Chính**: Mỗi phase phải đóng 1 loop và mở 1 loop mới để sustain attention.

**Nguồn**: Zeigarnik Effect, storytelling psychology

---

### 1.3. Information Chunking Để Giữ Retention

**Khái niệm**: Não bộ xử lý thông tin theo chunks (tối đa 7±2 items mỗi chunk). Video phải chia info phức tạp thành segments dễ tiêu hóa.

#### Chiến Lược Chunking Cho Body 30s (15-45s):

❌ TỆ (Quá tải):
"Kẽm kích hoạt enzyme, tăng testosterone, tăng cơ, giảm mỡ, tăng miễn dịch, cải thiện da, tăng sinh lý, giảm stress, tăng tập trung, cải thiện giấc ngủ..."

✅ TỐT (3 Chunks):

CHUNK 1 (15-25s): Cơ Chế Cốt Lõi
"Kẽm kích hoạt 300 enzyme, đặc biệt enzyme sản xuất testosterone."
[1 concept chính + 1 ví dụ cụ thể]

CHUNK 2 (25-35s): Nhận Diện
"Dấu hiệu thiếu: Da xấu, miễn dịch yếu, testosterone thấp."
[1 concept chính + 3 triệu chứng]

CHUNK 3 (35-45s): Loại Giải Pháp
"Cần 11-15mg/ngày. Nguồn: Thịt, hải sản, hạt, hoặc supplement hữu cơ."
[1 concept chính + 3 nguồn + 1 qualifier]

text

**Công Thức**:
- **Mỗi chunk 10s** = 1 key concept + 2-3 supporting details
- **Tối đa 3 chunks** trong body (15-45s)
- **Visual aid** recommended cho mỗi chunk (text overlay, B-roll)

**Tại Sao Hiệu Quả**:
- Ngăn cognitive overload
- Tăng comprehension
- Message retention tốt hơn
- Dễ nhớ key points

**Nguồn**: Cognitive Load Theory (George Miller, 1956)

---

### 1.4. Thang Tin Cậy (Trust Ladder)

**Khái niệm**: Trust xây dựng theo stages. Bỏ qua stages = phá trust = drop-off.

TRUST LEVEL 5: Hành Động (45-60s)
↑ (Product reveal HOẶC commitment ask)
|
TRUST LEVEL 4: Chấp Nhận Authority (35-45s)
↑ (Evidence, proof, thể hiện chuyên môn)
|
TRUST LEVEL 3: Hiểu Sâu (25-35s)
↑ (Giải thích sâu, "Aha!" moment)
|
TRUST LEVEL 2: Curiosity Được Thỏa Mãn (10-25s)
↑ (Trả lời "why", reveal cơ chế)
|
TRUST LEVEL 1: Attention Được Bắt (0-10s)
↑ (Hook - pattern interrupt)

text

#### Quy Tắc Áp Dụng:

**✅ ĐƯỢC PHÉP**:
- Giới thiệu product ở Level 5 (45-55s) sau khi trust đã xây
- Yêu cầu follow/save ở Level 4-5 (35-60s)
- Mention brand authority ở Level 3-4 (25-45s)

**❌ KHÔNG ĐƯỢC**:
- Product name ở Level 1-2 (0-25s) = Bán hàng sớm = Phá trust
- Yêu cầu mua trước khi giải thích solution = Pushy = Drop
- Bỏ qua giải thích cơ chế (Level 2) và nhảy thẳng product = Confused

**Tại Sao Product Ở 45-55s**:
- Viewer đã hiểu problem (Level 2)
- Viewer đã hiểu solution category (Level 3)
- Viewer đã thấy evidence (Level 4)
- GIỜ mới sẵn sàng chấp nhận product cụ thể (Level 5)

**Chiến Lược Educational-Only** (Product_Include = False):
- Dừng ở Level 4 (evidence/authority)
- CTA = Soft commitment (follow, save, comment)
- Xây trust cho conversion TƯƠNG LAI (video sau, vào profile)

**Nguồn**: Marketing psychology, buyer journey theory, AIDA model adaptation

---

### 1.5. Duy Trì Dopamine (Sau Hook)

**Khái niệm**: Hook trigger dopamine ban đầu. Body phải DUY TRÌ dopamine để ngăn drop.

#### Dopamine Triggers Trong Body (15-45s):

**1. Pattern Variation (Mỗi 10s)**:
- Đổi visual (cut sang góc khác/B-roll)
- Đổi audio (thay đổi tone, music layer)
- Đổi text overlay style
- **Mục tiêu**: Ngăn habituation

**2. Micro-Rewards (Mỗi 10-15s)**:
- Deliver 1 actionable insight mỗi chunk
- "Aha!" moments (reveal surprising fact)
- Progressive disclosure (tease chunk tiếp theo)
- **Mục tiêu**: Dopamine hits nhỏ liên tục

**3. Xây Dựng Anticipation**:
- "Và đây là phần quan trọng nhất..." (35s mark)
- "Có 1 điều ít người biết..." (25s mark)
- "Tôi sẽ chỉ bạn cách..." (40s mark)
- **Mục tiêu**: Forward momentum

**4. Social Proof (Optional, 30-40s)**:
- "Hàng nghìn người đã..." (nếu applicable)
- "Nghiên cứu cho thấy..." (evidence-based)
- **Mục tiêu**: Authority reinforcement

**Khác Biệt Với Hook Dopamine**:
- **Hook**: Shock value, curiosity gap (HIGH intensity)
- **Body**: Consistent value delivery, progressive satisfaction (SUSTAINED intensity)

**Tham khảo**: Xem `hook_principle.md` cho lý thuyết dopamine sâu. Phần này focus vào DUY TRÌ sau hook.

---

## PHẦN 2: HAI KHUNG CẤU TRÚC

### Tổng Quan: Hai Đường Đi

Hệ thống cấu trúc này hỗ trợ **LINH HOẠT** dựa trên mục tiêu content:

| Mode | Khi Nào Dùng | Mục Tiêu | Mention Sản Phẩm |
|------|-------------|----------|------------------|
| **Structure A** | Xây trust, audience mới, awareness phase | Giáo dục → Conversion tương lai | ❌ KHÔNG |
| **Structure B** | Conversion phase, audience ấm, launch SP | Giáo dục → Conversion ngay | ✅ CÓ |

**Điều khiển qua parameter trong prompt**:
Product_Include: False → Structure A
Product_Include: True → Structure B

text

---

## STRUCTURE A: Chỉ Giáo Dục (Product_Include = False)

**Use Case**: Pure value delivery, xây trust, awareness content

**Tổng Thời Lượng**: 60s  
**Revenue Model**: Gián tiếp (xây following → convert sau qua profile/video tương lai)

---

### Phase 1: Hook (0-10s)

**Mục đích**: Stop scroll, tạo curiosity gap

**Loại Content**:
- Problem awareness
- Thống kê gây shock
- Câu hỏi không có đáp án
- Contradiction với niềm tin phổ biến

**Tâm Lý**:
- Dopamine: Curiosity gap, pattern interrupt
- Trust: Level 1 (Attention captured)
- Loop: MỞ (câu hỏi macro)

**Cấu Trúc** (Xem `Instruction.md` cho chi tiết):
- 0-3s: Attention grabber (visual/audio shock)
- 3-7s: Problem statement / Câu hỏi
- 7-10s: Value promise / Tease mechanism

**Ví Dụ**:
"78% nam giới sau 30 testosterone giảm nhanh. Không phải tuổi. Không phải stress. Vậy nguyên nhân thật sự là gì?"

**Chuyển sang Phase 2**: Giây 8-10 phải tease WHY để pull viewer vào transition

**Lỗi Thường Gặp**:
- ❌ Trả lời câu hỏi trong hook (đóng loop quá sớm)
- ❌ Mention product name (premature)
- ❌ Quá mơ hồ ("Tôi sẽ nói về health..." - không specific)

---

### Phase 2: Transition - Reveal Cơ Chế (10-15s)

**Mục đích**: Thỏa mãn curiosity gap, giải thích TẠI SAO problem tồn tại

**Loại Content**:
- Scientific mechanism (đơn giản hóa)
- Reveal nguyên nhân gốc
- Delivery "Aha!" moment

**Tâm Lý**:
- Dopamine: Reward prediction (câu hỏi được trả lời)
- Trust: Level 2 (Curiosity satisfied → Trust tăng)
- Loop: MICRO LOOP 1 đóng, MICRO LOOP 2 mở

**Cấu Trúc**:
- 10-12s: Trả lời core "why" question từ hook
- 12-14s: Giải thích mechanism ngắn (1 câu)
- 14-15s: Tease "ý nghĩa với bạn" (pull vào body)

**Ví Dụ**:
"Nguyên nhân là thiếu kẽm. Kẽm là cofactor cho enzyme sản xuất testosterone. Không có kẽm = cơ thể không thể tạo testosterone dù còn trẻ."

**Nguyên Tắc Chính**: Đừng over-explain ở đây. Giữ depth cho body. Đây chỉ là "unlock" moment.

**Chuyển sang Phase 3**: "Vậy tại sao kẽm lại quan trọng đến vậy?" (implied, không nói ra)

**Lỗi Thường Gặp**:
- ❌ Quá kỹ thuật (mất audience)
- ❌ Quá nông (không có "aha" moment)
- ❌ Bỏ qua mechanism (nhảy thẳng solution = confusion)

---

### Phase 3: Body - Giáo Dục Sâu (15-45s)

**Mục đích**: Deliver value theo chunks, xây authority, sustain attention

**Tổng Thời Lượng**: 30s  
**Cấu Trúc**: 3 chunks × 10s mỗi cái

**Tâm Lý**:
- Dopamine: Micro-rewards mỗi 10s (insight mới)
- Trust: Level 2 → Level 3 → Level 4 (xây dần)
- Loop: Nhiều micro loops mở và đóng

---

#### Chunk 1: Deep Dive Cơ Chế (15-25s)

**Mục đích**: Giải thích cơ chế hoạt động CHI TIẾT

**Nội dung**:
- Mở rộng mechanism từ transition
- Thêm 2-3 supporting facts
- Dùng metaphor/analogy nếu phức tạp

**Ví Dụ**:
"Kẽm kích hoạt hơn 300 enzyme trong cơ thể. Đặc biệt, enzyme 5-alpha-reductase cần kẽm để convert testosterone. Thiếu kẽm = enzyme này không hoạt động = testosterone không được sản xuất. Đơn giản như vậy."

**Dopamine Trigger**: Pattern variation (cut B-roll, thêm text overlay "300 enzyme")

**Trust Level**: 2 → 3 (Viewer nghĩ: "À, tôi hiểu khoa học rồi")

---

#### Chunk 2: Nhận Diện & Liên Quan (25-35s)

**Mục đích**: Giúp viewer identify problem ở chính họ

**Nội dung**:
- Symptoms/dấu hiệu của problem
- Liên hệ với trải nghiệm của audience
- Làm cho nó personal

**Ví Dụ**:
"Làm sao biết bạn thiếu kẽm? Dấu hiệu: Da xấu, mụn nhiều, vết thương lâu lành, miễn dịch yếu ốm liên tục, và quan trọng nhất - testosterone thấp, ham muốn giảm, cơ bắp mất đi."

**Dopamine Trigger**: Self-recognition (viewer check mental boxes: "Tôi có dấu hiệu này!")

**Trust Level**: 3 → 4 (Viewer nghĩ: "Đây là về TÔI, không phải info chung chung")

**Visual Direction**: Quick cuts về symptoms (chậm chạp, mệt mỏi, etc.)

---

#### Chunk 3: Loại Giải Pháp (35-45s)

**Mục đích**: Giới thiệu solution KHÔNG specific product (chỉ giáo dục)

**Nội dung**:
- Solution category tổng quát
- Nguồn/methods có sẵn
- Lời khuyên thực tế (actionable)

**Ví Dụ**:
"Cơ thể cần 11-15mg kẽm mỗi ngày. Nguồn tốt nhất: 100g thịt bò = 7mg, 6 con hàu = 32mg, 30g hạt bí = 3mg. Hoặc supplement kẽm hữu cơ - chọn loại picolinate hoặc gluconate, hấp thu tốt hơn kẽm oxide gấp 4 lần."

**Dopamine Trigger**: Actionable knowledge (viewer có thể apply ngay)

**Trust Level**: 4 (Authority established - Professor biết chi tiết cụ thể)

**Nguyên Tắc Chính**: Mention LOẠI SOLUTION (vd: "kẽm hữu cơ supplement"), KHÔNG specific brand/product.

---

**Chuyển sang Phase 4**: Flow tự nhiên vào tip sâu hơn hoặc outro

**Lỗi Thường Gặp Cho Toàn Body**:
- ❌ Cả 3 chunks về cùng 1 khía cạnh (boring, repetitive)
- ❌ Không có visual variety (đơn điệu)
- ❌ Information overload (>3 concepts)
- ❌ Quên make it personal (quá academic)

---

### Phase 4: Advanced Insight / Pro Tip (45-55s)

**Mục đích**: Over-deliver value, cho bonus insight (vì không có product pitch)

**Loại Content**:
- Advanced tip ("Điều ít người biết...")
- Optimization strategy
- Những lỗi thường gặp cần tránh
- So sánh (cách tốt vs cách xấu)

**Tâm Lý**:
- Dopamine: Bonus reward (value bất ngờ)
- Trust: Level 4 solidified (Viewer nghĩ: "Người này giỏi thật")
- Loop: Micro loop về "cách optimize"

**Ví Dụ**:
"Mẹo: Uống kẽm cùng vitamin C tăng hấp thu 30%. Tránh uống cùng canxi hoặc sắt - chúng cạnh tranh hấp thu. Uống tối sau bữa tối 2 giờ để tối ưu."

**Nội Dung Thay Thế**:
- "3 sai lầm phổ biến khi bổ sung kẽm..."
- "Kẽm oxide vs kẽm picolinate: Sự khác biệt quan trọng..."
- "Làm sao test mức kẽm trong cơ thể..."

**Chuyển sang Phase 5**: Lead tự nhiên vào CTA

**Lỗi Thường Gặp**:
- ❌ Contradict info trước (consistency critical)
- ❌ Quá phức tạp (mất momentum ở đoạn cuối)
- ❌ Đột ngột pitch product (phá lời hứa educational-only)

---

### Phase 5: Outro - Soft CTA (55-60s)

**Mục đích**: Đóng macro loop, khuyến khích soft commitment (follow/save/comment)

**Loại Content**:
- Summary statement (optional, 1 câu)
- Catchphrase Professor Simon (BẮT BUỘC)
- Soft CTA (follow để xem thêm, save để xem lại, comment trải nghiệm)

**Tâm Lý**:
- Dopamine: Closure satisfaction (câu hỏi đã trả lời)
- Trust: Level 4 maintained
- Loop: MACRO LOOP đóng, FUTURE LOOP mở (tease video tiếp)

**Cấu Trúc**:
- 55-57s: Optional summary HOẶC transition phrase
- 57-59s: Delivery catchphrase (chậm, deliberate)
- 59-60s: CTA (verbal + text overlay)

**Ví Dụ**:
"Đó là lý do khoa học đằng sau testosterone và kẽm. [Pause] Nhớ lấy, làm đàn ông, khó nhất là giữ được mình. [Pause] Follow để học thêm về tối ưu hormone tự nhiên."

**CTAs Thay Thế** (Educational-Only mode):
- "Save video này để xem lại khi cần"
- "Comment bên dưới: Bạn có dấu hiệu nào?"
- "Follow, video tiếp theo tôi sẽ nói về [related topic]"
- "Link profile có series đầy đủ về testosterone"

**Tham Khảo Catchphrase**: Xem `persona.md` cho các catchphrase signature của Professor Simon

**Lỗi Thường Gặp**:
- ❌ Bỏ qua catchphrase (phá brand consistency)
- ❌ Nhiều CTAs (confusing - chọn MỘT)
- ❌ CTA yếu ("Like nếu bạn thích" - quá generic)

---

### Structure A: Tổng Kết Timing

0-10s: Hook (Problem + Câu hỏi)
10-15s: Transition (WHY mechanism)
15-25s: Body Chunk 1 (HOW mechanism hoạt động)
25-35s: Body Chunk 2 (Recognition - Problem CỦA BẠN)
35-45s: Body Chunk 3 (Loại solution)
45-55s: Advanced Insight (Pro tip)
55-60s: Outro (Catchphrase + Soft CTA)

Tổng: 60s
Product: KHÔNG CÓ
Conversion: Gián tiếp (follow/save/vào profile)

text

---

## STRUCTURE B: Giáo Dục + Sản Phẩm (Product_Include = True)

**Use Case**: Content conversion-focused, launch sản phẩm, audience ấm

**Tổng Thời Lượng**: 60s  
**Revenue Model**: Trực tiếp (product awareness ngay → click link → mua hàng)

**Khác Biệt Chính Với Structure A**: Phase 4 đổi từ "Advanced Insight" sang "Product Introduction"

---

### Phase 1-3: GIỐNG HỆT Structure A

**Hook (0-10s)** → Giống  
**Transition (10-15s)** → Giống  
**Body (15-45s)** → Giống (3 chunks: Mechanism → Recognition → Solution category)

**Tại Sao Giữ Giống**: Trust phải được xây qua giáo dục TRƯỚC KHI reveal product. Bỏ qua giáo dục = bán ép = drop-off.

---

### Phase 4: Product Introduction - Hero Solution (45-55s)

**Mục đích**: Giới thiệu product cụ thể như optimal solution

**Loại Content**:
- Product name reveal
- Unique selling proposition (USP)
- Brief social proof/credibility
- Soft CTA (link, xem mô tả)

**Tâm Lý**:
- Dopamine: Solution clarity (không phải tìm kiếm nữa)
- Trust: Level 4 → Level 5 (Từ kiến thức sang hành động)
- Loop: MICRO LOOP mở ("Tại sao product này cụ thể?") → MICRO LOOP đóng (USP explained)

**Cấu Trúc**:
- 45-48s: Transition phrase ("Có 1 sản phẩm tôi recommend...")
- 48-52s: Product name + USP (1-2 key benefits)
- 52-55s: Credibility/proof + nơi tìm (link)

---

#### Ví Dụ 1: Sản Phẩm Supplement

"Có 1 sản phẩm tôi recommend: **ZincMax Pro** - kẽm picolinate 15mg kết hợp vitamin C. Hấp thu gấp 4 lần kẽm thường, và đã giúp hàng nghìn anh em cải thiện testosterone tự nhiên. Link mô tả bên dưới."

**Phân Tích**:
- Transition: "Có 1 sản phẩm tôi recommend"
- Product name: "ZincMax Pro"
- USP 1: "Kẽm picolinate 15mg + vitamin C" (thành phần)
- USP 2: "Hấp thu gấp 4 lần" (lợi ích)
- Social proof: "Hàng nghìn anh em đã dùng" (credibility)
- CTA: "Link mô tả bên dưới" (nơi hành động)

---

#### Ví Dụ 2: Service/Program

"Tôi đã làm 1 chương trình: **Testosterone Reset 30 ngày** - kết hợp dinh dưỡng, supplement, và tập luyện. 87% học viên tăng testosterone 20-40% sau 1 tháng. Check link để tìm hiểu chi tiết."

---

#### Ví Dụ 3: Sản Phẩm Vật Lý (Non-supplement)

"Có 1 giải pháp tôi test 3 tháng: **Miếng Dán Ngải Cứu Bắc Kinh** - kích thích 60 huyệt đạo ở bàn chân, cải thiện tuần hoàn khí huyết, giúp ngủ sâu hơn. Dùng mỗi tối, testosterone tự nhiên tăng nhờ giấc ngủ chất lượng. Link mua bên dưới."

---

### Product Introduction: Nguyên Tắc Chính

**✅ NÊN**:
- Giới thiệu như "recommendation", không hard sell ("Có 1 sản phẩm tôi recommend...")
- Lead bằng benefit, không phải feature (Hấp thu tốt > Chứa picolinate)
- Giữ ngắn gọn (max 10s) - không phải full product demo
- Mention nơi tìm (link/mô tả)
- Light social proof nếu có (không phóng đại)

**❌ KHÔNG NÊN**:
- Tone hard sell ("Mua ngay!", "Khuyến mãi hôm nay!") - phá trust giáo dục
- Quá nhiều chi tiết product (để cho landing page)
- So sánh với đối thủ (giữ class)
- Phóng đại claims ("Chữa khỏi 100%")
- Mention giá (trừ khi đó là USP, vd: "chỉ 50k/ngày")

**Duy Trì Trust**: 
- Phrase như personal recommendation của Professor
- Focus vào problem-solution fit, không phải product features
- Maintain educational tone (inform, không persuade)

**Visual Direction**:
- Show product ngắn (2-3s)
- Text overlay: Product name + key benefit
- CTA text: "Link bên dưới" hoặc "Xem chi tiết mô tả"

---

### Phase 5: Outro - Call to Action (55-60s)

**Mục đích**: Đóng macro loop, drive action (click link)

**Loại Content**:
- Summary statement (optional)
- Catchphrase Professor Simon (BẮT BUỘC)
- Clear CTA (check link, vào profile)

**Tâm Lý**:
- Dopamine: Closure + action opportunity
- Trust: Level 5 (Sẵn sàng transaction)
- Loop: MACRO LOOP đóng, nhưng action loop mở (click link để complete)

**Cấu Trúc**:
- 55-57s: Optional transition phrase
- 57-59s: Delivery catchphrase
- 59-60s: CTA (verbal + text overlay)

**Ví Dụ**:
"Đó là cách kẽm ảnh hưởng testosterone và tại sao chọn dạng hữu cơ. [Pause] Nhớ lấy, làm đàn ông, khó nhất là giữ được mình. [Pause] Check link bên dưới để tìm hiểu thêm về sản phẩm."

**CTAs Thay Thế** (Product mode):
- "Link mua ở mô tả video"
- "Vào profile để xem thêm review"
- "Comment nếu có câu hỏi, tôi sẽ trả lời"
- "Follow để biết cách dùng hiệu quả nhất"

**Lỗi Thường Gặp**:
- ❌ Aggressive CTA ("Mua ngay đi!") - phá trust đã xây
- ❌ Bỏ catchphrase - inconsistency
- ❌ Quá nhiều CTAs (link + follow + comment + like) - decision paralysis

---

### Structure B: Tổng Kết Timing

0-10s: Hook (Problem + Câu hỏi)
10-15s: Transition (WHY mechanism)
15-25s: Body Chunk 1 (HOW mechanism hoạt động)
25-35s: Body Chunk 2 (Recognition - Problem CỦA BẠN)
35-45s: Body Chunk 3 (Loại solution - chung)
45-55s: Product Introduction (Product cụ thể như hero solution)
55-60s: Outro (Catchphrase + Clear CTA to link)

Tổng: 60s
Product: CÓ (45-55s window)
Conversion: Trực tiếp (click link → landing page → mua hàng)

text

---

## PHẦN 3: KỸ THUẬT CHUYỂN TIẾP GIỮA CÁC PHASE

### Tổng Quan

Transitions mượt mà ngăn drop-offs giữa các phases. Shifts đột ngột = viewer confused = swipe away.

**Nguyên Tắc**: Ending của mỗi phase phải SET UP beginning của phase tiếp theo.

Để deep dive về transition techniques, xem **`transition_techniques.md`** (file riêng).

---

### 3.1. Hook → Transition (10s mark)

**Thách Thức**: Thỏa mãn curiosity gap mà không trả lời đầy đủ

**Kỹ Thuật**: Partial Answer + Câu Hỏi Sâu Hơn

**Transition Tệ**:
Hook (10s): "Tại sao testosterone giảm?"
Transition (11s): "Bây giờ tôi sẽ nói về dinh dưỡng..."
[ĐỘT NGỘT - không connection]

text

**Transition Tốt**:
Hook (10s): "Tại sao testosterone giảm?"
Transition (11s): "Nguyên nhân là thiếu kẽm. Nhưng tại sao kẽm lại quan trọng đến vậy?"
[MƯỢT - trả lời rồi, mở câu hỏi mới]

text

**Công Thức**: Trả Lời Câu Hỏi Hook (1 câu) + Mở Câu Hỏi Mới (implicit hoặc explicit)

---

### 3.2. Transition → Body Chunk 1 (15s mark)

**Thách Thức**: Shift từ simple answer sang deep explanation

**Kỹ Thuật**: Bridge Statement ("Để hiểu rõ hơn...")

**Ví Dụ**:
Transition (14-15s): "...kẽm cần thiết cho enzyme testosterone."
Body (15s): "Để hiểu tại sao, hãy nhìn vào cách cơ thể sản xuất hormone này..."

text

**Bridges Thay Thế**:
- "Cơ chế hoạt động như sau..."
- "Đây là điều xảy ra trong cơ thể bạn..."
- "Khoa học giải thích rằng..."

---

### 3.3. Body Chunk 1 → Chunk 2 (25s mark)

**Thách Thức**: Shift từ mechanism sang personal relevance

**Kỹ Thuật**: "So what?" Statement

**Ví Dụ**:
Chunk 1 (24-25s): "...enzyme này cần kẽm để hoạt động."
Chunk 2 (25s): "Vậy điều này ảnh hưởng bạn thế nào? Nếu thiếu kẽm, bạn sẽ thấy những dấu hiệu sau..."

text

**Transitions Thay Thế**:
- "Bây giờ câu hỏi là: Làm sao biết bạn thiếu kẽm?"
- "Đây là lý do tại sao nhiều người không nhận ra..."
- "Áp dụng vào thực tế..."

---

### 3.4. Body Chunk 2 → Chunk 3 (35s mark)

**Thách Thức**: Shift từ problem recognition sang solution

**Kỹ Thuật**: Natural Problem-Solution Flow

**Ví Dụ**:
Chunk 2 (34-35s): "...đó là dấu hiệu cơ thể đang thiếu kẽm."
Chunk 3 (35s): "Vậy làm sao để bổ sung đủ kẽm? Cơ thể cần 11-15mg mỗi ngày..."

text

**Công Thức**: Acknowledge Problem + Ask Solution Question + Provide Answer

---

### 3.5. Body Chunk 3 → Phase 4 (45s mark)

**Hai Đường Dựa Trên Product_Include**:

#### **Đường A: Product_Include = False**

**Transition Sang Advanced Insight**:
Chunk 3 (44-45s): "...chọn kẽm hữu cơ để hấp thu tốt."
Phase 4 (45s): "Có 1 điều quan trọng ít người biết: Cách uống kẽm cũng ảnh hưởng hấp thu..."

text

**Kỹ Thuật**: "Bonus tip" framing ("Có 1 điều...", "Mẹo...", "Ít người biết...")

---

#### **Đường B: Product_Include = True**

**Transition Sang Product Introduction**:
Chunk 3 (44-45s): "...kẽm picolinate hoặc gluconate hấp thu tốt nhất."
Phase 4 (45s): "Có 1 sản phẩm tôi đã test và recommend: ZincMax Pro..."

text

**Kỹ Thuật**: Personal recommendation framing ("Tôi recommend...", "Tôi đã test...")

**Nguyên Tắc Chính**: Làm cho nó feel như natural continuation, không phải đột ngột sales pitch

---

### 3.6. Phase 4 → Outro (55s mark)

**Thách Thức**: Shift sang closure mà không feel abrupt

**Kỹ Thuật**: Summary Bridge + Catchphrase

**Ví Dụ (Product_Include = True)**:
Phase 4 (54-55s): "...link mô tả bên dưới để tìm hiểu thêm."
Outro (55s): "Đó là cách kẽm ảnh hưởng testosterone. [Pause] Nhớ lấy, làm đàn ông..."

text

**Ví Dụ (Product_Include = False)**:
Phase 4 (54-55s): "...uống tối sau bữa tối 2 giờ để tối ưu."
Outro (55s): "Đó là kiến thức khoa học về kẽm và testosterone. [Pause] Nhớ lấy, làm đàn ông..."

text

**Công Thức**: One-sentence summary (optional) + Pause + Catchphrase

---

## PHẦN 4: MA TRẬN LOẠI CONTENT

### Content Gì Thuộc Phase Nào?

| Phase | Loại Content | Ví Dụ | Không Nên Include |
|-------|-------------|--------|-------------------|
| **Hook (0-10s)** | Problem, Câu hỏi, Thống kê shock, Contradiction | "78% nam giới...", "Bạn nghĩ X? Sai rồi." | Trả lời, Solution, Product name, Giải thích dài |
| **Transition (10-15s)** | WHY mechanism, Root cause, Scientific basis | "Nguyên nhân là thiếu kẽm...", "Enzyme này cần..." | Chi tiết sâu, Nhiều concepts, Personal anecdotes |
| **Body Chunk 1 (15-25s)** | HOW mechanism, Process explanation, Scientific depth | "Kẽm kích hoạt 300 enzyme...", "Cơ chế như sau..." | Symptoms, Solutions, Product, Tangents không liên quan |
| **Body Chunk 2 (25-35s)** | Recognition, Symptoms, Personal relevance | "Dấu hiệu: Da xấu, mệt mỏi...", "Bạn có thấy..." | Lặp lại mechanism, Solutions sớm, Lists dài (>5 items) |
| **Body Chunk 3 (35-45s)** | Solution category, Lời khuyên chung, Nguồn | "Nguồn kẽm: Thịt, hải sản...", "Cần 15mg/ngày..." | Specific products (Structure A), Tips không liên quan |
| **Phase 4A (45-55s)** Educational | Advanced tip, Optimization, Lỗi cần tránh | "Uống với vitamin C...", "Tránh uống với canxi..." | Product mentions, Lặp info cơ bản, Contradiction |
| **Phase 4B (45-55s)** Product | Product name, USP, Social proof, CTA | "ZincMax Pro - kẽm picolinate...", "Hàng nghìn người..." | Hard sell, Price wars, Chi tiết product dài |
| **Outro (55-60s)** | Catchphrase, Soft CTA, Future tease | "Nhớ lấy, làm đàn ông...", "Follow để học thêm..." | Info mới, Product intro (quá muộn), Nhiều CTAs |

---

## PHẦN 5: HƯỚNG DẪN PROMPTING THEO PARAMETER

### Cho AI/Content Creators

Khi generate scripts dùng structure này, sử dụng parameter system sau:

---

### Template Prompt

```markdown
# TASK: Generate Full Video Script (0-60s)

## PARAMETERS

**Product_Include**: [True / False]
- True  → Dùng Structure B (Giáo Dục + Product Introduction ở 45-55s)
- False → Dùng Structure A (Chỉ Giáo Dục, Advanced Insight ở 45-55s)

**Topic**: [Topic video của bạn]

**Pain_Point**: [Pain point cụ thể từ context.md]

**Dopamine_Technique**: [Chọn từ hook_principle.md]

**Formula_Reference**: [Optional - Nếu dùng formula từ