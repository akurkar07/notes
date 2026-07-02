# Image Processing Comprehensive Notes

These notes summarise the Image Processing lecture slides into revision-focused explanations. The module covers how digital images are represented, transformed, filtered, segmented, and evaluated.

## Big Picture

Image processing is about transforming images to make information easier to measure, interpret, or use. The module moves from low-level pixel operations to higher-level segmentation.

Typical pipeline:

1. Image formation and acquisition
2. Digital representation
3. Point processing and colour spaces
4. Histogram processing
5. Linear and non-linear filtering
6. Thresholding and binary images
7. Connected components and morphology
8. Derivatives, sharpening, and edge detection
9. Hough transform
10. Segmentation and superpixels
11. Segmentation metrics
12. Interactive segmentation with graph cut

## Digital Images

A digital image is a sampled and quantised representation of a visual scene.

Key ideas:

- Sampling decides the spatial grid of pixels.
- Quantisation decides the finite set of possible intensity values.
- Each pixel stores one or more values.
- Greyscale images usually store one intensity per pixel.
- Colour images store multiple channels, commonly red, green, and blue.

### Pixel Coordinates

Images are usually treated as a 2D array:

- x coordinate: horizontal position.
- y coordinate: vertical position.
- I(x, y): intensity at that pixel.

Neighbourhoods are important because images are spatially organised. Nearby pixels often belong to the same surface, object, or illumination region.

### Greyscale Images

For an L-level greyscale image:

- Pixel values are usually in the range 0 to L - 1.
- For 8-bit images, L = 256 and values are 0 to 255.
- Low values are dark.
- High values are bright.

### Colour Images

RGB images use three channels:

- Red
- Green
- Blue

Other colour spaces may be more useful for some tasks because they separate brightness from colour information.

Common colour-space idea:

- Some spaces represent intensity/luminance separately from chromatic information.
- This can make thresholding or segmentation easier.

## Point Processing

Point processes transform each pixel independently.

General form:

```text
output(x, y) = T(input(x, y))
```

The output at a pixel depends only on the input value at that same pixel.

Examples:

- Brightness adjustment
- Contrast adjustment
- Negative image
- Thresholding
- Intensity stretching

Strength:

- Simple and fast.

Limitation:

- Ignores spatial context.

## Intensity Transformations

Intensity transformations remap pixel values.

Examples:

- Darken: map values lower.
- Brighten: map values higher.
- Increase contrast: spread values over a wider range.
- Decrease contrast: compress the range.

Contrast stretching is useful when an image uses only a small part of the available intensity range.

## Histograms

The histogram of an image counts how many pixels have each intensity.

For grey levels in range 0 to L - 1:

```text
p(r_k) = n_k
```

where:

- r_k is the kth grey level.
- n_k is the number of pixels with grey level r_k.
- k ranges from 0 to L - 1.

Histograms provide global information about the image.

They can indicate:

- Whether an image is dark or light.
- Whether contrast is low or high.
- Whether there are multiple dominant intensity groups.
- Whether thresholding may separate object and background.

### Histogram Normalisation

A normalised histogram divides counts by the total number of pixels.

```text
p(r_k) = n_k / N
```

where N is the total number of pixels.

This can be interpreted as an estimated probability distribution over intensity values.

### Cumulative Distribution Function

The cumulative distribution function sums histogram probabilities up to a grey level.

It is useful for histogram equalisation.

### Histogram Equalisation

Histogram equalisation remaps intensities to spread values more evenly across the available range.

Goal:

- Improve contrast, especially when the image occupies a narrow intensity range.

Important point:

- It is a global method, so it may over-enhance noise or produce unnatural contrast in some images.

## Spatial Filtering

Spatial filtering uses a local neighbourhood around each pixel.

General idea:

1. Place a window or mask over a pixel.
2. Use the pixel values inside the window.
3. Compute a new value for the target pixel.
4. Move the window across the image.

