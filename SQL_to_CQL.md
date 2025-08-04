# To help all splunkers (SPL) who have been forced to adopt Crowdstrike Query Language (CQL)
## Basic Field Search
Description: To conduct a basic search in SPL vs CQL

**Splunk**

```index=foo sourcetype=bar field=value```

**CQL**

```#event_simpleName=foo field=value``` 

Notes: No need to define index or sourcetype, there is only CS just search off event_simpleName "#" is required.

## Create New Field
Description: To make a new field from a value in the search use the follwing syntax.

**Splunk**

```| eval field=value```

**CQL**

```| field := value``` 

## Regex Syntax
Description: To use regex filtering in your CQL query.

**Splunk**

```| regex field="(?i)\\\(match|match2)\\\```

Notes: 
+ (?i) case incentive token.
+ | or statement
+ " regex " used to identify start and end of regex
+ \\\\ two escapes needed to escape single "\\\"

**CQL**

```field=/\\(match1|match2)\\/i``` 

Notes:
+ /i for case incentive token
+ | or statement
+ / regex / used to identify regex
+ one \ needed to escape single "\"
