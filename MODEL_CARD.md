ECGMatcher Model Card
1. Model Name
Multi-Lead Morphological Matching for ECG Image Abnormality Screening
Recommended model-weight filename: `ecgmatcher_step1_curve_segmentation_best.pth`
Software version: ECGMatcher v1.0.0
Release format: Protected portable edition for 64-bit Windows
Task: ECG curve reconstruction and semantic segmentation, followed by multi-lead morphological matching
2. Intended Use
The model is designed to extract thin ECG waveform traces with a low foreground-to-background ratio from reconstructed ECG images. The resulting foreground masks are used for subsequent contour alignment, key-waveform comparison, similarity assessment, and abnormality localization.
The model is not a disease classifier and does not directly generate disease labels, etiologic interpretations, treatment recommendations, or clinical diagnoses.
3. Model Design Overview
ECGMatcher is specifically designed to address the structural characteristics of ECG traces, including their elongated morphology, low foreground occupancy, and pronounced amplitude transitions within QRS complexes. The model incorporates:
directional thin-line enhancement;
waveform-structure consistency constraints;
curve-structure prior fusion;
completion of weak-response regions; and
centerline positional-stability constraints.
The model is intended to preserve the continuity and clinically relevant morphology of authentic ECG traces while suppressing false-positive background responses.
4. Training and Experimental Settings
The principal training settings reported in the current manuscript are summarized below:
| Setting                     | Value                |
| --------------------------- | -------------------- |
| Input size                  | 640 × 640            |
| Batch size                  | 2                    |
| Number of training epochs   | 80                   |
| Optimizer                   | AdamW                |
| Initial learning rate       | 6 × 10⁻⁵             |
| Weight decay                | 1 × 10⁻²             |
| Random seed                 | 42                   |
| Training framework          | PyTorch              |
| Target software environment | 64-bit Windows 10/11 |
5. Datasets
LUDB
Contains 200 standard 12-lead ECG recordings.
Provides expert annotations of P-wave, QRS-complex, and T-wave boundaries.
Used for ECG signal reconstruction, curve segmentation, and key-waveform morphological comparison.
PTB-XL
A large-scale clinical 12-lead ECG database.
The current study uses 2,203 recordings for model training and testing.
Includes comprehensive diagnostic, rhythm, and morphological annotations.
Used to evaluate model adaptability across heterogeneous clinical ECG recordings.
The original datasets are not redistributed with this software. Users must obtain them from their official sources and comply with the corresponding licensing and citation requirements.
6. Intended Applications
The model is intended for:
research on the reuse of image-based ECG records;
ECG curve reconstruction and segmentation experiments;
multi-lead morphological consistency analysis;
lead-level and waveform-segment-level abnormality screening;
verification of results reported in academic publications; and
non-commercial teaching and algorithm evaluation.
7. Out-of-Scope Applications
The model must not be used directly for:
standalone clinical diagnosis;
automated disease-classification conclusions;
emergency triage or urgent medical management;
medication or treatment decision-making;
unvalidated population-screening programs;
medical-device deployment without regulatory approval; or
commercial clinical services.
8. Ethics and Privacy
Only data for which the user has lawful authorization should be processed.
All patient-identifying information must be removed before public disclosure.
The use of clinical data must comply with applicable ethical-review and informed-consent requirements.
Patient CSV files, case identifiers, runtime logs, and screenshots must not be uploaded directly to public repositories.
9. License
The model weights and original ECGMatcher components are governed by the research, education, and non-commercial evaluation license provided in `LICENSE.txt`. Third-party frameworks and libraries remain subject to their respective licenses.

