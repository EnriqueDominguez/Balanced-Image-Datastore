# Balanced-Image-Datastore #
A Matlab datastore class for balanced image data.

## Description ##
Use a BalancedImageDatastore object to manage a balanced collection of image files.
The balanced datastore of image files is created by duplicating the lowest ocurence images from the original image datastore. The new datastore will be composed by *nClasses* \* *maxOccur* observations, where *nClasses* if the number of distinct labels of the original image datastore and *maxOccur* is the count of the most sampled label.

## Syntax ##
> `>> balds = BalancedImageDatastore(imds)`

Input Arguments: 
* `imds` an ImageDatastore object, containing the original image files labelled

Output:
* `balds` a BalancedImageDatastore object

See also [ImageDatastore](https://www.mathworks.com/help/matlab/ref/matlab.io.datastore.imagedatastore.html)

## Properties ##
* `Duplicates` Array of integer, which indicate the number of repetition for the file in the image datastore. `Duplicates(i)==0`when the image *i* is original. `Duplicates(i)==k` when the image *i* is the *k*-th repetition. This information is also included in the structure returned by the `read` method
* `AlternateFileSystemRoots` Alternative file system root path  for the files
* `ReadSize` Upper limit on the number of images returned by the read method
* `NumObservations` Total number of provided images by the datastore. `NumObservtions == NumFiles + NumDuplicates`
* `NumFiles` Number of image files
* `NumDuplicates` Number of duplicate images

## Methods ##
* `read` Read data in datastore
* `readall` Read all data in datastore
* `reset` Reset datastore to initial stage
* `hasdata` Determine if data is available to read
* `shuffle` Shuffle files in datastore
* `partition` Partition a datastore
* `splitEachLabel` Split datastore by proportions
* `countEachLabel` Count image files and their duplicates in datastore

### Requirements ###
The original image datastore must be labelled
