# ntm_common_xml
An XML- data model for Notices to Mariners. This development work is the result of the [IHO](http://www.iho.int) [NIPWG](https://www.iho.int/srv1/index.php?option=com_content&view=article&id=628&Itemid=980&lang=en) initiative to create a common format for chart-corrections to facilitate sharing and re-using this data among Hydrographic offices. 
The development of a common data model and XSD was initiated at the [XML- workshop](https://www.iho.int/mtg_docs/com_wg/NIPWG/WorkshopXMLNtM2018/WorkshopXMLNtM2018Docs.html) hosted by the Italian Hydrographic Institute in Genoa 1-2 October 2018.

Futher discussions is found at the [NIPWG WIKI](http://wp12183585.server-he.de/npubwiki/wiki/index.php/NtM_Chart-correction_XML).
For questions regarding this GitHub repository, please contact stefan[dot]engstrom[a]traficom[dot]fi

### 2020-01-20
  * EA project refresh
  * Open / Save EAP- project in version 12.0.1215
  * New export of separate PNG- UML image
  * New export of XSD- file. (Note! Untick: Tools -> Options -> Objects -> Sort features Alphabetically)
  

### 2018-10-18
  * Uploaded a complete package with the changes in XSD- file since 0.0.3
   * Created release 0.0.4
  * Changes;
   * attribute *area* moved to beginning of *notice*
   * *productLastCorrected* is optional, as sometimes a chart is brand new
  
### 2018-10-17
  * Uploaded new version
  * Created release 0.0.3
  * Changes: 
    * attributes ordered by content instead of alphabetically
    * chart data added once to the notice and panel referenced in content
    * <producingAgencyS62/> dataype changed string => int

### 2018-10-10
  * Uploaded version 0.0.2 of the package.
