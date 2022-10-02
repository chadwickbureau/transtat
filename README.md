Transcriptions of statistics tables from printed sources

### General description

This repository contains data for baseball minor leagues which has been transcribed (or otherwise extracted)
from printed sources.

What these files accomplish is to get the information that is in those sources into an electronic and
structured form for further processing.  See below for notes and caveats.


### Data format

We use YAML as the representation of the data records.  We like YAML (compared to, say, JSON) because it
is somewhat easier for humans to read and, where necessary, to edit.  It also plays very well with
version control.  Although the raw data in printed sources is immutuable, nevertheless errors do happen
in the transcription or extraction processes, and so being able to version the data easily and
transparently is quite valuable.

Most of the data in this repository comes from tabular-based sources, such as statistical compilations
of statistics for a league.  Each table corresponds to a single YAML file, which is a list of records.
In such a case, each record corresponds to one row of the table.  The records in the same file, therefore,
can all be interepreted the same way (for example, a file named batting.yml is going to contain a list of
records which are batting statistics from a table).

All data are always represented as strings. This is quite useful for representing percentages, as the files
contain the percentages to the same number of decimal places as in the source.  Likewise, fractional innings
pitched are usefully represented this way (so we can reliably distinguish between records which have rounded
innings pitched, versus a pitcher who pitched an exact integer number of innings).  It is true that other count
data could be represented as integers, but our experience is that it is useful to treat all data as strings
of characters, and do the conversion to numbers further down our processing pipeline.

In creating the records, we attempt as much as possible to retain the structure of the original source.
For example, the columns in a record will appear in the same order as they appear in the source, and the
rows (records) likewise are in the same order as in the source.  This makes it easy to cross-check
visually information against the original source.  We only do some light standardisation, for example, to
use the same abbreviation for a category irrespective of the abbreviation used in the source.


### Data quality and editing

It is important to bear in mind that, in general, **the data in this repository are the data as they appear in
the source**, and that, **there are many errors and inconsistencies in sources**!.  This is not a cleaned and
edited dataset; it is the raw content of the sources.

Personal names are rendered as they appear in the sources.  They are generally reliable for trying to identify
the person being referenced, but they are far from a reliable guide for a person's correct name.

In the case in which there is *internally inconsistent* data, we do indicate in the records places in which
we have made amendments.  For example, in the case in which a record quotes a batting average which is not
equal to hits divided by at bats, we *may* indicate a recommended amendment in a case in which there is a clear
typo.  We do this conservatively, and in all cases we also indicate the original value as well for transparency.
We do not however in general enforce consistency across different records.  For example, it is not uncommon
for a pitcher's games pitched to be different from their games fielded at pitcher, or for their games pitched
to exceed their games played from a batting table.  We do not make such amendments at the level of this data,
again leaving it to downstream steps in a data processing pipeline to make editorial judgments about which
data to keep.


### Licensing and use

This repository is maintained by Chadwick Baseball Bureau for the benefit of the community.  It has been made
possible by the diligent work of dozens of contributors over the years who have created this data.


### Contributing

If you are interested in contributing to creating transcriptions, please contact us on ted.turocy@gmail.com.



