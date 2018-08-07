Data download link:
https://drive.google.com/open?id=0Bz-jINrxV740SWE1UjR4RXFKRm8


Data
For this challenge, we use the publicly available LIDC/IDRI database. This data uses the Creative Commons Attribution 3.0 Unported License. We excluded scans with a slice thickness greater than 2.5 mm. In total, 888 CT scans are included. The LIDC/IDRI database also contains annotations which were collected during a two-phase annotation process using 4 experienced radiologists. Each radiologist marked lesions they identified as non-nodule, nodule < 3 mm, and nodules >= 3 mm. See this publication for the details of the annotation process. The reference standard of our challenge consists of all nodules >= 3 mm accepted by at least 3 out of 4 radiologists. Annotations that are not included in the reference standard (non-nodules, nodules < 3 mm, and nodules annotated by only 1 or 2 radiologists) are referred as irrelevant findings. The list of irrelevant findings is provided inside the evaluation script package (annotations_excluded.csv).

Data is available on the download page. The data is structured as follows:

subset0.zip to subset9.zip: 10 zip files which contain all CT images
annotations.csv: csv file that contains the annotations used as reference standard for the 'nodule detection' track
sampleSubmission.csv: an example of a submission file in the correct format
candidates_V2.csv: csv file that contains the candidate locations for the ‘false positive reduction’ track
Additional data includes:

evaluation script: the evaluation script that is used in the LUNA16 framework
lung segmentation: a directory that contains the lung segmentation for CT images computed using automatic algorithms
additional_annotations.csv: csv file that contain additional nodule annotations from our observer study. The file will be available soon
Note: The dataset is used for both training and testing dataset. To allow easier reproducibility, please use the given subsets for training the algorithm for 10-folds cross-validation.

Images
The complete dataset is divided into 10 subsets that should be used for the 10-fold cross-validation. All subsets are available as compressed zip files.

In each subset, CT images are stored in MetaImage (mhd/raw) format. Each .mhd file is stored with a separate .raw binary file for the pixeldata. You can read a preliminary tutorial on how to handle, open and visualize .mhd images on the Forum page. A detailed tutorial on how to read .mhd images will be available soon on the same Forum page.

Annotations
The annotation file is a csv file that contains one finding per line. Each line holds the SeriesInstanceUID of the scan, the x, y, and z position of each finding in world coordinates; and the corresponding diameter in mm. The annotation file contains 1186 nodules.

Candidates
The candidates file is a csv file that contains nodule candidate per line. Each line holds the scan name, the x, y, and z position of each candidate in world coordinates, and the corresponding class. The list of candidates is provided for participants who are following the ‘false positive reduction’ track. Tutorial on how to view lesions given the location of candidates will be available on the Forum page.

The candidate locations are computed using three existing candidate detection algorithms [1-3]. As lesions can be detected by multiple candidates, those that are located <= 5 mm are merged. Using this method, 1120 out of 1186 nodules are detected with 551,065 candidates. For convenience, the corresponding class label (0 for non-nodule and 1 for nodule) for each candidate is provided in the list. It has to be noted that there can be multiple candidates per nodule.

After ISBI 2016, we have decided to release a new set of candidates for the false positive reduction track. This updated set is obtained by merging the previous candidates with the ones from the full CAD systems etrocad (jefvdmb2) and M5LCADThreshold0.3 (atraverso). The new combined set achieves a substantially higher detection sensitivity (1,166/1,186 nodules), offering the participants in the false positive reduction track the possibility to further improve the overall performance of their submissions.

Lung segmentation
To aid the development of the nodule detection algorithm, lung segmentation images computed using automatic segmentation algorithm [4] are provided. The lung segmentation images are not intended to be used as the reference standard for any segmentation study.

DICOM images
An alternative format for the CT data is DICOM (.dcm). You can read a preliminary tutorial on how to handle, open and visualize .dcm  images on the Forum page. The original DICOM files for LIDC-IDRI images can be downloaded from the LIDC-IDRI website.
