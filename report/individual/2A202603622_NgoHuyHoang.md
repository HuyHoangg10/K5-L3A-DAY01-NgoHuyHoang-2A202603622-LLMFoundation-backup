# Báo cáo cá nhân — Day 01: Lọc tin nhắn rác bằng ML, DL, Embedding và LLM

- **MSSV:** 2A202603622
- **Họ và tên:** Ngô Huy Hoàng
- **SEED:** 3537

## 1. Bằng chứng

| Tệp | Có? |
| --- | --- |
| `day01_lab.ipynb` | ✅ |
| `lab1_report.json` | ✅ |
| `hand_calc.jpg` | ✅ |

## 2. Kết quả chính

| Phương pháp | F1 test | F1 SUB 40 | p95 ms/tin | USD/1k tin |
| --- | ---: | ---: | ---: | ---: |
| BoW + LogReg | 0.865 | 0.857 | 0.089 | 0 |
| BoW + MLP | 0.937 | 0.947 | 0.511 | 0 |
| Encoder + kNN | 0.902 | 0.923 | 123.975 | 0 |
| Encoder + LogReg | 0.939 | 0.947 | 39.549 | 0 |
| Encoder + MLP | 0.944 | 0.947 | 45.589 | 0 |

Toi khong chay LLM API nen khong co ket qua that cua phan LLM.

## 3. Dự đoán và thực tế

1. Toi du doan F1 cua BoW + LogReg la 0.87%, nhung ket qua that la 0.865, tuc khoang 86.5%. Toi da nham giua ti le va phan tram. Toi cung nham ve phan bo data, vi ham moi la class chiem da so.

2. Toi du doan val loss se giam trong khoang 10 epoch, nhung thuc te val loss thap nhat o epoch 5 va bat dau tang sau do. Model bat dau overfit som hon toi nghi.

3. O stress test, toi du doan BoW dat khoang 55–60% va cac model embedding dat khoang 60–70%. Ket qua accuracy lan luot la 52%, 50%, 70%, 64% va 66%. Du doan cua toi gan dung, nhung Embedding + kNN tot hon toi nghi.

## 4. Phân tích 50 case khó

BoW + MLP tut nhieu nhat, F1 giam tu 0.947 xuong 0.324. Model nay kho voi spam giong tu nhien va ne tu khoa vi BoW chi nhin cac token roi rac.

Case #12 la spam viet nhu mot cuoc tro chuyen lich su, khong co tu khoa spam ro rang, nen tat ca model deu doan sai. Case #31 chen dau cham giua cac chu cai, lam BoW khong nhan ra cac tu da hoc.

## 5. Thử thách cá nhân

De cua toi la chay kNN voi k = 1, 5 va 25. Phan nay toi chua hoan thanh trong bai nop.

## 6. Phương án cho sản phẩm thật

Toi chon BoW + MLP lam model chinh vi F1 test dat 0.937, p95 chi 0.511 ms va khong ton chi phi API. Encoder + MLP co F1 cao hon mot chut nhung p95 la 45.589 ms, kha sat gioi han 50 ms.

Co the dung BoW + MLP xu ly cac tin model tu tin, sau do chuyen cac tin co probability gan 0.5 sang Encoder + MLP. Cach nay can bang duoc toc do va chat luong.

## 7. AI log và điều đã học

Toi dung AI de giai thich vocab, vectorize, MLP, embedding, doc metric, ho tro code Phan 4 va phan tich ket qua Phan 5. Sau do toi chay bo test, doi chieu voi output notebook va tu lam lai cac phep tinh tren giay.

Sau bai nay toi hieu ro hon viec model phuc tap hon khong phai luc nao cung la lua chon tot hon. Khi chon model con phai xem F1, latency, chi phi, data va yeu cau cua san pham.
