# To help all splunkers in Splunk Processing Language (SPL) who have been forced to adopt Crowdstrike Query Language (CQL)
## Basic Field Search
Description: To conduct a basic search in SPL vs CQL

**Splunk**

```index=foo sourcetype=bar field=value```

**CQL**

```#event_simpleName=foo field=value``` 

Notes: No need to define index or sourcetype, there is only CS just search off event_simpleName "#" is required.

## Token Search
Description: To conduct a "token" search in SPL vs CQL

**Splunk**

```index=foo sourcetype=bar token```

**CQL**

```#event_simpleName=foo token``` 

Notes: NA

## Logic Operators (AND vs and)
Description: To conduct a "token" with two conditions present search in SPL vs CQL. The "AND" in splunk is capital while the "and" in CQL is lowercase. Both are implicit with a space " " 

**Splunk**

```index=foo sourcetype=bar token1 token2```

**CQL**

```#event_simpleName=foo token1 token2``` 

Notes: In both splunk and CS the "AND"/"and" is implicit with a " " space

## Logic Operators (NOT)
Description: To conduct a conitional search in SPL vs CQL where NOT is used

**Splunk**

```index=foo sourcetype=bar token1 NOT token2```

**CQL**

```#event_simpleName=foo token1 not token2``` 

```#event_simpleName=foo token1 !token2```

Notes: In both splunk and CS the not term, but in CQL lowercase. Additional functionality not present in SPL is, !token which uses the "!" as a not as well.
## Logic Operators (NOT field=value)
Description: To conduct a conitional search in SPL vs CQL where NOT is used

**Splunk**

```index=foo sourcetype=bar token1 NOT field=value```

```index=foo sourcetype=bar token1 field!=value```

**CQL**

```#event_simpleName=foo token1 not field=value``` 

```#event_simpleName=foo token1 field!=value```

Notes: In both splunk and CS the syntax is nearly identical.
## Comparison Operators
Description: These are identical to Splunk.

**CQL/Splunk**

```field < value```

```field <= value```

```field = value```

```field != value```

```field >= value```

```field > value``` 

## Create New Field
Description: To make a new field from a value in the search use the following syntax.

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
+ one \ needed to escape single "\\"
