# Confluence-PageGenerator
## Description
A simple http service that posts a page in **Conflunce**
## Requirements
Build requiremnts:
* [Maven 3.9.0](https://maven.apache.org/download.cgi)
* [Java version 17+](https://www.oracle.com/in/java/technologies/downloads/)


Runtime requirements:
* a Confluence account which has API access and a personal access token

## Installing and Building
1. Clone the project 
```git
git clone https://rndwww.nce.amadeus.net/git/scm/perfs/confluence_report.git
```
2.Open the code in IDEA or open cmd in the project path, in the terminal
* this will compile and package and gives you the target folder which has the jar file
```maven
mvn clean install
```

## Posting Page
* API endpoint - /api/content

### Environment variables
* Add secrets to the user variables
* Space Id and Parent page Id can also be added directly in commandline, but token and url must be present in the env variables
```
CONFLUENCE_TOKEN  "Confluence API personal access token"
CONFLUENCE_URL    "https://{domain}/confluence/rest/api/content"
PARENT_PAGE_ID  "parent page id"
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
* Sample command to run the jar file
```cmd
java -cp target/confluence_report.jar CreatePageConfluence -create -t "Sample title" -c "Sample Content" -s XXX -p 0 -l sample_label
```

* Sample command with long options
```cmd
java -cp target/confluence_report.jar CreatePageConfluence -create --title "Sample title" --content "Sample Content" --space XXX --parent 0 --label sample_label
```

#### Get Page Content from Confluence
* Command to get data from the confluence using pageId
* pageId of the page can be found in the url of pageInformation
```cmd
java -cp target/confluence_report.jar CreatePageConfluence -get -pageId 000000000
```


