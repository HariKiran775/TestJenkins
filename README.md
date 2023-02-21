# TestJenkins
## Description
A simple http service that posts a page in **Conflunce**
## Requirements
Build requiremnts:
* [Maven](https://maven.apache.org/download.cgi)
* [Java](https://www.java.com/download/ie_manual.jsp)


Runtime requirements:
* a Confluence account which have API access and a personal access token
## Posting Page
* API endpoint - /rest/api/content
* sample config.yaml 
```yaml
pageTitle: Sample Page
page: <h1>Some Content</h1>
space: XXX
labelToAdd: Some_label
parentPageId: 0
```
### Command line
* Arguments can be given in the same order mentioned in sample config.yaml

```cmd
java -cp target\CurlConfluence-1.0-SNAPSHOT-jar-with-dependencies.jar CreatePageConfluence "Sample page" "<h1>Some Content</h1>" XXX Some_label 00000000
```

* Give only some arguments and take rest as default i.e; config.yaml
```cmd
java -cp target\CurlConfluence-1.0-SNAPSHOT-jar-with-dependencies.jar CreatePageConfluence - - XXX - 0
```

