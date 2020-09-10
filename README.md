# Bluesky Data Samples

This repository contains samples of data from a range of institutions and
instruments. The data is openly licensed as
[CC0 "public domain"](https://creativecommons.org/share-your-work/public-domain/cc0/).

## Purpose

This data is used by Bluesky Project contributors to:

* Test new software development on realistic workloads
* Verify that changes up and down the software stack do not break access,
  visualization, and processing of existing data (i.e. integration testing)
* Provide ready example data for demos and teaching materials

## How to Use The Data

Much of the sample data includes large array data (images, spectra) which is not
suitable for storing directly with ``git``. This respoitory uses the
[Git Large File Storage ("git lfs") git extension](https://git-lfs.github.com/)
to manage large external files. Only *references* to the large files are stored
in git, and the ``git lfs`` tool is used to download the large files as needed.
See a
[short overview video from GitHub Guides](https://www.youtube.com/watch?v=uLR1RNqJ1Mw)
to learn more. See [git lfs](https://git-lfs.github.com/) for installation and
setup instructions.

In [TOC.md](./TOC.md) you will find an overview of the collections of data
samples. Within each directory under `collections/` you will see a README. To
make a collection "discoverable" on your system by databroker first install
databroker-pack

```
pip install --upgrade databroker-pack
```

and then run

```
databroker-unpack inplace collections/<directory> <directory>
```

or

```
databroker-unpack mongo_normalized collections/<directory> <directory>
```

to copy the documents into MongoDB for better performance.


## How to Contribute Data

Export data using databroker-pack


```
databroker-pack [--uids | --query ] --copy-external --salt="" --strict CATALOG TARGET_PATH
```

Move the packed directory under the ``collections`` directory in this
repository. Ensure that all external formats are registered as "large files" to
be managed by git lfs.

```
git track  # list managed formats
```

```
git track "*.some_extension  # Add a format
git add .gitattributes
```

Commit and push the files.
