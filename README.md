usgin-geoportal-specs
=====================

USGIN Geoportal-Server Documents and Files for packaging. 

##The USGIN ISO 19115 Profile for Geoportal-Server

After the geoportal has been successfuly setup and is running, you are ready to add new profiles. The items available through this package (repository) are the USGIN 19115 profile, and the CSDGM FGDC to ISO 19115 XSLT.

###Getting USGIN 19115 Set Up

Navigate to the /webapps/geoportalName/WEB-INF/classes/gpt/metadata/iso directory in the geoportal-server

Move the usgin folder, available through this package, and place it into the metadata/iso directory in the geoportal-server.

Navigate back to the gpt/metadata directory in the geoportal-server

Open the schemas.xml file in an editor and add the USGIN defintion files between the open and closed <schemas></schemas> elements:

'''
<schemas>

	<!-- The first definition file tests to determine if the input record has been processed by the
	ISO to USGIN ISO xslt transform; if it has, it is processed by the definition file.  All validation criteria
	have been removed from the validation, the assumption being that once processed by the xslt, it is a valid
	usgin-profile record-->

   	<schema fileName="gpt/metadata/iso/usgin/USGIN-ISO19115Definition.xml"/>
 
   	<!-- The second defintion file tests whether the record is a MD_Metadata or MI_Metadata record and if so,
   	sends it to the ISO to USGIN ISO xslt; after transformation it will be interrogated again and caught by the
  	 first definition file -->

   	<schema fileName="gpt/metadata/iso/usgin/ISO-to-USGIN-19115-data-definition.xml"/>

</schemas>
   
'''


In order for the USGIN 19115 profile to work thorouly on all ISO metadata it should replace the ISO 19115 and ISO 19115-2 profiles in the geoportal-server. Remove the ISO 19115 and ISO 19115-2 definitions from the schemas file, and place the USGIN ISO 19115 definitions at the beginning of the file after the first <schemas> element. If an example is needed, review the schemas.xml file that comes with this package. All definition files do not, and should not be removed.
