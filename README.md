# music_classification_data

Schema Definition Declaration
===============

The gold standard schema consists of the following 6 schema files:<br/>
- <strong>CueSchema.xsd</strong>: it's the main part of this standard schema. 
The decisions about whether a text music-event related is described with the tag „Relevance“. 
The seperate decisions about is music-related (isMusic) and event-related (isEvent) as well as 
the corresponding probabilities (IsEventInterRaterAgreement and IsMusicInterRaterAgreement) are 
also given in this schema. Here we considered only two types of text resources: Facebook and newspaper. 
The event type can be extended later flexibly as requires.

- <strong>Common.xsd</strong>: in this schema, all the basic types are defined, such as Location, Organizer, meta-information about the raw document. 
Apart from this, the music-related NER sets are also defined in this scheam.

- <strong>FacebookSource.xsd</strong>: this schema corresponds to the events that are acquired from facebook. All information about event is gathered 
and described in this schema.

- <strong>FoundInfo.xsd</strong>: this file provides the meta-information that relates to the event. It gives the expanded information of locations and organizers.

- <strong>NamedEntity.xsd</strong>: in this file, all the Named Entities, such as musician, band, Song writer etc. are defined and included in a Named Entity set. When Named Entities occur in texts, it will be encapsulated in corresponding 
Named Entity type (with music roll, if it's music related). 

- <strong>PaperSource.xsd</strong>: this schema corresponds to the events that are gathered from news paper. It defines also event but with different source.

Usage
===============
 For formatting the raw text data, we provide a tool called <strong>CueSchema.py</strong>. It gives the following functionalities:
 - <strong>Validating a single xml file</strong> that is formatted by our schemas or yourself:
 >- $: python CueSchema.py -p  test.xml 
 
 - <strong>Formatting raw unstructured single text into xml files</strong> after the schema, the raw data is given in <em>facebook_events.json</em>, the resutl file is speicifed in 
 <em>Result_Facebook.xml</em>, <em>ner.txt</em> provides the named entities occur in our raw text:
 >- $: python CueSchema.py  -s facebook_events.json -o Result_Facebook.xml -n ner.txt
 
 - <strong>Formatting raw unstructured texts into xml files in batch mode</strong> after the schema, the <em>Standart_with_sources.json</em> file
 specifies the necessary information related to raw text,  the directory <em>ner/</em> gives the path where the ner reatled texts are located
, <em>Decision.csv</em> provides the music relatedness, music relatedness as well relevance of each text:
 >- $: python CueSchema.py  -l Standart_with_sources.json -e ner/ -v Decision.csv

 
