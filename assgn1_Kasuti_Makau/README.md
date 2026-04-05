# Homework Assignment 1

**Course:** COSC 073 - Computational Photography  
**Term:** Spring 2026  
**Author:** Kasuti Makau

---

## Getting Started

1. Create a virtual environment:
   ```bash
   python3 -m venv venv
   ```

2. Activate the virtual environment:
   ```bash
   source venv/bin/activate
   ```

3. Install requirements:
   ```bash
   pip install -r requirements.txt
   ```

---

## 1.1 Implement a Basic Image Processing Pipeline

### 1.1a RAW Image Conversion

**Prerequisite:** Install `dcraw` since RAW files cannot be directly read by `skimage`.
```bash
brew install dcraw
```

#### Step 1: Extract RAW metadata
Run this command to get the black, white and scale values:
```bash
dcraw -4 -d -v -W -T data/Thayer.CR2
```

**Example output:**
```
Loading Canon EOS 2000D image from data/Thayer.CR2 ...
Scaling with darkness 2044, saturation 16383, and
multipliers 2.293742 1.000000 1.368654 1.000000
Building histograms...
Writing data to data/Thayer.tiff ...
```

**Extracted values:**

| Parameter | Value |
|-----------|-------|
| Black     | 2044  |
| White     | 16383 |
| R Scale   | 2.293742 |
| G Scale   | 1.000000 |
| B Scale   | 1.368654 |

#### Step 2: Generate the correct TIFF file

**Important:** Delete the `.tiff` file created in Step 1, then run dcraw with different flags:

```bash
rm data/Thayer.tiff
dcraw -4 -D -T data/Thayer.CR2
```

This produces a new `.tiff` file .

> **Note:** The `-D` flag (uppercase) outputs the raw sensor data without any processing, while `-d` (lowercase) applies basic scaling. We need the unprocessed data for our pipeline.
