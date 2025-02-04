This directory contains several fixes:

1. ImageRegisteryFix.reg  changes a value in the Windows Registery that prevents the "Loading Image" dialog from showing each time Access loads an image file. This not only speeds up image loading, it also prevents Access from crashing when quickly moving from one record to the next.

2. On some systems the comdlg32.ocx file is not installed. Access will show an error message whenever you open a form. On a 32bit Windows copy the file to: C:\Windows\system32\. After that register it with the file InstallComdlg32.bat. On a 64bit Windows copy it to C:\Windows\SysWOW64. After that register it with the file InstallComdlg64.bat.

3. Max Locks per File fix: For certain processing commands Access will produce an error when the number of records is large. This fix will increase the maximum value in the Registery.


4. Reconyx Hyperfire EXIF data fix: The Reconyx Hyperfire cameras don't store the date and time in the standard EXIF format. Instead they store that information in the Maker Notes. Fortunately there is an easy way to copy the DateTime information from the MakerNote to the actual EXIF DateTime field using Phil Harvey's ExifTool ( http://www.sno.phy.queensu.ca/~phil/exiftool/). Here the command that will process all images in all subdirectories of a given directory (replace DIR with the path of the directory containing all image directories):

exiftool "-DateTimeOriginal>DateTimeOriginal" -r -overwrite_original -ext .JPG DIR 

The EXIFTool is included in the Fixes folder. The EXIFTool can also batch extract EXIF data. 

Easy steps to apply this fix to all of your images:

1.	Copy the exiftool.exe and FixHyerfire.bat files into the directory where your images are (they can be in subdirectories). So if your images are in C:\Images\Camera1, C:\Images\Camera2 etc. copy it to C:\Images.
2.	Run the FixHyperfire.bat by double-clicking on it. This will update all the images in the directory and all subdirectories.
