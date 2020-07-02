# Cmpe 352 Final Exam - Spring 2020 (13:40 - 15:00)

### HONOR CODE

```diff
- By submitting this exam I agree that:
+ I am a student at Bogazici University and registered for Cmpe352 during the 2020 Spring semester. 
+ The answers I am submitting for the Cmpe352 exam are exclusively my own answers.
+ I have prepared these answers individually without the assistance of anyone else whatsoever.
+ I have not provided any assistance to anyone during this exam.
```

*Name*:

*ID*:

*Group No*:

## New Requirement

A new feature for the user to tag their posts  (Product or Project - according to your Cmpe352 group project) 
with information from _Internet Archive_ is requested.
The [Internet Archive](https://archive.org) is a digital library of Internet sites and other digital cultural artifacts. 
It aims to provide researchers, historians, scholars, and the general public access to knowledge.
It provides many APIs towards this end. Brief examples are given below, but you should inspect the APIs.

*  [advanced search endpoint](https://archive.org/advancedsearch.php) to search for items in the archive

<details><summary>Example for the query Donald Knuth (click to expand)</summary>
<p>
    
```json
{
    "responseHeader": {
        "status": 0,
        "QTime": 99,
        "params": {
            "query": "(title:Donald^100 OR description:Donald^15 OR collection:Donald^10 OR language:Donald^10 OR text:Donald^1) (title:Knuth^100 OR description:Knuth^15 OR collection:Knuth^10 OR language:Knuth^10 OR text:Knuth^1)",
            "qin": "Donald Knuth",
            "fields": "identifier,publicdate,publisher,title",
            "wt": "json",
            "sort": "createdate",
            "rows": "50",
            "start": 0
        }
    },
    "response": {
        "numFound": 228,
        "start": 0,
        "docs": [
            {
                "identifier": "isbn_9780387979922",
                "publicdate": "2015-08-04T15:41:02Z",
                "publisher": "New York : Copernicus",
                "title": "Out of their minds : the lives and discoveries of 15 great computer scientists"
            },
            {
                "identifier": "TeX_CD-ROM_July_1995_Disc_2_Walnut_Creek_1995",
                "publicdate": "2017-10-16T19:11:50Z",
                "title": "TeX CD ROM July 1995 (Disc 2)(Walnut Creek)(1995)"
            },
```
    
</p>
</details>

* [item metadata](http://archive.org/metadata/) to get details of items.

<details><summary>Example of the data to be processed if the query was Adidas and the chosen identifier was `Impossible_Is_Nothing` </summary>
<p>
    
```json
{
    "created": 1593335222,
    "d1": "ia902606.us.archive.org",
    "d2": "ia802606.us.archive.org",
    "dir": "/25/items/Impossible_Is_Nothing",
    "files": [
        {
            "name": "02-04_Jonah_30_Final-cut.gif",
            "source": "derivative",
            "format": "Animated GIF",
            "original": "02-04_Jonah_30_Final-cut.mov",
            "md5": "2de94a7d02234595d14efd4a16c2150e",
            "mtime": "1227674958",
            "size": "68843",
            "crc32": "f756fdc8",
            "sha1": "7336973def018b4b05a007d362a13d5da37a9577"
        }
```

</p>
</details>

## Requirement

**TODO (6 points)**: Write the requirements related to this newly requested functionality (using wiki).


## Issue

**TODO (6 points)**: Create two *significant* issues related to the new requirement.

## Design

### Class Diagram

Revise your class diagram to add the variable  `tagList`  to your posts and an  `addTag`  method. 
Also, add a new class called ArchiveItems to represent the identifier, title, date, and media associated with the archive item.
This class should also have the methods `fetch_archive_information` to search for items given a user query and `fetch_information`  to get information about the  items.

**TODO (6 points)**: Draw the relevant classes and upload the source file and the exported image (.png or .jpg format) under *diagrams* folder in this repository (do not forget to highlight/color the newly added parts of your class diagram). 

### Sequence Diagram

Draw the sequence diagram for a user to tag a post with an item from the Internet Archive. Tagging means that user will search for an item within the archive.
If there are any matches the item list will be shown to the user. If the user finds an item they like, they will select one to tag the post (using addTag method). 
Use the described methods to perform the archive search and getting item information method to tag the item.

**TODO (12 points)**: Draw the sequence diagram and upload the source file and the exported image (.png or .jpg format) under *diagrams* folder in this repository.

## Implementation

Use the following endpoints:

* [advanced search endpoint](https://archive.org/advancedsearch.php)
* [item metadata](http://archive.org/metadata/)

to perform the following actions:

1. Fetch a list of *identifiers, titles, publishers, and publicdates* for a given query using [advanced search endpoint](https://archive.org/advancedsearch.php).
 If there is no match for the query it should return status 407.
 
**TODO (9 points)**: Write the `fetch_archive_information` method under this repository.

2. Allow a user to choose an item from a list of archive items. 
Then fetch information about this item to retrieve files of media type of `Thumbnail`, `Ogg Video` or `Animated GIF` using  [item metadata](http://archive.org/metadata/).

**TODO (9 points)**: Write the `fetch_information` method under this repository.

### Unit tests

**TODO (12 points)**: Write the necessary unit tests for the `fetch_archive_information` function. Your unit tests must cover functionality as well as exception handling.

**IMPORTANT NOTE**: All of your commits should be available at the master branch before the deadline.
