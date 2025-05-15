'''XML chart correction examples for comparison'''


----

'''Finnish XML'''

Description by TRAFICOM:
NtM chart corrections in XML are produced since 2016. A custom XSD-schema is used. XML for booklets is imported into Indesign- software and made into PDF- booklets using a "semi automatic" workflow. XML-schema is defining a "list of notices", and the same XML- format is used also for the T&P- list. Separate XSL- translations are used to produce different products. Example includes Native XML-format, common XML-format and common XML translated into HTML.

* '''Examples:''' [[File:FI ntm issue 2019 30.zip]]

Contacts: stefan.engstrom@traficom.fi

'''Comments:'''

----

----

'''French XML'''

Description by Shom:
NtM chart corrections in XML are produced since the beginning of 2018, with CARIS “Publication module” customized for Shom. They are used by our internal process for the production of our weekly NtM booklet (pdf) and NtM website. The XML also contains some internal data. The XML doesn’t contain the chart correction number. It is added later in the process as well as the link with the tracing and with the possible NtM block (graphical chart-updating). One NtM may concern several charts to be updated. The XML refers to a font (TrueTypeFont) for the graphical feature which is subject of the instruction. The chart corrections are in French and a glossary French-English is available in our weekly NtM booklet and NtM website [(http://gan.shom.fr/ganl/htdocs/FR_home.htm)].
We also convert the XML in GML for internal checking purposes using the geometry of NtM (graphical display).
In the examples below, one file containts the chart corrections for one weekly NtM booklet.

'''Examples:''' [[File:Xml_fr.zip]]

Contacts: pierre-yves.le.moigne@shom.fr, jonathan.mouton@shom.fr

'''Comments:'''

----


----

'''German XML'''

Description by BSH


'''Examples''' [[File:DE_xml.zip]]

Contacts: daniel[dot]zuehr[at]bsh[dot]de

'''Comments:'''

----


----
'''Italian NtM'''

Dwscription by Italian HO

'''Examples''' [[File:Italian_NtM.zip]]


Contacts: ludovico_sturla[at]marina[dot]difesa[dot]it


'''Comments:'''

----


----




'''Conventions Summary'''


=Conventions=

==Multiple use of XML, Notice(s) applicable for one chart, notice applicable for several charts==
The data model to be developed should be able to handle both versions. If the setup is such, that every chart-correction can have a reference to one or several charts [1..*], it is up to the producer to decide whether corrections are repeated chart-by-chart or each correction has a reference to all affected charts. The German XML version shows that it should be possible to create a data structure that supports both versions. 

== Data model ==

== Data model files ==

* Data model package including *.eap is transferred to GitHub. '''https://github.com/fihofi/ntm_common_xml'''
* To download the latest release package as zip: '''https://github.com/FihoFi/ntm_common_xml/releases/'''

=== UML diagram ===
'''Data model as UML- diagram presenting the structure of a list of Notices to Mariner'''
[[File:UML_NtM_conceptual_structure.png]]

===Notice===
Each '''NoticeToMariner''' represents one single Notice.

===NoticeContent===
Each notice can contain any number of '''NoticeContent'''. '''NoticeContent''' is an abstract object, which can represent any of three types of content. 
* '''TextContent''' is a simple text-field, that can store simple (unformatted) text. 
* '''ImageContent''' is any image added to the notice. Usually these are images of the chart to be corrected. 
* '''ChartCorrectionContent''' is a complex structure that includes a combination of an S-4 standard action (ADD, DELETE etc.), INT- symbols, standard phrases /commands and additional textual explanations.

Each '''NoticeContent''' has a reference to a '''ChartImage''', which in turn has a reference to the '''ChartProduct''' it belongs to. A chart product is here assumed to be a given edition of a chart.

===ChartCorrectionContent===
The ChartCorrectionContent is the structure holding the actual chart-correction.
The table below shows the tabular display translation of one ChartCorrectionContent, with 3 ChartCorrectionTextrows and 5 ChartCorrectionPositions

* The first row could contain INT- symbols and a textual note, which are attributes of ChartCorrectionContent
* The following rows could contain data stored in ChartCorrectionTextrows

{| class="wikitable"

|Action
|
{| class="wikitable"
|-
| objectA ||  ||objectB || row_note
|-
| textA ||  ||textB || row_note
|-
| textA ||  ||textB || row_note
|-
| textA ||  ||textB || row_note
|}
|
#lat lon description
#lat lon description
#lat lon description
#lat lon description
#lat lon description
|}

==Images and Symbols==

===Format===
Symbols will be described by textual description and graphical symbols. Textual description will be mandatory. 
The graphical symbols can be provided by a) vector (svg), b) Raster (TIFF), c) Font (True Type Font).
 
<symbolTxt><br>
<BOYCAR><br>
<BOYSHP>pillar</BOYSHP><br>
<CATCAM>north cardinal mark</CATCAM><br>
<COLOUR>black, yellow</COLOUR><br>

</BOYCAR><br>
	<TOPMAR><br>
…<br>
</TOPMAR><br>
<LIGHTS><br>
	…<br>
</LIGHTS><br>
<ChartLabel><br>
<Content>Fl.Y.3s</Content> [currently, single attributes in LIGHTS]<br>
<nowiki><!-- <Style>bold, italic, 6pt</Style> --></nowiki><br>
</ChartLabel><br>
</symbolTxt><br>


The associated xsd in that case would be:

