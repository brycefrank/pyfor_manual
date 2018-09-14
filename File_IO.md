---
output:
  pdf_document: default
  html_document: default
---
# File I/O

File input is step one of ALS analysis in any context. Especially important is learning what data to import from your local files. `pyfor` relies specifically on `laspy`, another useful Python package that is used to read the information from `.las` files. This chapter will go over the basics of how `.las` files are structured and read into Python, and how to properly and efficiently manage the wealth of information contained in these files.

## laspy

LAS files come in an array of different versions, and it is important to know which specification your las file is so you know what kind of information you can extract from it. As of the writing of this chapter the most recent LAS specification is 1.4, released in July, 2013. You can read the contents of the 1.4 specification [here](http://www.asprs.org/wp-content/uploads/2010/12/LAS_1_4_r13.pdf). LAS specifications are generally dry, technical documents that define the structure of the LAS file itself, and defines this structure such that low-level programmers can efficiently read the LAS file using their programs.

Fortunately for us Python users, someone has already done all of this hard work for us, and that work is called [laspy](https://github.com/laspy/laspy). `laspy` has been around for several years and is an actively maintained open source LAS I/O package for Python.

### Reading the Cloud

The first question most analysts want to answer is: how do I read a point cloud from a LAS file? Using laspy, this answer is almost trivial. The following is an example:

```{python}
import laspy
my_las = laspy.file.File("my_las.las")
```

These two lines achieve two things. First, we import `laspy` into the Python namespace, then we create a pointer to a `.las` file by instantiating a `laspy.file.File` object. Note that **this is a pointer only**, we have yet to read any data into memory by creating this pointer. This is an important distinction for memory management when doing large analyses.

If we wish to read actualy point cloud data into memory, we can retrieve the `points` attribute of the pointer.

