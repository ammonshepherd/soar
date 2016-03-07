# The Repository

This directory contains PDF, JPG, and PNG versions of primary source material used in the
dissertation. Footnotes in the dissertation text link to the files in this
directory.

# Metadata

A JSON file contains metadata about each document. 

The Metadata includes:

**FileID**: A generated string to uniquely identify a file. An SHA1 hash made from
name of file, Epoch time, and size at time of creation. Even if the file name,
and size change, the FileID remains the same forever. Ex. "Zsuzsa-Farago.pdf  1453261538 15751744" There is a space between the FileName, Epoch time, and size in bytes. The SHA1 should be created by the following command:

``` 
echo -n Zsuzsa-Farago.pdf `date +%s``wc -c < 'FileName.pdf'` | shasum | awk  '{print toupper($1)}' 
```

The output is not important, just that it is different for each file. This can
be ensured by a number of methods; file name, epoch time at running of script
and file size seem like an unique method to create a unique string.

**Title**: A title or name for the document. Can be the same as the file name.

**Description**: Who and what the document is about.

**Author**: Who created the original primary document. 

**Date**: Date the original primary document was created (not the digital
version). Use the format YYYY-MM-DD, time and time zone are most likely never
needed.

**FileName**: The name of the file. This may change over time, but should always
point to the same FileID.

**URI**: The unique URI to find the file on line. The URL has the format:

`http://nazitunnels.org/repository/FileID.[pdf,jpg,png]`

# Usage

1. Copy the PDF into the directory.
2. Run the script which does
  - Prompt for the FileName, Person, Author, Date
  - Generate the unique FileID
  - Create a new object in the JSON data for the file
  - Output the URI
3. Copy the URI
4. Paste URI in the footnote referencing the document

# Version Control

This directory is kept under version control with Git.