This uses local context, unlike point processing.

## Linear Filters

A linear filter computes a weighted sum of pixels in a neighbourhood.

This is usually implemented by convolution or correlation with a mask/kernel.

For a 3 x 3 filter:

```text
output(x, y) = sum of kernel(i, j) * image(x + i, y + j)
```

### Mean Filter

The mean filter replaces a pixel with the average of its neighbourhood.

Example 3 x 3 mean kernel:

```text
1/9 * [1 1 1
       1 1 1
       1 1 1]
```

Effect:

- Smooths the image.
- Reduces noise.
- Blurs edges and fine detail.

### Gaussian Filter

Gaussian filtering uses weights based on a Gaussian distribution.

Effect:

- Smooths the image.
- Gives more weight to nearby pixels.
- Produces less blocky blur than a simple mean filter.

Important parameter:

- sigma controls the scale of smoothing.

Larger sigma:

- More smoothing.
- More edge blurring.

### Noise

Filtering is often used to reduce noise.

Common noise types:

- Gaussian noise: small random intensity variation.
- Salt-and-pepper noise: isolated black and white pixels.

Mean and Gaussian filters are useful for Gaussian-like noise, but not ideal for salt-and-pepper noise.

## Non-Linear Filters

Non-linear filters do not compute a simple weighted sum.

They are often better at preserving edges.

### Median Filter

The median filter replaces a pixel with the median value in its neighbourhood.

Effect:

- Good for salt-and-pepper noise.
- Preserves edges better than mean filtering.

Why it is non-linear:

- Median is an order statistic, not a weighted sum.

### Anisotropic Diffusion

Anisotropic diffusion smooths within regions while reducing smoothing across edges.

Idea:

- Diffusion is strong where intensity changes slowly.
- Diffusion is weak across strong gradients.

Effect:

- Smooths noise.
- Preserves important boundaries.

### Bilateral Filter

Bilateral filtering combines:

- Spatial closeness
- Intensity similarity

Pixels contribute more if they are nearby and similar in intensity.

Effect:

- Smooths within regions.
- Preserves edges better than Gaussian filtering.

## Thresholding and Binary Images

Thresholding converts an image into a binary image.

Binary image:

- Pixels are either 0 or 1.
- Often interpreted as background and object.

For a dark object on a light background:

```text
if I(x, y) < T:
    object
else:
    background
```

For a bright object on a dark background:

```text
if I(x, y) > T:
    object
else:
    background
```

### Global Thresholding

A single threshold T is used for the whole image.

Works well when:

- Illumination is fairly uniform.
- Object and background intensities are well separated.

Fails when:

- Lighting varies across the image.
- Object and background overlap in intensity.
- There is heavy noise.

### Adaptive Thresholding

Adaptive thresholding computes a threshold locally.

Useful when:

- Illumination changes across the image.
- A single global threshold is not enough.

Trade-off:

- More flexible, but depends on window size and local statistic.

## Connected Components

Connected component labelling identifies connected sets of object pixels.

Connectivity can be:

- 4-neighbour connectivity: up, down, left, right.
- 8-neighbour connectivity: includes diagonals.

Choosing 4 or 8 connectivity changes whether diagonal pixels are considered connected.

Connected components are useful for:

- Counting objects.
- Measuring object area.
- Filtering small noisy regions.
- Extracting regions of interest.

## Mathematical Morphology

Morphology processes binary or greyscale images using a structuring element.

The structuring element defines the local shape used to probe the image.

Common operations:

- Erosion
- Dilation
- Opening
- Closing

### Erosion

Erosion shrinks foreground objects.

For binary images:

- A foreground pixel remains foreground only if the structuring element fits inside the foreground at that position.

Effects:

- Removes small objects.
- Breaks thin connections.
- Shrinks boundaries.

### Dilation

Dilation expands foreground objects.

For binary images:

- A pixel becomes foreground if the structuring element overlaps foreground.

