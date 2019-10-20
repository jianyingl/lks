# VFS
VFS is a layer between system call and the various real file systems. The VFS hides the difference of each file system by providing a common file model. That makes the upper application unchanged when the underlying file system changes.

### Four main objects in the common file model: superblock, dentries, inodes, files

Access to a filesystem starts by mounting it. This operation takes a filesystem type (like ext2, vfat, iso9660, nfs) and a device and produces the in-core superblock that contains the information required for operations on the filesystem; a third ingredient, the mount point, specifies what pathname refers to the root of the filesystem.

The pathname argument that is passed to system calls (e.g. open(), stat(), etc.) is used by the VFS to search through the directory entry cache (also known as the dentry cache or dcache). This provides a very fast look-up mechanism to translate a pathname (filename) into a specific dentry. Dentries live in RAM and are never saved to disc: they exist only for performance.

The kernel keeps track of files using in-core inodes ("index nodes"), usually derived by the low-level filesystem from on-disk inodes.

A file object describes how a process interacts with a file it has opened. The object is
created when the file is opened and consists of a file structure.


NOTE:: For disk based file system, superblock/inode has both in-memory object and on-disk storage. For dentry/file object, both of them are only created in memory.


