# CC_estimate
Estimate Cloud Cover in specific area

This Python script is designed to download, process, and analyze satellite images from the GOES-16 satellite to calculate cloud cover percentages at specified latitude and longitude coordinates. The script includes several key functions and processes:

1. **`download_goes_images`**:
   - Downloads GOES-16 images based on the specified base URL and date.
   - It iterates over the hours and minutes specified in `hours_range` and `minutes_range` to construct image URLs.
   - Downloads the images into a specified output folder, checking for pre-existing files to avoid redundant downloads.

2. **`lat_lon_to_pixel`**:
   - Converts geographic coordinates (latitude and longitude) into pixel coordinates based on the satellite's geostationary projection.
   - This is crucial for mapping the cloud cover data to specific geographic locations in the image.

3. **`calculate_cloud_cover`**:
   - This function reads an image, converts it to grayscale, and thresholds the image to identify cloud pixels.
   - It then calculates the percentage of cloud cover in a small region surrounding the target latitude and longitude coordinates.

4. **`get_bounding_box`**:
   - Computes the bounding box around a specific latitude and longitude, based on a given radius in kilometers.
   - This is used to determine the area surrounding a target point where cloud cover will be assessed.

5. **`plot_cloud_cover_by_hour`**:
   - Visualizes the cloud cover data in a bar plot, showing cloud cover percentages for selected hours (00, 12, 18) of the day.
   - The plot is saved as a JPEG file and displayed to the user.

6. **`main`**:
   - Orchestrates the process by calling the aforementioned functions in sequence.
   - Downloads the images, calculates the cloud cover for the target location at each time point, and then plots the results.

### Key Features:
- The script automatically downloads and processes GOES-16 images over the past few days.
- It uses the Pyproj library to handle geographic projections and transformations.
- It generates detailed plots showing cloud cover trends at different times of the day.

### Requirements:
- `requests` for HTTP requests.
- `numpy` for numerical operations.
- `opencv-python` (cv2) for image processing.
- `matplotlib` and `seaborn` for plotting.
- `pyproj` for handling geographic projections.

This script is useful for monitoring cloud cover in specific regions using satellite imagery and can be adapted for other satellite products or weather-related analysis tasks.
