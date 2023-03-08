# Confluence-PageGenerator
### Description
A simple http service that posts a page in Confluence
### Requirements
Build requiremnts:
* [Maven 3.9.0](https://maven.apache.org/download.cgi)
* [Java version 17+](https://www.oracle.com/in/java/technologies/downloads/)


Runtime requirements:
* a Confluence account which has API write access ,and access to the space in which the page is created.
* personal access token 

### Getting Started

#### Installation

1. Clone the project
```git
git clone https://rndwww.nce.amadeus.net/git/scm/perfs/confluence_report.git
```
2.Open the code in IDEA or open cmd in the project path, in the terminal
* this will compile and package and gives you the target folder which has the jar file
```maven
mvn clean install
```

#### Running Confluence-PageGenerator
##### Log file
* Create a file with extension *.properties
* Sample properties file and you can also exclude console handler if not necessary
```properties
handlers= java.util.logging.ConsoleHandler, java.util.logging.FileHandler
.level= INFO

# Configure the console handler
java.util.logging.ConsoleHandler.level = INFO
java.util.logging.ConsoleHandler.formatter = java.util.logging.SimpleFormatter

# Configure the file handler
java.util.logging.FileHandler.level = INFO
java.util.logging.FileHandler.formatter = java.util.logging.SimpleFormatter
java.util.logging.FileHandler.pattern = LOG_FILE
```

### Environment variables
* Add secrets to the user variables and add the path of the log properties file.
* Space Id and Parent page Id can also be added directly in commandline, but token and url must be present in the env variables
```
CONFLUENCE_TOKEN   "Confluence API personal access token"
CONFLUENCE_URL     "https://{domain}/confluence/rest/api/content"
CONFLUENCE_LOGPATH "LOG_PATH"
PARENT_PAGE_ID     "parent page id"
SPACE_ID           "space id"
```
### Command line
#### CommandLineParameters
```cmd
java -jar target/confluence_report.jar --help
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
java -jar target/confluence_report.jar -create -t "Sample title" -c "Sample Content" -s XXX -p 0 -l sample_label
```

* Sample command with long options
```cmd
java -jar target/confluence_report.jar -create --title "Sample title" --content "Sample Content" --space XXX --parent 0 --label sample_label
```

#### Get Page Content from Confluence
* Command to get data from the confluence using pageId
* pageId of the page can be found in the url of pageInformation
```cmd
java -jar target/confluence_report.jar -get -pageId 000000000
```
###### Check all the logs in error.log file


