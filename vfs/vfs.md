# VFS

#### Four main objects: superblock, dentries, inodes, files

The kernel keeps track of files using in-core inodes ("index nodes"), usually derived by the low-level filesystem from on-disk inodes.
A file may have several names, and there is a layer of dentries ("directory entries") that represent pathnames, speeding up the lookup operation.
Several processes may have the same file open for reading or writing, and file structures contain the required information such as the current file position.
Access to a filesystem starts by mounting it. This operation takes a filesystem type (like ext2, vfat, iso9660, nfs) and a device and produces the in-core superblock that contains the information required for operations on the filesystem; a third ingredient, the mount point, specifies what pathname refers to the root of the filesystem.
