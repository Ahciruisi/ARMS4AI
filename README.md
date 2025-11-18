# ARMS4AI
BTECH_EVALUATION_TASK

Cloudless Raster Mosaic Visualization (Google Colab)

This project provides a reliable method for visualizing large, generated geospatial rasters (TIFF files) within a Google Colab environment, specifically tailored to avoid the "out-of-memory" crashes common with large datasets.

Key Features & Colab Optimization

Memory Efficiency: The code bypasses Colab's RAM limitations by only loading a small, defined sample window of the full mosaic (cloudless_mosaic.tif) for visualization, preventing session crashes.
Geospatial Integrity: Uses rasterio to correctly read the raster and automatically identify the NoData value from the file's metadata for accurate masking.
Contrast Correction: Implements percentile clipping (default 2% to 98% stretch) during normalization to ensure the sampled image displays with proper visual contrast, even when viewing small, dark, or homogeneous areas.
Explicit Cleanup: Includes Python's garbage collection (gc.collect()) to manually free up memory immediately after the plot is displayed, maximizing available RAM for subsequent steps.

Requirements

This notebook block assumes the following libraries are installed and imported:
rasterio
numpy (np)
matplotlib.pyplot (plt)

Usage & Configuration

Before running the visualization block, ensure the OUTPUT_FILE variable is set to the path of your mosaic (e.g., "cloudless_mosaic.tif").
Parameter
Description
Recommended Adjustment
SAMPLE_SIZE
The pixel dimensions of the area to load (e.g., 1000x1000). Keep this low to save RAM.
Default: 1000
OFFSET_X & OFFSET_Y
The top-left corner coordinates (in pixels) of the area you want to sample.
Adjust these to view different parts of your mosaic.
lower_percentile & upper_percentile
The percentile range for image contrast normalization.
Adjust these (e.g., to $1$ and $99$) if the resulting image is too dark or washed out.



Download Dataset: https://objectstore.e2enetworks.net/btechtasksampledata/data.zip
