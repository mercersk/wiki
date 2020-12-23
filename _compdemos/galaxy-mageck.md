---
title: MAGeCK on Galaxy
last_modified_at: 2020-12-04
main_author: Kate Hertweck
primary_reviewers: k8hertweck
---

This demo walks through the process of preparing sequence data
to be analyzed with [MAGeCK](https://sourceforge.net/projects/mageck/),
which identifies important genes from genome screens from 
CRISPR-Cas9 knockouts.
It combines instructions from [this MAGeCK tutorial](https://sourceforge.net/p/mageck/wiki/Home/#the-third-tutorial-going-through-a-public-crisprcas9-screening-dataset)
with information from the Hutch's customizable,
[on-premise Galaxy tool](/compdemos/galaxy-on-prem/).

## Getting set up

Prior to starting this tutorial,
you need to have already [logged on to `rhino`](/compdemos/first_rhino/)
and [created a Galaxy instance](/compdemos/galaxy-on-prem/#creating-your-first-galaxy-instance).

## Installing MAGeCK

While a few common tools come pre-installed in your new Galaxy instance,
we first need to install the specific software we'll be using,
`MAGeCK count`.
Follow the [instructions to install software on Galaxy](/compdemos/galaxy-on-prem/#installing-software),
searching for "MAGeCK count".
You may choose to create a new section called MAGeCK if desired.

## Uploading data

-	upload data (Upload data, from URL)
    -	ftp://ftp.sra.ebi.ac.uk/vol1/fastq/ERR376/ERR376998/ERR376998.fastq.gz
    -	ftp://ftp.sra.ebi.ac.uk/vol1/fastq/ERR376/ERR376999/ERR376999.fastq.gz
    - https://sourceforge.net/projects/mageck/files/libraries/yusa_library.csv.zip

The first two files are experimental (`fastq`) files;
the third is the library file.
If the library file doesn't upload appropriately,
download the file to your local computer,
unzip, and upload from there.

Convert file format of experimental data: for both ERR files
(FIXME: check if this is necessary)
- Click on edit (pencil) icon
- Convert tab
- Select option in dropdown menu: “convert compressed to uncompressed”

Run MAGeCK count
- Click on tool in lefthand sidebar
- Appropriate data will be autodetected: highlight appropriate data in “Sample reads” section (fastq files)
- Scroll down and select “execute”
- Download results
- Click the title of the box in righthand sidebar for the MAGeCK output.
- Click the Save icon in the summary below to save results to your computer
- FIXME: normalization (in Options menu)
