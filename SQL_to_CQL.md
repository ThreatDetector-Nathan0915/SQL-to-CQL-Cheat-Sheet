# To help all splunkers in Splunk Processing Language (SPL) who have been forced to adopt Crowdstrike Query Language (CQL)
## Basic Field Search
Description: To conduct a basic search in SPL vs CQL

**Splunk**

```index=foo sourcetype=bar field=value```

**CQL**

```#event_simpleName=foo field=value``` 

Notes: No need to define index or sourcetype, there is only CS just search off event_simpleName "#" is required.

## Token Search (unsupported)
Description: Crowdstrike does not support token search like in Splunk.

**Splunk**

```index=foo sourcetype=bar token```

**CQL**

```N/A``` 

Notes: NA

## Logic Operators (AND vs and)
Description: To conduct a query with two conditions present search in SPL vs CQL. The "AND" in splunk is capital while the "and" in CQL is lowercase. Both are implicit with a space " " 

**Splunk**

```index=foo sourcetype=bar field1=value field2=value ```

```index=foo sourcetype=bar field1=value AND field2=value ```

**CQL**

```#event_simpleName=foo field1=value field2=value``` 

```#event_simpleName=foo field1=value and field2=value``` 

Notes: In both splunk and CS the "AND" "and" is implicit with a " " space

## Logic Operators (NOT)
Description: To conduct a conditional search in SPL vs CQL where NOT is used

**Splunk**

```index=foo sourcetype=bar field1=value NOT field2=value```

**CQL**

```#event_simpleName=foo field1=value not field2=value``` 

```#event_simpleName=foo field1=value !field2=value```

Notes: In both splunk and CS the not term, but in CQL lowercase. Additional functionality not present in SPL is, !field which uses the "!" as a not as well.

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

## Wild-Card Field Search
Description: In Splunk alot of times you want a field to have value but you're unsure what the at value is. Here's how you do it in SPL vs CQL
**Splunk**

```| field=*```

**CQL**

```| field=?field``` 

Note: the "*" wild card is used in SPL, where in CQL you call the field again but with a "?" leading.

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

## Table Results
Description: To table fields from the results of a search in SPL vs CQL

**Splunk**

```| table field1 field2 field3 field4```

**CQL**

```| select([field1, field2, field3, field4])``` 
## Stats Count
Description: Stats is very powerfull in splunk na dcan be used to corelate and filter results, in CQL "group" is the equivalent.

**Splunk**

```| Stats count by field```

**CQL**

```| groupBy([field], limit=max)``` 

Notes: This is a very simple example and it can get exponentially more complex. But just as a starter they both do the same thing they group results by the chosen field. With the caveat that CQL has a limit of 20k results so if you want more than that you must define a greater limit with ", limit=max"
