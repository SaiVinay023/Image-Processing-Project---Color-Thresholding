
---

# Image Processing Project - Color Thresholding

## Project Description

This project demonstrates a basic image processing technique called **Color Thresholding** using Python and libraries such as NumPy and Matplotlib. The purpose of color thresholding is to isolate or highlight certain areas in an image based on their RGB color values. This project implements a simple thresholding algorithm to filter out specific colors in an image and create a binary output (black and white) based on the applied thresholds.

## Project Structure

```
├── .gitattributes        # Git configuration file
├── .gitignore            # Git ignore file to exclude unnecessary files
├── code1.ipynb           # Jupyter Notebook with project progress and code implementations
├── hello.ipynb           # Another notebook with project progress
├── sample.jpg            # Sample image used for the color thresholding algorithm
```

## Key Features

1. **Color Thresholding Algorithm**: 
   The algorithm is implemented in Python using the NumPy library. It creates a binary image by selecting pixels that meet the defined RGB thresholds.
   
2. **Input and Output**: 
   - The input is an RGB image (`sample.jpg` in this case).
   - The output is a binary image highlighting areas of interest based on color selection criteria.

3. **Customizable Thresholds**:
   - Users can modify the red, green, and blue thresholds to customize which parts of the image are selected for color thresholding.

## Code Walkthrough

### Color Thresholding Function

```python
def color_thresh(img, rgb_thresh):
    # Create an empty array the same size as the image but with a single channel
    color_select = np.zeros_like(img[:,:,0])
    
    # Apply RGB threshold
    above_thresh = (img[:,:,0] > rgb_thresh[0]) \
                & (img[:,:,1] > rgb_thresh[1]) \
                & (img[:,:,2] > rgb_thresh[2])
    
    # Assign 1's where the thresholds are exceeded
    color_select[above_thresh] = 1
    
    return color_select
```

### Thresholds Definition

```python
# Define the RGB threshold values
red_threshold = 160
green_threshold = 160
blue_threshold = 160

# Set the threshold tuple
rgb_threshold = (red_threshold, green_threshold, blue_threshold)

# Apply the thresholding function to the input image
colorsel = color_thresh(image, rgb_thresh=rgb_threshold)
```

### Visualizing the Results

```python
# Display the original and the binary images side by side
f, (ax1, ax2) = plt.subplots(1, 2, figsize=(21, 7), sharey=True)
f.tight_layout()
ax1.imshow(image)
ax1.set_title('Original Image', fontsize=40)

ax2.imshow(colorsel, cmap='gray')
ax2.set_title('Thresholded Image', fontsize=40)
plt.subplots_adjust(left=0., right=1, top=0.9, bottom=0.)
plt.show()
```

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/YourUsername/your-repo-name.git
   ```

2. Install the required Python libraries:
   ```bash
   pip install numpy matplotlib jupyter
   ```

3. Run the Jupyter notebook to explore the code:
   ```bash
   jupyter notebook code1.ipynb
   ```

## Requirements

- Python 3.x
- Jupyter Notebook
- NumPy
- Matplotlib

## How to Use

1. Place the image you want to process in the project directory.
2. Open the `code1.ipynb` Jupyter notebook.
3. Modify the `red_threshold`, `green_threshold`, and `blue_threshold` variables to suit your needs.
4. Run the notebook cells to see the color thresholding in action.


## Future Improvements

- Add functionality for dynamic color range selection via a GUI interface.
- Experiment with different types of thresholding (e.g., HSV-based).
- Implement edge detection along with color thresholding for advanced image segmentation.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---
