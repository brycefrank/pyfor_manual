# Cloud

The integral unit of `pyfor` are `Cloud` objects. These contain the information of the `.las` file, as well as several methods useful for manipulating and displaying point cloud data. This chapter will provide common use cases of `Cloud` objects.

## Loading a Cloud Object

Loading a `Cloud` into memory is simple:

```{python}
from pyfor.cloud import Cloud

my_cloud = Cloud("my_las.las")
```

What happens when we load a `Cloud` object? Many of the things we discussed in the File I/O chapter. If we were to look at the `pyfor` source code, we would see that when a `Cloud` object is instantiated (i.e. its `__init__` function is called), `laspy` reads the point cloud data into another object called `CloudData` and this object is made accessible through the `Cloud` object.

One might ask, why bother with the `CloudData` object at all? `CloudData` is mainy used as an internal class used to handle las I/O for us. As users we generally do not want to spend our time making sure our header and in-memory las information is up to date after conducting processing tasks. This is the main purpose of `CloudData` and, unless you are really down in the weeds of processing, you can generally let `CloudData` handle the boring stuff for you. We will turn our attention back to the real player, `Cloud`.

## Accessing Raw Points

We access raw points through an attribute of `Cloud` called `las` which is really just a pointer to a `CloudData` object. We then access the points themselves through `points`:

```{python}
print(my_cloud.las.points)
```

If we were to print the type of this object we would see the following:

```{python}
print(type(my_cloud.las.points))

# > pandas.DataFrame
```

For frequent Python users in the audience, this is a familiar face. `pandas.DataFrame`s (dataframes hereafter) are one of the most common data types in Python data analysis, and for good reason. They are highly efficient data structures meant for handling very large numbers of records, such as those found in `.las` files. They also provide a nice, natural way of interacting with data. Once you learn a bit of syntax, you can do very powerful things just through manipulating the `my_cloud.las.points` object. In fact, much of `pyfor`'s functionality is simply wrapping these manipulations into convenient names.

Let's say we want to filter out all points below a given threshold, say 10 meters. This is a routine operation for dataframes:

```{python}
below_10_bool = my_cloud.las.points["z"] < 10
my_cloud.las.points = my_cloud.las.points[below_10_bool,:]
```
The first line creates a boolean vector such that any z value less than 10 is marked `True`, otherwise it is marked `False`. This vector is of the same length as our `my_cloud.las.points` dataframe. Thus, we can use it to subset our points in the second la=ine. `my_cloud.las.points[below_10_bool,:]` uses this boolean to select all rows that are `True` and all columns (using `:` to get all columns). This is all we need to do to "filter" points out less than 10 meters.


