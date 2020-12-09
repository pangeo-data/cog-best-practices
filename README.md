# cog-best-practices
Best practices with cloud-optimized-geotiffs (COGs)

**The goal of this repository is to determine best practices for accessing the increasing amount of COG data with Pangeo tooling (GDAL, Rasterio, Xarray, Dask).** 

A Cloud Optimized GeoTIFF (COG) is a regular GeoTIFF file, aimed at being hosted on a HTTP file server (or Cloud object storage like S3), with an internal organization that enables more efficient workflows on the cloud. It does this by leveraging the ability of clients issuing HTTP GET range requests to ask for just the parts of a file they need. Read more at https://www.cogeo.org 

One great use-case of COGS is downloading small pieces of a big file to your laptop. Another use-case is accessing COGs from within the same datacenter where they are stored over very efficient network connections.

This repository focuses on distributed computing within the same datacenter using this great new AWS public dataset in us-west-2 https://registry.opendata.aws/sentinel-1/ (Sentinel-1 Synthetic Aperture Radar images covering the United States).

### Computing environment

We can use [Pangeo Cloud](https://pangeo.io/cloud.html) and [Pangeo Binder](https://aws-uswest2-binder.pangeo.io) on AWS us-west-2 to iterate on examples in a common computing environment, click the button below to run the notebooks in this repository interactivel via Pangeo Binder on AWS:

[![badge](https://img.shields.io/static/v1.svg?logo=Jupyter&label=PangeoBinderAWS&message=us-west-2&color=orange)](https://aws-uswest2-binder.pangeo.io/v2/gh/pangeo-data/notebook-binder/2020.12.08?urlpath=git-pull%3Frepo%3Dhttps%253A%252F%252Fgithub.com%252Fpangeo-data%252Fcog-best-practices%26urlpath%3Dlab%252Ftree%252Fcog-best-practices%252F%26branch%3Dmain) 


#### Organization

For starters there are four notebooks in this repository with the following focus:

1. Accessing a single COG
2. Working with multiple COGs (concatenated in time)
3. Dask LocalCluster
4. Dask GatewayCluster

Unit tests and examples often are simplified to an extreme and consequently fail to translate to ‘real world examples’. At the other extreme, full scientific analysis or large-scale computations are complex and difficult to follow. The goal with these examples is to explore the middle ground - simple operations that are commonplace on ~10-1000GB datasets.


#### Goals

1. Figure out ways to improve these notebooks for better efficiency and clarity (this might involve opening issues and pull requests in other projects)
2. Add new notebooks for common workflows
    e.g. creating COGs, rechunking COGs, applying custom functions, reprojection...