Effects:

- Fills small gaps.
- Connects nearby components.
- Expands boundaries.

### Opening

Opening is erosion followed by dilation.

Effects:

- Removes small foreground noise.
- Smooths object boundaries.
- Breaks narrow bridges.

### Closing

Closing is dilation followed by erosion.

Effects:

- Fills small holes.
- Closes narrow gaps.
- Smooths boundaries.

### Regions of Interest and Masks

A region of interest is a selected part of an image.

A mask specifies where an operation should apply.

This is powerful because image processing can be applied selectively, for example only inside a detected object or bounding box.

## Derivatives and Edges

Image features are often characterised by changes in intensity.

Derivatives measure change:

- First derivative: rate of change.
- Second derivative: change in the rate of change.

Edges usually correspond to sharp intensity changes.

## First Derivative Filters

In 1D, a first derivative can be approximated by differences between neighbouring values.

In 2D, the gradient has x and y components:

```text
grad I = (dI/dx, dI/dy)
```

Gradient magnitude:

```text
sqrt((dI/dx)^2 + (dI/dy)^2)
```

Approximation often used:

```text
abs(dI/dx) + abs(dI/dy)
```

Gradient direction tells the direction of greatest intensity increase.

### Roberts Operator

Roberts uses small diagonal masks.

Strength:

- Very fast.

Weakness:

- Sensitive to noise.
- Responds mainly to very sharp edges.

### Sobel Operator

Sobel estimates horizontal and vertical derivatives using 3 x 3 masks.

Strength:

- More robust than Roberts because it includes smoothing.
- Still widely used.

Weakness:

- Requires threshold selection.
- Can produce thick edges.

## Image Sharpening

Sharpening enhances edges and fine detail.

### Unsharp Masking

Procedure:

1. Smooth the image, often with a Gaussian.
2. Subtract the smoothed image from the original to get high-frequency detail.
3. Add this detail back to the original.

Effect:

- Edges appear sharper.

Risk:

- Noise may also be sharpened.

### Laplacian Sharpening

The Laplacian is a second derivative operator.

A common 4-neighbour Laplacian mask:

```text
 0 -1  0
-1  4 -1
 0 -1  0
```

A sharpening operator can combine the original image with the Laplacian.

Example single-step sharpening mask:

```text
 0 -1  0
-1  5 -1
 0 -1  0
```

The central positive value preserves the original pixel while neighbouring negative values emphasise differences.

## Edge Detection

Edge detection aims to locate boundaries where image properties change sharply.

Ideal edge:

- First derivative has a peak.
- Second derivative has a zero-crossing.

### First-Derivative Edge Detection

Procedure:

1. Compute gradient magnitude.
2. Threshold the magnitude.
3. Pixels above threshold are edge candidates.

Problem:

- Threshold choice is difficult.
- Noise also produces high gradients.

### Second-Derivative Edge Detection

Second derivative methods detect zero-crossings.

They often smooth first to reduce noise.

### Marr-Hildreth Edge Detector

Marr-Hildreth:

1. Smooth with a Gaussian.
2. Apply the Laplacian.
3. Detect zero-crossings.

This can be implemented as a Laplacian of Gaussian.

### Difference of Gaussians

Difference of Gaussians approximates Laplacian of Gaussian.

Idea:

- Smooth image with two Gaussian filters of different sigma.
- Subtract the results.

This approximates edge-sensitive second derivative behaviour.

## Canny Edge Detector

Canny is a widely used edge detector designed for:

- Good detection
- Good localisation
- Minimal response

Pipeline:

1. Smooth with a Gaussian.
2. Compute gradient magnitude and direction.
3. Apply non-maximum suppression.
4. Apply double thresholding.
5. Track edges by hysteresis.

### Non-Maximum Suppression

Non-maximum suppression thins edges.

For each pixel:

- Check whether it is a local maximum along the gradient direction.
- Keep it only if it is the strongest response across the edge.

