# Assignment 1 Report

**Course:** COSC 073 - Computational Photography  
**Term:** Spring 2026  
**Author:** Kasuti Makau

---

## 1.1 Basic Image Processing Pipeline

### RAW Image Conversion

**Q: What are the black, white, and scale values extracted from the RAW file?**

| Parameter | Value |
|-----------|-------|
| Black     | 2044  |
| White     | 16383 |
| R Scale   | 2.293742 |
| G Scale   | 1.000000 |
| B Scale   | 1.368654 |

### Python Initials

**Q: How many bits per pixel does the image have? What is its width and height?**

| Property        | Value       |
|-----------------|-------------|
| Bits per pixel  | 16          |
| Width           | 6020 px     |
| Height          | 4016 px     |

### Bayer Pattern Identification

**Method:** For each of the four candidate patterns (`grbg`, `rggb`, `bggr`, `gbrg`), we subsampled `img_linear` to extract R, G, and B channels at their respective pixel positions, applied the dcraw white balance multipliers (R=2.293742, G=1.0, B=1.368654) as a visual aid, and rendered a 300×300 crop of the top-left corner. The correct pattern is the one that produces natural-looking colors.

**Result:** `rggb` — the only pattern that showed a realistic blue/gray sky with dark tree branches. The other three produced strong magenta (`grbg`, `gbrg`) or orange (`bggr`) color casts.