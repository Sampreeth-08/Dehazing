# Single Image Dehazing

This project implements a method for removing haze from single input images. It estimates transmission maps and recovers haze-free scene radiance using a dark channel prior approach.

## Algorithm Overview

-**Dark Channel Computation:** Compute the dark channel of the input hazy image, which observes pixels with very low intensity in at least one color channel.

-**Initial Transmission Estimation:** Estimate the initial transmission map using the dark channel prior and haze imaging model.

-**Transmission Refinement:** Refine the transmission map using guided filter to smooth estimates while preserving edges.

-**Atmospheric Light Estimation:** Estimate atmospheric light color from the haze image.

-**Scene Radiance Recovery:** Recover haze-free scene radiance using the refined transmission map and estimated atmospheric light.

-**Output Dehazed Image:** Output the final recovered haze-free image.

<div align="center">
<img src="images/Model structure.jpg" width="70%" />
</div>

## Detailed Implementation

-**DarkChannel.py:** Computes the dark channel of the input image using a sliding window approach.

-**tp.py:** Estimates the initial transmission map by combining the dark channel prior with the haze imaging model.

-**transmissionEstimate.py:** Refines the transmission map using a guided filter to smooth estimates while preserving edges.

-**atmLight.py:** Estimates the atmospheric light color from the brightest pixels in the dark channel.

-**getRadiance.py:** Recovers the haze-free scene radiance using the refined transmission map and estimated atmospheric light.

-**haze_test.py:** Runs the full dehazing pipeline on sample images and outputs results.

## Results and Evaluation

Example results show the method effectively removes haze even in dense scenes. Quantitative metrics in darkChannel_eval.py evaluate the dark channel prior on test images.

<div align="center">
<img src="images/Result1.jpg" width="70%" />
</div>

<div align="center">
<img src="images/Result2.jpg" width="70%" />
</div>

<table>
<tbody>
<tr>
<td>Metric</td>
<td>Value</td>
</tr>
<tr>
<td>
<p>MSE</p>
</td>
<td>0.014999</td>
</tr>
<tr>
<td>SSIM</td>
<td>0.93180</td>
</tr>
<tr>
<td>PSNR</td>
<td>22.8285</td>
</tr>
</tbody>
</table>