Without this, thresholding can leave thick edges.

### Hysteresis Thresholding

Hysteresis uses two thresholds:

- High threshold: strong edges.
- Low threshold: weak candidate edges.

Keep weak edges only if they connect to strong edges.

This fills gaps while rejecting isolated weak noise responses.

## Hough Transform

The Hough Transform detects parameterised shapes, especially lines.

Line equation:

```text
y = m x + c
```

If a point (x_i, y_i) lies on a line, then:

```text
y_i = m x_i + c
```

Rearranged:

```text
c = -m x_i + y_i
```

This means one image point corresponds to a line in parameter space.

If many image points lie on the same line, their parameter-space curves intersect at a common point.

### Hough Algorithm for Lines

1. Quantise parameter space into an accumulator array.
2. Initialise accumulator cells to zero.
3. For each edge pixel, vote for all parameter values consistent with that pixel.
4. Find accumulator cells with large values.
5. Each peak corresponds to a detected line.

Strength:

- Can detect lines even with gaps and noise.

Weakness:

- Gives line parameters, not necessarily exact segment endpoints.
- Accumulator resolution affects accuracy and cost.

## Segmentation

Segmentation partitions an image into meaningful regions.

Possible region properties:

- Intensity
- Colour
- Texture
- Gradient
- Spectral profile

Segmentation is hard because "meaningful" depends on the task.

## Region-Based Segmentation

Region-based methods aim to create regions that are internally similar and different from neighbouring regions.

### Region Growing

Region growing starts from seed pixels.

Procedure:

1. Choose seed pixels.
2. Compute region statistics.
3. Add neighbouring pixels that are similar enough.
4. Update statistics.
5. Repeat until no more pixels fit.

Strength:

- Simple and intuitive.

Weakness:

- Depends on seed choice and similarity threshold.

### Split and Merge

Split:

- Start with the whole image as one region.
- Split regions that are not internally consistent.

Merge:

- Combine adjacent regions that are sufficiently similar.

Quadtrees are a common structure for recursive splitting.

## Edge-Based Segmentation

Edge-based segmentation uses boundaries.

Idea:

- If edges correspond to object boundaries, then closed edge contours define regions.

Problem:

- Edges may be broken.
- Texture and noise can create false edges.

## Watershed Segmentation

Watershed views the gradient image as a topographic surface.

Interpretation:

- Low-gradient regions are valleys.
- High-gradient regions are ridges.
- Flooding from minima forms catchment basins.
- Watershed lines separate regions.

Algorithm idea:

1. Sort pixels by gradient value from low to high.
2. Process pixels in that order.
3. Assign labels based on labelled neighbours.
4. Create boundaries where growing regions meet.

Watershed can be efficient and can run in linear time with suitable sorting because digital images have a finite set of grey values.

Weakness:

- Can over-segment noisy images.

## Superpixels

Superpixels group pixels into small, coherent regions.

They are not necessarily final semantic segments. They are often used as a preprocessing step.

Advantages:

- Reduce the number of units from pixels to regions.
- Preserve local boundaries.
- Make later algorithms faster.

### SLIC

SLIC stands for Simple Linear Iterative Clustering.

Key properties:

- Produces compact, nearly uniform superpixels.
- Based on k-means style clustering.
- Main parameter is the desired number of superpixels.

Basic process:

1. Initialise cluster centres on a grid.
2. Move centres to low-gradient positions if needed.
3. Assign pixels to nearby cluster centres based on colour and spatial distance.
4. Recompute centres.
5. Iterate.

Distance combines:

- Colour similarity.
- Image-plane distance.

## Segmentation Metrics

Segmentation metrics compare predicted masks with ground truth.

First define:

- True Positive: predicted foreground and actually foreground.
- False Positive: predicted foreground but actually background.
- False Negative: predicted background but actually foreground.
- True Negative: predicted background and actually background.

