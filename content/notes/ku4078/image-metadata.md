---
title: "image metadata"
date: 2023-10-06T14:14:00+07:00
authors: ['Sparisoma Viridi']
tags: ['ku4078']
draft: false
math: true
url: "0089"
---
{{< toc >}}


## introduction
+ One type of image metadata is EXIF metadata, where the term stands for Exchangeable Image File Format, whose technology behind it was developed in 1995 by the Japanese Electronic Industries Development Association as a standard format for JPEG and TIFF with current version is 2.3 that has been available since 2010 ([IONOS, 2023](https://www.ionos.com/digitalguide/websites/web-design/what-is-exif-data/)).
+ Almost all nowadays camera manufacturers use EXIF to store information about the captured image, where this information is called metadata which can include camera settings, image metrics, data & time information, location information, thumbnail, description, and copyright information ([Kukil, 2022](https://learnopencv.com/what-is-exif-data-in-images/)).


## removing metadata
+ Image metadata can be removed manually with Windows, using ImageOptim on Mac, using GIMP that supported by several OS, dan using mobile apps ([Arsenault, 2018](https://www.keycdn.com/blog/image-metadata)).


## code
+ There are some JavaScript libraries that can access the Exif data in digital photos, e.g Piexifjs, not only read but also edit and erase it ([deVilla, 2021](https://auth0.com/blog/read-edit-exif-metadata-in-photos-with-javascript/)).
+ Read and remove metdata data form photos can be performed also with Python, e.g. exif package ([deVilla, 2021](https://auth0.com/blog/read-edit-exif-metadata-in-photos-with-python/)).
+ With Java not only Exif metadata can be read, but also IPTC/IIM and XMP metadata ([Hillert, 2022](https://medium.com/@hillert/read-write-image-metadata-with-java-part-1-d5e2057c80d9)).


## notes
+ Kode KU4078 is for Studium Generale course.
+ The Metadata lecture is for 11 Oct 2023 on Faculty of Animal Science, UNJA.
+ Other note(s): [0076](../0076/).