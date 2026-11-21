# Computer Vision Course Projects

A collection of practical projects spanning image segmentation, object detection, transfer learning, deep learning, classical computer vision, motion, stereo depth, and digital image processing.

## Repository Structure

The repository contains nine category folders and thirteen notebook projects. Some categories contain multiple project subfolders.

| Category | Focus | Project README |
|---|---|---|
| `01-image-segmentation/` | Semantic and instance segmentation | See project links below |
| `02-object-detection/` | Object localization and detection | See project links below |
| `03-transfer-learning/` | Pretrained CNN transfer learning | See project links below |
| `04-image-classification/` | MNIST classification models | See project links below |
| `05-deep-learning-with-tensorflow-keras/` | CNN architecture comparisons | See project links below |
| `06-classical-cv/` | Geometry, Hough transforms, edges, panorama | See project links below |
| `07-motion-estimation/` | Motion and optical flow | See project links below |
| `08-stereo-and-depth-estimation/` | Stereo disparity and depth | See project links below |
| `09-digital-image-processing-fundamentals/` | Image processing fundamentals | See project links below |

### Project Guides

| Category | Project | Guide |
|---|---|---|
| 01-image-segmentation | Pet Image Segmentation with U-Net | [README](01-image-segmentation/image-segmentation-using-U_NET/README.md) |
| 01-image-segmentation | Concrete Defect Instance Segmentation with YOLO11 | [README](01-image-segmentation/Instance-segmentation/README.md) |
| 02-object-detection | Clash of Clans Object Detection with YOLO11s | [README](02-object-detection/README.md) |
| 03-transfer-learning | Transfer Learning and Fine-Tuning of Pretrained CNNs | [README](03-transfer-learning/README.md) |
| 04-image-classification | MNIST and Pet Image CNN Comparisons | [README](04-image-classification/README.md) |
| 05-deep-learning-with-tensorflow-keras | MNIST and Pet Image CNN Comparisons | [README](05-deep-learning-with-tensorflow-keras/README.md) |
| 06-classical-cv | Geometric Image Transformations | [README](06-classical-cv/Geometric%20image%20transformation/README.md) |
| 06-classical-cv | Hough Transforms for Circle and Line Detection | [README](06-classical-cv/Hough%20transformation/README.md) |
| 06-classical-cv | Image Edge Detection with Sobel, Laplacian, and Canny | [README](06-classical-cv/Image%20Edge%20detetction/README.md) |
| 06-classical-cv | Feature Matching and Panorama Stitching | [README](06-classical-cv/panorama/README.md) |
| 07-motion-estimation | Motion Estimation and Optical Flow | [README](07-motion-estimation/README.md) |
| 08-stereo-and-depth-estimation | Stereo Disparity and Depth from Block Matching | [README](08-stereo-and-depth-estimation/README.md) |
| 09-digital-image-processing-fundamentals | Digital Image Processing Fundamentals | [README](09-digital-image-processing-fundamentals/README.md) |

## Tech Stack

- **Language:** Python 3.10+
- **Computer vision:** OpenCV, Ultralytics YOLO11, scikit-image
- **Deep learning:** TensorFlow, Keras, TensorFlow Datasets, PyTorch
- **Numerical/image processing:** NumPy, SciPy, Pillow
- **Visualization and evaluation:** Matplotlib, pandas, scikit-learn, pycocotools

## Running the Notebooks

Open a project guide and launch its notebook in Colab or Jupyter. Notebooks may download external datasets or require local image/video files. The guides use `pip install -r ../../requirements.txt`; this repository currently has no `requirements.txt`, so dependencies must be installed separately until one is added.
