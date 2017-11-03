# BOLD DNA sequence
Linking BOLD DNA sequences to specimens published in GBIF

Linking barcode data from BOLD to specimens in GBIF has a high priority in the current GBIF work-plan. The GBIF Science Committee (represented by chair Rod Page) published in December 2016 a snapshot of the iBOL dataset (doi:10.15468/inygc6) including a total of 2,789,906 occurrences. However, the link to the museum specimens themselves was not maintained.

### Examples from the GBIF iBOL 2016 dataset:
* GBIF iBOL occurrence record: https://www.gbif.org/occurrence/1415958347
* BOLD data record: http://bins.boldsystems.org/index.php/Public_RecordView?processid=LON2542-15

The most reliable specimen identifier in GBIF is the dwc:occurrenceID. There is also the traditional and (more) human readable dwc:catalogNumber identifying a museum specimen. The BOLD Process ID is the most important identifier for material samples corresponding to the museum specimens. BOLD also provide a "Museum ID" and a "Sample ID" however, nether match exactly the occurrenceID or the catalogNumber in GBIF.


| GBIF                                 | BOLD                     |
|-------------------------------------:|:-------------------------|
| occurrenceKey = 1426521030           | Process ID = NOBAS010-14 |
| occurrenceID = urn:catalog:O:F:75130 | Museum ID = O-F-75130    |
| catalogNumber = 75130                | Sample ID = O-F-75130    |
| eventID/fieldNumber = [blank]        | Field ID = MY1-0568      |
| GBIF API: 1426521030                 | BOLD API: NOBAS010-14    |


* URL: http://bins.boldsystems.org/index.php/Public_RecordView?processid=NOBAS010-14 
* API: http://www.boldsystems.org/index.php/API_Public/sequence?ids=NOBAS010-14 

* URL: https://www.gbif.org/occurrence/1426521030 
* API: http://api.gbif.org/v1/occurrence/1426521030/verbatim 

## Mapping from BOLD API to GBIF IPT

Feedback on the proposed mapping using the issues tracker is most welcome!

### MeasurementOrFact :: http://rs.gbif.org/extension/dwc/measurements_or_facts.xml
* measurementID = boldAPI:processid
* measurementType = "BOLD-sequence" [alt. = "BOLD-sequence (_markercode_)"]
* measurementValue = boldAPI:nucleotides
* measurementAccuracy = NULL
* measurementUnit = NULL
* measurementDeterminedDate = boldAPI:run_dates
* measurementDeterminedBy = boldAPI:sequencing_centers
* measurementMethod = boldAPI:markercode  [alt. = boldAPI:seq_primers]
* measurementRemarks = http://www.boldsystems.org/index.php/API_Public/sequence?ids=_processid_

## Simple Multimedia :: http://rs.gbif.org/extension/gbif/1.0/multimedia.xml
* type = "StillImage"
* format = "image/jpeg"
* identifier = http://www.boldsystems.org/pics/NOBAS/MY1_0568+1408457242.JPG
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

