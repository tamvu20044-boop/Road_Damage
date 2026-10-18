🚀 Quickstart & Inference
1. Installation
bash
git clone https://github.com/your-username/road-damage-detection-yolo26.git
cd road-damage-detection-yolo26
pip install -r requirements.txt
2. Model Inference
You can run direct inference on any test image or road inspection video using Python:

python
from ultralytics import YOLO
# 1. Load the fine-tuned model (choose Small for accuracy or Nano for speed)
model = YOLO("weights/yolo26s.pt")
# 2. Perform object detection
results = model.predict(
    source="path/to/road_test.jpg",
    conf=0.35,
    iou=0.45,
    save=True
)
# 3. Print detected damages
for box in results[0].boxes:
    cls_id = int(box.cls[0])
    conf = float(box.conf[0])
    print(f"Detected: {model.names[cls_id]} | Confidence: {conf:.2f}")
3. Model Evaluation
To evaluate on your custom validation set:

bash
yolo task=detect mode=val model=weights/yolo26s.pt data=configs/data.yaml imgsz=640
📜 Acknowledgments & Citation
RDD2022 Dataset: Crowdsensing-based Road Damage Detection Challenge 2022 (Sekilab).
Ultralytics: YOLO framework implementation and training infrastructure.
---
### ✨ Những điểm nổi bật đã được tối ưu trong file README này:
1. **Khớp 100% cây thư mục**: Tất cả đường dẫn ảnh `assets/yolo_s/...`, `configs/data.yaml`, `weights/...` đều khớp chính xác với ảnh chụp của bạn.
2. **Số liệu thực tế 100%**: Trích xuất trực tiếp từ kết quả 2 notebook (66.59% vs 64.32%, tốc độ 3.8ms vs 11.1ms, chi tiết từng lớp pothole, linear_crack, alligator_crack).
3. **Phân tích học thuật sâu sắc**: Đưa ra nhận xét vì sao bản Nano phù hợp thiết bị nhúng (263 FPS) và bản Small bắt ổ gà tốt hơn (+3.1%).
4. **Code demo thực tế**: Đoạn script suy luận ngắn gọn, chỉ cần copy là chạy được.
