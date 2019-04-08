# Dicom_Utilities
Various utilities created to help with the interpretation of dicom images/RT Structures

RT Structure and dicom conversion to numpy arrays

This code is designed to receive an input path to a folder which contains both dicom images and a single RT structure file

For example, assume a folder exists with dicom files and an RT structure located at 'C:\users\brianmanderson\Patient_1\CT1\' with the roi 'Liver'

The performed action would be Dicom_Image = DicomImagestoData(path='C:\users\brianmanderson\Patient_1\CT1\',Contour_Names=['Liver'])

Assume there are 100 images, the generated data will be:
Dicom_Image.ArrayDicom is the image numpy array in the format [# images, rows, cols]
Dicom_Image.mask is the mask array with format [# images, rows, cols, contours]

So for the above example the mask will be [100, 512, 512, 1]

If there are two rois ['Liver','Ablation Zone'], the mask will be [100, 512, 512, 2] with the first mask being 'Liver'

from Image_Array_And_Mask_From_Dicom import DicomImagestoData

Path = 'C:\users\brianmanderson\Patient_1\CT1\'
Contour_Names = ['Liver']

DicomImage = DicomImagestoData(path=Path,Contour_Names=Contour_Names)

Image_Array = DicomImage.ArrayDicom
mask = DicomImage.mask
