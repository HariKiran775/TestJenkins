# TestJenkins
## Description
A simple http service that posts a page in **Conflunce**
## Requirements
Build requiremnts:
* [Maven 3.9.0](https://maven.apache.org/download.cgi)
* [Java version 17+](https://www.java.com/download/ie_manual.jsp)


Runtime requirements:
* a Confluence account which have API access and a personal access token
## Posting Page
* API endpoint - /api/content

### Environment variables
* Add secrets to the user variables
* Space Id and Parent page Id can also be added directly in commandline, but token and url must be present in the env variables
```
CON_TOKEN  "Confluence API personal access token"
CON_URL    "https://{domain}/confluence/rest/api/content"
PARENT_ID  "parent page id"
SPACE_ID   "space id"
```
### Command line
#### CommandLineParameters
```cmd
java -cp target/confluence_report.jar CreatePageConfluence -h
```
```
usage: CommandLineParameters
 -c,--content <arg>   Page content
 -create              CreatePage
 -get                 GetPage
 -h,--help            Shoes the help
 -l,--label <arg>     label
 -p,--parent <arg>    parentId
 -pageId <arg>        Get the data from this page
 -s,--space <arg>     space
 -t,--title <arg>     page Title
```

```cmd
java -cp target/confluence_report.jar CreatePageConfluence -create -t "Sample title" -c "Sample Content" -s XXX -p 0 -l sample_label
```

* Give only some arguments and take rest as default i.e; config.yaml

Space key is given, rest is default
```cmd
java -cp target\CurlConfluence-1.0-SNAPSHOT-jar-with-dependencies.jar CreatePageConfluence - - XXX - 0
```

