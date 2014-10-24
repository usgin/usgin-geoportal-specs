usgin-geoportal-specs
=====================

USGIN Geoportal-Server Documents and Files for packaging. 

##The USGIN ISO 19115 Profile for Geoportal-Server

After the geoportal has been successfully setup and is running, you are ready to add new profiles. The items available through this package (repository) are the USGIN 19115 profile, and the CSDGM FGDC to ISO 19115 XSLT.

###Getting USGIN 19115 Set Up

#### STEP 01: Adding The USGIN Folder to the Geoportal-Server

Navigate to the _/webapps/geoportalName/WEB-INF/classes/gpt/metadata/iso_ directory in the geoportal-server

Move the usgin folder, available through this package, and place it into the _gpt/metadata/iso_ directory in the geoportal-server.

#### STEP 02: Adding Definition Files to the Schemas.xml File

Navigate back to the _gpt/metadata_ directory in the geoportal-server

Open the schemas.xml file in an editor and add the USGIN definition files between the open and closed <schemas></schemas> elements:

```
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
   
```


*NOTE:* In order for the USGIN 19115 profile to work thoroughly on all ISO metadata it should replace the ISO 19115 and ISO 19115-2 profiles in the geoportal-server. Remove the ISO 19115 and ISO 19115-2 definitions from the schemas file, and place the USGIN ISO 19115 definitions at the beginning of the file after the first <schemas> element. If an example is needed, review the schemas.xml file that comes with this package. All definition files do not, and should not be removed.

#### STEP 03: Adding Properties into the gpt.properties File

Navigate to the _gpt/resources_ directory in the Geoportal-Server

Open the gpt.properties file in a text editor and scroll to bottom of page

Add in properties needed for USGIN 19115 profile:

```
# Label resource key for USGIN editor
catalog.mdParam.schema.usgin.iso19115 = USGIN-ISO 19115 Profile
```
#### STEP 04: Save Everything and Restart Servlet/Tomcat

After the servlet has been restarted, test out the USGIN Profile to see if it works.

### Adding the FGDC to USGIN-ISO 19115 XSLT
Provided in this package (repository) is an fgdc directory that contains the XSLT and Definition file for FGDC to USGIN-ISO 19115. 

#### STEP 01: Add Files from the FGDC Directory into the Geoportal-Server

Navigate to the _\gpt\metadata\fgdc_ directory within the Geoportal-Server and place the fgdc-to-USGIN19115-definition.xml and csdgm-to-iso19115_USGIN.xslt files in.

#### STEP 02: 

