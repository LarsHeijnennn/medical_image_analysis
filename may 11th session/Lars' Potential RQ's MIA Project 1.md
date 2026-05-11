
---
### RQ 1
RQ 1: How does the choice of similarity metric affect affine intensity-based registration accuracy for intra-modal versus inter-modal MR brain registration?

this is about comparing two ways of measuring whether two images are well aligned. - Registration is the process of aligning two or more images.
- Images are rarely aligned perfectly because of:
	- Patient movement between scans.
	- Use of different modalities (e.g., MRI and CT).
	- Scans taken at different time points (e.g., before and after treatment).
	- Comparisons across different patients.

A similarity metric is a score used by the registration algorithm to decide whether one alignment is better than another. We could compare with:
- Normalized cross-correlation --> works well when images have similar intensity patterns
- Mutual information --> often better when images come from different modalities. 

Then, we would test this for: 
- Intra-modal registration: registering images from the same modality, such as T1-to-T1.
- Inter-modal registration: registering images from different modalities, such as T2-to-T1.

The goal is to see whether normalized cross-correlation is better for T1-to-T1, and whether mutual information is better for T2-to-T1.

---
### RQ 2
RQ 2: Does affine registration improve alignment compared to rigid registration for transformed T1 brain images?

This RQ is about whether a more flexible transformation model gives better registration results. A transformation model describes what kinds of changes the algorithm is allowed to make to the moving image. The moving image is the image that is actively being being transformed, shifted, rotated, or warped to match a target.

For this RQ, we compare:
- Rigid registration in which the image can only rotate and shift. Shape and size stay the same. 
- Affine registration in which the image can rotate, shift, scale, and shear. This approach is more flexible. 

We would test this on T1 to T1 registration, for example registering t1 d.tif back to  t1.tif. The d image is a transformed version of the original T1 image. The goal is to see whether affine registration gives better alignment than rigid registration, especially if the simulated transformation includes scaling or shearing.

---
### Important definitions

- **Image Registration:** The process of aligning two images so anatomical structures overlap perfectly.
- **Fixed Image:** The reference image that stays stationary during the process.
- **Moving Image:** The image being transformed (shifted, rotated, or scaled) to match the fixed image.
- **Intra-Modal Registration:** Alignment between images of the same type (e.g., T1 to T1).
- **Inter-Modal Registration:** Alignment between different types of images (e.g., MRI T2 to MRI T1).
- **T1 and T2-FLAIR:** Specific MRI sequences that highlight different tissue properties but share the same anatomy.
- **Transformation Model:** The mathematical framework defining how the moving image is allowed to change.
- **Rigid Transformation:** A simple model allowing only rotation and translation; shape and size are preserved.
- **Affine Transformation:** A model allowing rotation, translation, scaling, and shearing for extra flexibility.
- **Similarity Metric:** A mathematical score used to determine how well two images are currently aligned.
- **Normalized Cross-Correlation:** A metric that compares intensity patterns; best for same-modality images.
- **Mutual Information:** A statistical metric that assesses shared information; the "gold standard" for different-modality images.
- **Point-Based Registration:** Alignment based on specific, manually selected landmark points in both images.
- **Intensity-Based Registration:** Alignment calculated automatically using the pixel/voxel values of the images.
- **Control Points / Landmarks:** Specific anatomical locations used as anchors to guide the registration.
- **Registration Error:** The distance between where a point is and where it _should_ be after alignment.
- **Target Registration Error:** Error measured using "hidden" validation points not used to create the transformation.
- **Convergence:** The point where the algorithm finds the best match and stops making changes.
- **Learning Rate:** A setting that determines the size of the steps the algorithm takes toward the solution.
- **Optimization:** The iterative search for the best transformation parameters to maximize similarity.
- **Shearing:** A slanting or "leaning" deformation; part of the affine model but rare in actual brain motion.
- **Degrees of Freedom:** The number of independent variables (like X-shift or Y-rotation) the model can adjust.