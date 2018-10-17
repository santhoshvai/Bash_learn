# Compression & Archiving

### zip / unzip

* Compress and archive (bundle) files into a single file.
* A new compressed .zip file is created and the original files stay intact.
* Many options! E.g., add files to an existing zip, encrypt with a password ..etc

```
zip <zipped file name> <files to compress>
unzip <zipped file name>
```

### gzip

* Compress files using Lempel-Ziv coding.
* Does not bundle files, the compressed files will replace the original files.

```
gzip <file to compress>
gunzip <compressed file>
```

### bzip2

* Compress files using Burrows-Wheeler block sorting text compression algorithm and Huffman coding.
* More efficient than gzip on most files, but a bit slower.
* Like gzip, this is only a compression tool, and thus compressed files will replace the original files.

```
bzip2 <file to compress>
bunzip2 <compressed file>
```

## Tarballs

* To archive multiple files together, we can use the “Tape Archive” utility (tar).
* tar bundles multiple files together into a single file (but does not compress them or replace them)

```
tar -cf archive.tar foo bar
```
Create archive.tar from files foo and bar

```
tar -xf archive.tar
```
Extract all files from archive.tar

### Compressed Tarballs

* To compress a tarball we can pipe the outcome of tar to a tool like gzip or bzip2.

* However, tar has flags to automatically do this:
  * -z : compress using gzip
  * -j : compress using bzip2

```
tar -czf archive.tar.gz foo bar
```
Creates a compressed file (archive.tar.gz) from files foo and bar

Naming convention:

* `archive.tar.gz` or `archive.tgz`: gzipped tarballs
* `archive.tar.bz2` or `archive.tbz`: bzip2 tarballs

**Works with directories too!**

```
tar -czf cs2042.tgz cs2042/*
```
Creates a compressed file containing the directory and contents of cs2042 directory

### A Backup Script

Here is something a little more practical - a simple script to back up all the files in your documents directory:

**Example: backup.sh**

```
#! /bin/bash
tar -czf ∼/backups/cs2042.backup.tar.gz \
∼/Documents/cs2042/
```

This script makes use of the tar archiving command:

Making Tarballs:
```
tar -c(z/j)f <dest_archive> <source>
tar -x(z/j)f <archive>
```

* -c version creates a new archive from a source file/dir
* -x extracts an existing archive to the current dir
* pick either -z or -j options (-z ⇒ .tar.gz , -j ⇒ .tar.bz2)