<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
<xs:element name="symbolLeft">
          <xs:element name="symbolVector" minOccurs="0"/>
          <xs:element name="symbolRaster" minOccurs="0"/>
          <xs:element name="symbolFont" minOccurs="0"/>
          <xs:element name="symbolTxt" minOccurs="1"/>
</xs:element>
</xs:schema>

===Repository===
Symbols can be stored by each HO individually. <br> 
Should we try to convince the IHO Secretariat to host a repository (database) of symbols (similar to INT1) in a discrete format (to be defined) and a textual description associated to each symbol? <br>
HOs can then download the data sets and use them in their production systems. It should be discussed how the generation/drawing of symbols can be managed. Is an appropriate online tool available on the market? Should we approach the Secretariat to contract the developement of such an online tool? Can HO(s) volunteer to contract the development?

===Generation===
use of predefined set(s)<br>
customise as appropriate, e.g. depth with depth contour

==Status of correction==
Following status versions are appliable:<br>
'''Published'''
PUBLISHED notices are those, which are in force. <br>

'''Cancelled'''
CANCELLED notices are those, which are cancelled by a new notice.<br>
CANCELLED notices are those, which are not showing up on the "T&P in force" list. <br>

'''Deactivated'''
DEACTIVATED notices are those, which are not active anymore due to any several (internal or external) reasons, e.g. a new edition of a chart makes it superfluous<br> 
DEACTIVATED notices are those, which are not showing up on the "T&P in force" list<br>

==Chart corrections and General notifications==

===Chart corrections===
Instruction where to place a block, e.g ADD block in position xxx.xxx, yyy.yyy<br>
Instructions according to IHO Standard S-4<br>
Use of GML coordinate encoding at the backend but at the front end the coordinates should be presented as 00°00,000'N  000°00,000'E, less decimals are possible if source or chart scale make it necessary<br>

Do we need to provide information on corrections of corrections (Pierre-Yves raises this question)? Or can we say that all corrections are independant corrections and if one needs to correct erratums, a new correction should be generated without mentioneing that it corrects erratums?<br>

Stefan: In the FI system is a function for a notice to cancel another previously published notice. We are using this functionality for corrections to previous notices.<br> Also re-issuing or cancelling T&P notices is made using this same functionality


Ludovico: In the case we made an error on a notice, we produce another notice to correct the chart and not the notice: this because from our experience, the mariners do not track and collect the number of notices and their history, but they reported manually the corrections on the affected charts when they receive the notices (except for T&P notices that should be charted in pencil and being tracked for cancellation purpose).
Just for internal use and for letting the mariners know that in the real word there is no change to the previous situation but only a difference of that is represented on the chart, we use the letter “(R)” beside the notice number.

===Positions===
Positions in the common XML have to be provided in decimal degree. The format for editors input and publications output is in HOs decision. <br>
SOURCE_HO_NTM.XML (decimal degree/ degree, decimal minutes) => SOURCE_TO_COMMON.XSL  => COMMON_NTM.XML (decimal degree) => COMMON_TO_RCVR.XSL => RCVR_HO_NTM.XML (decimal degree/ degree, decimal minutes)


Additional verbal description of a position should be provided. (no lat/long available, corrections affecting symbols on the chart edge).

===P&T Notices===
It should be no difference between T&P and  regular notices. All notices are similar in structure, and only an attribute flag is indicating a notice as T or P.

P&T notices can have following status:<br>

PUBLISHED - in force<br>
CANCELLED - no longer in force due to cancellation by another P&T notice, or by a full notice (appropriate information must be provided)<br>
DEACTIVATED- no longer in force due to HO internal processes (appropriate information must not be provided)<br>




{| class="wikitable"


|
{| class="wikitable"
|-
| '''S4 ed 4.7.0 reference''' || '''Standard/Permanent Notice''' || '''T&P Notice'''  || '''Notes'''
|-
| B-630.4 j) reference to the preceding NM ||YES || NO||
|-
| B-631.3 Title ||YES || YES||
|-
| B-631.4 Text ||YES || NO||ES, FR, GB, HR and TN for T&P notices use a textual description including positions, rarely  the 5 instruction terms (insert/delete/amend/replace/move) are used
|-
| B-631.5 Positions ||YES || YES||
|-
| B-631.6 Authority ||YES || YES||
|-
| B-631.7 Charts(s) affected ||YES || YES||
|-
| B-631.8 Amplifying notes ||YES || NO||Used in T&P notices very often from the above HOs
|-
| Cancellation of a previous notice||NO|| YES||

|}
|
|}

===General notification===

New Chart/New Edition can be provided as general notification messages. <br>
HOs have to decide in which section of the Bulletin this information will be provided.  (chart correction section, catalogue correction, miscellaneous).

==Language==
The corrections should be provided in multiple languages.

In the UML there is a separate class '''MultilangString''' to indicate which attributes currently need to be provided in several languages. For example chart-texts are not translated.

==Block correction==
Block corrections are to be created as separate geo-referenced PDF-documents / files. <br>

A link to the block is added to the Notice. The provision of the block centre geo-reference is optional.<br>

The separate geo-referenced PDF-documents / files should also be made available for download.

==Images providing correction advice==
Larger images assisting the chart-correction can be added as '''ImageContent'''.

=XML Examples after the XML workshop=
==Finland==
* '''Examples:''' [[File:FI ntm issue 2019 30.zip]]

==France==
[[File:FR_NTM_XML.zip]]  containg two files, the XML and the xsl

==Germany==

==Italy==
[[File:Italy.XML]]

==Norway==
[[File:NO_NTM_XML.zip]] XML- file as presented on NIPWG 7

==UK==


==US==
