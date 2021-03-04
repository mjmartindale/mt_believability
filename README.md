# Machine Translation Believability

This package contains data files with MT outputs for the test portion of the MTTT task and 
human annotation scores for believability, fluency, and adequacy.

## Annotation File Naming Conventions

The package contains two sets of annotation files for each type of annotation for each MT system: a summary file containing the official final 
segment scores (mean zscore and binary label) and annotation files with all the raw annotator scores and zscores (normalized per annotator).

The score files are named as follows under the 'annotations' directory for the appropriate language pair:

* {langpair}.{annotype}.csv - summary file
* {langpair}.{annotype}.annot.{scoretype}.csv - annotator score files

Where:

* langpair = Language pair
* annotype = Type of annotation
* scoretype = raw or z (for zscores)

### Systems 

In version 1.1, the only systems tested were 'general-rm1' for Arabic to English (ar-en), Farsi to English (fa-en) and Korean to English (ko-en)

### Annotation Types
* ad: Standard adequacy question
* bl: Believability (i.e., without source or reference, how likely is it that the meaning is correct?)
* fl: Standard fluency question

### Score Types
* raw: average of raw scores
* zscore: scores converted to zscore per annotator then averaged

## Score file format

Each score file is a csv file with the following fields:
* SEGID - The (one-indexed) line of the text that is being evaluated
* LANGPAIR - The language pair for this MT output (redundant information for sanity check)
* ANNOTYPE - Annotation type (redundant information for sanity check)
* BINLABEL - Binary label ('True' or 'False')
* MEANSCORE - Mean zscore for that segment
* NUMANNOT - Number of annotations averaged in this score

## Annotation file format

Each score file is a csv file with the following fields:
* SEGID - The (one-indexed) line of the text that is being evaluated
* LANGPAIR - The language pair for this MT output (redundant information for sanity check)
* ANNOTYPE - Annotation type (redundant information for sanity check)
* NUMANNOT - The number of annotations
* ANNOTATOR_01 ... ANNOTATOR_N - Score for this segment by this annotator (or 'nan' if this annotator did not score this segment)

It is recommended that these files be read in via pandas.read_csv

## Text Files

The following text is provided for reference in text:
* mt_output/{languagepair}.{system}.tok.en = Output of the MT system
* test/ted_test1_en-{ar,fa,ko}.{raw,tok}.{ar,fa,ko} = Source text from MTTT provided for convenience
* test/ted_test1.{raw,tok}.en = Original English (same for all language pairs)

## Paper

Link to paper and citation forthcoming.

## Fine print
This data set is publicly available for use under Creative Commons CC-BY.

Version: 1.1
