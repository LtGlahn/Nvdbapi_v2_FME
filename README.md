NVDB api V2 with FME
===============
Sample FME workspaces to fetch objects from [NVDB api v2](https://www.vegvesen.no/nvdb/apidokumentasjon/). 

Made with FME desktop 2015.

Modifying these workspace to fetch other object types is straightforward, but the property names must be explisit defined (or exposed) in an attributeCreator transformer (or attribute Exposer, if you prefer). With over 360 object types defined in NVDB data catalogue, this handiwork could become very boring and tedious very quickly. 

For a more generic solution, check out @jetgeo [NVDBGML](https://github.com/jetgeo/NVDBGML/tree/master/FME). 

Please note that the location of the xfsmap definition file (*xfmapDefintion_nvdbapi2fme_V2.xml*) in the XMLFeatureReader transformer must be adjusted to match your local file system. In most cases, it should work straight out of the box - if not, just pop open the "point at file" dialog, click on the file and hit OK.

![Locate xfmapfile in XML Feature M](/images/locate_xfmapfile.PNG)
 

# nvdbapi_V2_Bomstasjoner.fmw 

Will download all toll stations (Bomstasjoner) from NVDB api. Optionally, you may also augment the data set with street names. If enablet, for each Bomstasjon-feature we attempt to fetch street names at the bomstasjon locations in the road network(NVDB object "Gate", property "Gatenavn" at the same route ID + road network position). See https://www.vegvesen.no/nvdb/apidokumentasjon/#/verdi/veglenke 

> **Note** Due to a bug in NVDB api, we cant search for objects at a **precise** point at the road network: We must search within a stretch of the road. So instead of the _linkID@position_ syntax we  use _linkID@fromPosition-toPosition_ 
 

Make sure the location of the xfsmap defintion file (*xfmapDefintion_nvdbapi2fme_V2.xml*) in the XMLFeatureReader transformer matches your local file system. 


# nvdbapi_V2_trafikkulykker.fmw 

Will download road accidents (trafikkulykke) from NVDB api for Tromsø kommune. Optionally, only download accidents with property  _Alvorligste skadegrad = drept_

Make sure the location of the xfsmap defintion file (*xfmapDefintion_nvdbapi2fme_V2.xml*) in the XMLFeatureReader transformer matches your local file system. 



