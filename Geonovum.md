# Notes Geonovum
Some Geonovum models require other Test Object Types than available in the vanilla ETF validator. See https://github.com/etf-validator/etf-webapp/issues/180
Therefore this fork is created. Geonovum maintains the changes for the Test Object Types for this library.

## Changes
Note: EID = ```EID{UUID}```

### StUF IMGeo 1.1.1 documents
EID:
```
EIDa7fb8a3d-c82d-48f0-a5c6-8f13efebefb1
```
Namespace root-element:
```
http://www.geostandaarden.nl/imgeo/2.1/stuf-imgeo
```

### StUF IMGeo 1.2 documents
EID:
```
EID1b9cf8d4-85cc-4f30-9848-25cb33333b54
```
Namespace root-element:
```
http://www.geostandaarden.nl/imgeo/2.1/stuf-imgeo/1.2
```


### StUF IMGeo 1.3 documents
EID:
```
EID14b4aa1d-6157-413d-8acc-f8a026d0d6dd
```
Namespace root element:
```
http://www.geostandaarden.nl/imgeo/2.1/stuf-imgeo/1.3
```

### GeoBAG 1.0
EID:
```
EID500d136e-4fda-4a76-8998-bb1bfd07fa4b
```
Namespace root element:
```
http://register.geostandaarden.nl/xmlschema/geobag/1.0
```

### GeoBAG 1.1
EID:
```
EIDd5877f6d-740d-4765-b56d-21320e756944
```
Namespace root element:
```
http://register.geostandaarden.nl/xmlschema/geobag/1.1
```

### GeoBOR 1.0
*TODO: Is Geo-BOR altijd het root-element?*

EID:
```
EID6d5155b2-9202-4d7d-8c7b-0c43bf1c0a63
```

Namespace root element:
```
http://register.geostandaarden.nl/imgeo/2.1/geobor/1.0
```


## Building the library (and fixing building errors)
To build the library:
1. (try to) build the jar the first time (skip tests, due to an error in tests), in the root dir of the project: ```./gradlew jar -x test```
1. Building probably fails. This is a known issue in the etf-webapp setup with gradle (see https://github.com/etf-validator/etf-webapp/issues/168). Fix some settings to avoid errors like:
```
Could not resolve all dependencies for configuration ':compileClasspath'.
> Could not resolve de.interactive_instruments:ii-commons-util:2.0.0-SNAPSHOT.
  Required by:
      project :
   > Could not resolve de.interactive_instruments:ii-commons-util:2.0.0-SNAPSHOT.
      > Unable to load Maven meta-data from http://services.interactive-instruments.de/etfdev-af/ext-releases-local/de/interactive_instruments/ii-commons-util/2.0.0-SNAPSHOT/maven-metadata.xml.
         > Could not GET 'http://services.interactive-instruments.de/etfdev-af/ext-releases-local/de/interactive_instruments/ii-commons-util/2.0.0-SNAPSHOT/maven-metadata.xml'. Received status code 403 from server: Forbidden
   > Could not resolve de.interactive_instruments:ii-commons-util:2.0.0-SNAPSHOT.
      > Unable to load Maven meta-data from http://services.interactive-instruments.de/etfdev-af/ext-cache/de/interactive_instruments/ii-commons-util/2.0.0-SNAPSHOT/maven-metadata.xml.
         > Could not GET 'http://services.interactive-instruments.de/etfdev-af/ext-cache/de/interactive_instruments/ii-commons-util/2.0.0-SNAPSHOT/maven-metadata.xml'. Received status code 403 from server: Forbidden
```
1. then continue building the jar again.

### Building with gradle
Build jar and skip tests (contains error):
```
./gradlew jar -x test
```

The jar-file can be found in ```./build/libs/etf-stdtot-{version}.jar```

### Deployment
1. Remove or replace the existing version (etf-stdtot-{version}.jar) from the libs directory of the ETF webapp: ```etf-webapp/WEB-INF/lib/```. And put the new jar-file in the ETF webapp lib directory.
1. (Re)load the web application
