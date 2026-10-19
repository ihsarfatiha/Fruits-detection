# Fruit Detection with YOLOv8

Deteksi 6 jenis buah menggunakan YOLOv8s custom training.

**Kelas:** Apple, Banana, Grape, Orange, Pineapple, Watermelon

## Isi repo

| File / Folder | Keterangan |
| --- | --- |
| `train_fruit_detection.py` | Script training, validasi, dan evaluasi model |
| `realtime_fruit_detection.py` | Deteksi real-time dari webcam / video / gambar |
| `reduce_dataset.py` | Utilitas mengurangi jumlah dataset |
| `fruit_detection_training.ipynb` | Notebook eksperimen training |
| `data.yaml` | Konfigurasi dataset (6 kelas) |
| `fruit_detection_runs/` | Hasil training: metrik, kurva, confusion matrix, `best.pt` |
| `fruit_detection_academic_report.docx.pdf` | Laporan akademik |
| `screenshot_*.jpg` | Screenshot hasil deteksi |

## Instalasi

```bash
pip install ultralytics opencv-python
```

## Menjalankan

```bash
# Real-time dari webcam (default memakai best.pt)
python realtime_fruit_detection.py

# Dengan weights tertentu
python realtime_fruit_detection.py --weights fruit_detection_runs/train/weights/best.pt
```

## Training ulang

Dataset tidak disertakan di repo karena ukurannya besar. Siapkan ulang dengan struktur:

```
train/images  train/labels
valid/images  valid/labels
test/images   test/labels
```

lalu jalankan:

```bash
python train_fruit_detection.py
```

`yolov8s.pt` (pretrained) akan diunduh otomatis oleh Ultralytics saat training pertama.

## Hasil

Grafik dan metrik training tersedia di `fruit_detection_runs/train/`:
`results.csv`, `results.png`, `BoxF1_curve.png`, `BoxPR_curve.png`, `confusion_matrix.png`.
