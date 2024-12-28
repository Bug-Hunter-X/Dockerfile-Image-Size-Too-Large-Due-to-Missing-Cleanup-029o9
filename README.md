# Dockerfile Bug: Image Size Optimization

This repository demonstrates a common issue with Dockerfiles: neglecting to clean up temporary files after package installation. This leads to unnecessarily large image sizes and potential dependency conflicts.

## Problem

The original `Dockerfile` installs Python and dependencies but fails to remove the downloaded packages using `apt-get clean`. This results in a much larger image than necessary.

## Solution

The `Dockerfile_fixed` shows the corrected `Dockerfile` that includes the `apt-get clean` command after the installation step. This significantly reduces the image size and improves build efficiency.

## How to Reproduce

1.  Clone this repository.
2.  Build the original Dockerfile: `docker build -t large-image -f Dockerfile .`
3.  Build the fixed Dockerfile: `docker build -t small-image -f Dockerfile_fixed .`
4.  Compare the image sizes using `docker images`.

You will observe a considerable difference in size between the two images.  The `small-image` will be significantly smaller due to the cleanup command.