### Accuracy

```text
accuracy = (TP + TN) / (TP + TN + FP + FN)
```

Problem:

- Accuracy can be misleading under class imbalance.

Example:

- If background dominates, predicting background everywhere can have high accuracy but useless segmentation.

### Precision

```text
precision = TP / (TP + FP)
```

Precision answers:

- Of the pixels predicted as object, how many were correct?

High precision means few false positives.

### Recall

```text
recall = TP / (TP + FN)
```

Recall answers:

- Of the true object pixels, how many were found?

High recall means few false negatives.

### F1 Score

```text
F1 = 2 * precision * recall / (precision + recall)
```

F1 balances precision and recall.

### Intersection over Union

```text
IoU = intersection / union
```

For binary masks:

```text
IoU = TP / (TP + FP + FN)
```

IoU is widely used for segmentation.

### Dice Coefficient

```text
Dice = 2TP / (2TP + FP + FN)
```

Dice is similar to F1 for binary segmentation masks.

### Hausdorff Distance

Hausdorff distance measures boundary mismatch.

It is useful when region overlap alone is not enough. Two segmentations may have similar IoU but poor contour alignment.

## Interactive Segmentation

Interactive segmentation uses user input to guide the algorithm.

Example:

- The user marks rough foreground and background regions.
- The algorithm segments the object of interest.

This is useful when fully automatic segmentation is difficult.

## Graph Cut Segmentation

Graph cut formulates segmentation as a graph optimisation problem.

Graph structure:

- Pixels are nodes.
- Source represents foreground.
- Target represents background.
- t-links connect pixels to source or target.
- n-links connect neighbouring pixels to each other.

Weights:

- t-link weights encode likelihood of foreground/background.
- n-link weights encode similarity between neighbouring pixels.

If neighbouring pixels have similar values, their n-link should be strong. Cutting a strong link is expensive, so similar pixels tend to stay together.

### Colour Distributions

User scribbles or selected regions provide foreground and background examples.

From these, estimate:

- P(I | Object)
- P(I | Background)

These probabilities guide t-link weights.

### Min-Cut and Max-Flow

The segmentation is found by solving a min-cut problem.

Min-cut:

- Find the lowest-cost set of links whose removal separates source from target.

Max-flow equivalence:

- Min-cut can be solved through max-flow.

Analogy:

- Links are tubes with capacities.
- Water flows from source to target.
- The bottleneck corresponds to the cut.

Pixels connected to source become foreground. Pixels connected to target become background.

## Common Pitfalls

- Treating point processing and spatial filtering as the same thing.
- Forgetting that linear filters blur edges.
- Using mean filtering for salt-and-pepper noise when median is more suitable.
- Applying a global threshold to an image with non-uniform illumination.
- Ignoring the difference between 4- and 8-connectivity.
- Confusing erosion and dilation.
- Assuming high accuracy means good segmentation under class imbalance.
- Forgetting that Hough Transform gives parameters, not necessarily line endpoints.
- Thinking Canny is just Sobel plus thresholding. Non-maximum suppression and hysteresis are central.

## Quick Revision Checklist

- Define sampling and quantisation.
- Explain histograms and histogram equalisation.
- Compare point processing with spatial filtering.
- Explain convolution and linear filtering.
- Compare mean, Gaussian, median, anisotropic diffusion, and bilateral filtering.
- Explain thresholding and adaptive thresholding.
- Explain connected components and connectivity.
- Define erosion, dilation, opening, and closing.
- Explain first and second derivative edge detection.
- Explain unsharp masking and Laplacian sharpening.
- Describe Canny edge detection step by step.
- Explain the Hough accumulator.
- Compare region growing, split-and-merge, watershed, and superpixels.
- Compute accuracy, precision, recall, F1, IoU, and Dice from TP/FP/FN/TN.
- Explain graph cut segmentation using t-links, n-links, min-cut, and max-flow.
