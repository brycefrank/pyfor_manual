# Introduction

Welcome to the `pyfor` manual. This is a user manual for the Python package for LiDAR data processing called `pyfor` that is used to prepare raw point cloud data for use in forest inventory and monitoring applications, specifically for aerial laser scanning (ALS) data. This manual is written for those with at least a base familiartiy with the Python programming language but I encourage those that are not familiar with the language yet to believe in themselves and give their processing task a shot before looking to other tools. Why? Well, it turns out many things you probably will want to do are likely straightforward using this package. It is designed to offer a mixture of user-friendliness and accesibility to more complex operations if desired.

The following is an example. Let's say we would like to normalize a point cloud, i.e. subtract the underlying ground elevation such that we can reliably measure tree heights:

```{python}
from pyfor.cloud import Cloud

my_cloud = Cloud("data/my_tile.las")
my_cloud.normalize(cell_size=0.5)
```

And we are done. The point cloud, called `my_cloud` was read into memory and normalized (in place) using a required normalization parameters `cell_size` set to 0.5. Simple as that. Of course, things can get a bit more complex, but we will go over those things in the chapters to come.

## What is `pyfor`?

`pyfor` takes raw point cloud information, usually in the form of `.las` files, and converts them into useful information for generating predictions across the forested landscape. If this sounds a bit vague, it is because it is. There are many different routes in point cloud processing, all of which have their applications and merits. `pyfor` attempts to accommodate these tasks in a flexible and accessible way using the Python programming language. `pyfor` does not constrain itself to only LiDAR data. Any remote sensing method that produces point clouds, and can provide a `.las` or `.laz` file are compatible data sources.

## Why Python?

This is an interesting question. I think the most honest answer for me is because I like Python. I enjoy programming in it, and after learning a few other languages, I still keep coming back for more. There are a bunch of other reasons as well. 

- Python is a maintainable and accessible language, and easy to pick up.
- Python has a large backing from the data science and GIS community and, if ever there was a field that is at the intersection of those two things, it is probably ALS research and operations. 
- Python is backed by an incredible number of packages ready for use. 
- The package manager `conda`, although a headache some days, is a reasonable way to gurantee cross-platform compatibility so my tools can be available to Windows, Linux and MacOS users.
- Python offers access to low-level data structures, some of which rival C++ and FORTRAN performance.

Clearly, any language can claim these feats, but I believe Python is a rare bird in that it does all of these things very well.

## Why not Other Tools?

Let's address the elephant in the room. Why not use `lidR` or `FUSION`? To be honest, there is no good reason...at least not yet. So, let me give you my reasons. With respect to `lidR` I think this package is a very great tool, and much more mature than my own. I used it extensively for a few months with very good and operational results. But I am a programmer by nature, and wanted to tack a whack at ALS processing myself and see what I could bring to the Python eco-system. Secondly, I dislike the R programming language outside of statistical analysis. It is a messy beast with a few too many "quirks" for my liking. Thirdly, I think treating ALS processing as an object-oriented system has benefits for maintainability of source code and for the end-user experience. Python does OOP very well and I have never bothered to dive into R's OOP tools. As for `FUSION`, the tool is Windows exclusive and I do the bulk of my work in a Linux environment. `FUSION` is the TI-84 of the ALS processing toolset. A bit old by modern standards but damn if it isn't reliable (and fast due to its, I believe, FORTRAN-based source code).

## What does this Manual Cover?

This manual covers a variety of use cases for `pyfor` in great detail and is meant to expand on the samples found in the GitHub repository for the package. Think of this manual as a superset of those samples. In addition, I will connect the functions, objects and algorithms implemented in `pyfor` to the aerial laser scanning (ALS) literature. And, because my writing is so often neutered in the academic setting, will freely interject opinions and other thoughts in an attempt to make this project a fun, casual read for the ALS enthusiast in all of us.




