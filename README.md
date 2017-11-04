# BOLD DNA sequence
Linking BOLD DNA sequences to specimens published in GBIF

Linking DNA sequence barcode data from BOLD to specimens in GBIF has a high priority in the GBIF work-plan. The [GBIF Science Committee](https://www.gbif.org/contact-us/directory?group=scienceCommittee) represented by SC chair Rod Page, [published in December 2016](http://iphylo.blogspot.no/2016/12/dna-barcoding-taxonomy-now-in-gbif.html) a [snapshot](https://github.com/rdmpage/ibol-dwca) of the iBOL dataset [doi:10.15468/inygc6](http://doi.org/10.15468/inygc6) including a total of 2,789,906 occurrences. However, the link to the museum specimens themselves has not been maintained. Example: [gbifKey:1415958347](https://www.gbif.org/occurrence/1415958347 "GBIF iBOL 2016 dataset occurrence record") and the corresponding BOLD data record with [processid:LON2542-15](http://bins.boldsystems.org/index.php/Public_RecordView?processid=LON2542-15 "BOLD processid=LON2542-15").

The most reliable specimen identifier in GBIF is the [dwc:occurrenceID](http://rs.tdwg.org/dwc/terms/occurrenceID). There is also the traditional and (more) human readable [dwc:catalogNumber](http://rs.tdwg.org/dwc/terms/catalogNumber) identifying a museum specimen. The [BOLD Process ID](http://www.boldsystems.org/index.php/resources/boldfaq#reg1) is the most important identifier for material samples corresponding to the museum specimens. BOLD also provide a "Museum ID" and a "Sample ID" however, nether match exactly the occurrenceID or the catalogNumber in GBIF.


| GBIF                                 | BOLD                     |
|-------------------------------------:|:-------------------------|
| occurrenceKey = 1426521030           | Process ID = NOBAS010-14 |
| occurrenceID = urn:catalog:O:F:75130 | Museum ID = O-F-75130    |
| catalogNumber = 75130                | Sample ID = O-F-75130    |
| eventID/fieldNumber = [blank]        | Field ID = MY1-0568      |

* BOLD URL: http://bins.boldsystems.org/index.php/Public_RecordView?processid=NOBAS010-14 
* BOLD API: http://www.boldsystems.org/index.php/API_Public/sequence?ids=NOBAS010-14 

* GBIF URL: https://www.gbif.org/occurrence/1426521030 
* GBIF API: http://api.gbif.org/v1/occurrence/1426521030/verbatim 

## Mapping from BOLD API to GBIF IPT

Feedback on the proposed mapping using the issues tracker is most welcome!

### MeasurementOrFact :: http://rs.gbif.org/extension/dwc/measurements_or_facts.xml
* measurementID = boldAPI:processid
* measurementType = "BOLD-sequence" _[alt. = BOLD-sequence + (_markercode_)]_
* measurementValue = boldAPI:nucleotides
* measurementAccuracy = NULL
* measurementUnit = NULL
* measurementDeterminedDate = boldAPI:run_dates
* measurementDeterminedBy = boldAPI:sequencing_centers
* measurementMethod = boldAPI:markercode  _[alt. = boldAPI:seq_primers]_
* measurementRemarks = http://www.boldsystems.org/index.php/API_Public/sequence?ids= + _processid_

### Simple Multimedia :: http://rs.gbif.org/extension/gbif/1.0/multimedia.xml
* type = "StillImage"
* format = "image/jpeg"
* identifier = boldAPI:image_urls
* references
* title = occurrenceID [alt. = processID]
* description = boldAPI:captions
* created = boldAPI:copyright_years
* creator = boldAPI:photographers
* contributor
* publisher = boldAPI:copyright_institutions (??)
* audience = "experts"
* source = "BOLD"
* license = boldAPI:copyright_licenses
* rightsHolder = boldAPI:copyright_institutions
* datasetID

