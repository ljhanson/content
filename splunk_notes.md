---
title: Splunk Notes
slug: splunk-notes
date: 2019-11-08
---

## Splunk Components

- Indexer - Process, stores and creates events.  Does this via time stamped directories.
- Search Head - Front End, consolidate and enrich results
- Forwarder -  Agent that sends data to indexer
  - These three represent the minimal install of splunk.
- Deployment Server
- Cluster Master
- License Master

## Roles

- Admin
  - Can install apps, and create knowledge objects
- Power
  - Can create and share knowledge objects for app users and do realtime searches.
- User
  - Will only see own knowledge objects and those shared with them.

## Links

[Splunkbase](https://splunkbase.splunk.com) - App store for Splunk
[Splunk Howto's](https://www.splunk.com/en_us/resources/videos.html#How-To)
[Splunk Documentation](https://docs.splunk.com)

## Splunk Index Time Process

- Input Phase
  - Handled at source (Usually the Forwarder)
  - Data sent as stream, any config applies to whole stream
- Parsing Phase
  - Handled by Indexer or Heavy Forwarder
  - Datastream broken into events
  - Advanced processing **can** occur
  - Indexing Phase
    - License meter runs as data and is initially written to disk, prior to compression
    - Can't be changed after written

## Index's

- Index's are directories where data will be stored.
- Separate index can be more efficient
- Allow access limits
- Allow Different retention policies

## Searching

- Limit by time is best practice
- Commands that create starts and visualizations are called transforming commands
- Search jobs active for 10 minutes by default, Shared jobs are good for 7 days.
- Search Modes
  - Fast
    - default fields and only those necessary for search
    - Field Discovery disabled
  - Smart
    - Default
    - Toggles based on what’s being queried.
  - Full/Verbose
    - Everything possible
- Zoom in is original job
- Zoom out is new job
- “\*” (Finish string), AND, OR, NOT all work
- Parentheses are for order of operations
- Quotes for exact phrases
- “\\” to escape characters
- Before first “|” looks for matching terms, after pipe looks for commands
- Results displayed revers chronologically
- Time Ranges

| Unit | Abbreviation |
| :--- | :--- |
| seconds | s|
| minutes | m |
| hours | h |
| days | d |
| week | w |
| months | mon |
| years | y |

- “@“ used to snap to time unit specified
  - Rounds **down**
- Time range can be specified using earliest and latest
- Search job permissions and lifetime can be changed

## Fields

- Fields are Key/Value pairs
- Interesting fields are fields that are present in 20% or more of the events yout search returned.
- ‘*a*’ signifies string fileds
- ‘#’ denotes number fields
- Filed names are case sensitive, values are not
- “=“ and “!=“ can be used for both numeric and string values
- “>, \<, >=, \<=“ Can only be used for numeric values.
- Can use “IN’ rather than chaining.
  - e.g. “status IN (“500”, “503”)
- subnet/CIDR aware for searches
- != vs. NOT
  - Both exclude events
  - != returns events where field exists and value doesn’t equal query
  - NOT returns events where filed exists and value doesn’t equal query **and all events that field doesn’t exist**
  - Only same when field always exists in data.

## Best Practices

- Time is most critical
- Second Tier
  - index
  - host
  - source
  - sourcetype
- More you tell, better results
- inclusion, better than exclusion
- Filter early
- Avoid wildcards at beginning or middle of string
- When possible use OR instead of wildcards

## Splunk Search Language (SPL) Fundamentals

- “|” works like UNIX pipes for searches
- Ctrl|Command + “\\” moves pipes to new lines
- Field extraction is costly and only affects displayed results
- table command creates nicely formatted tables of results
- rename command renames field names in display
  - have to use new name in subsequent commands
  - renames needed to be quoted
- dedup command removes duplicate results
  - Can be filed specific
- Sort, ascending or descending order
  - \+ is ascending, \- is descending
  - space between operator and field name makes it affect all
  - can use limit as part of sort

[Search Reference](http://docs.splunk.com/Documentation/Splunk/latest/SearchReference)
[Search Quick Reference](http://docs.splunk.com/Documentation/Splunk/latest/SplunkEnterpriseQuickReferenceGuide)

## Transforming Commands

- Top - Most common
- Rare - Least common
- Stats
  - count
  - distinct_count (same as count but unique only)
  - sum
  - avg
  - min
  - max
  - list
  - values (same as list but unique values only)

### Stats must be in same pipe or event may no longer be present in pipeline

- Tables created with stats commands can be formatted

## Dashboards and Visualizations

- Best practice is to define naming convention for reports
- Be carefull of permissions on who report runs as to prevent inadvertent disclosure
- Time Range picker will only work on panels with inline search
- Reports are saved searches
- Best practice is to create dashboards based off reports, as a change in a report updates every dashboard the uses it.

## Pivots and Datasets

- Data Models are knowledge objects that provide the data structures that drives pivots
  - Created by Admin and Power User
- Represented as tables
- Think of as slices of data
- Like and “AND’ in SQL
- Instant Pivot creates data model without query language
- Datasets help users find data and get answers faster

## Lookups

- Like vlookup in Excel
- Categorized as Dataset
- Setup
  - Define table
  - Define lookup
- Automatic lookup will do lookup in searches by default
- outputnew can be used as clause to avoid overwriting existing fields

## Scheduled Reports and Alerts

- Be careful with demand caused by reports
  - Use priority to manage
    - only done by admin
  - Use window for flexible start
- Managed via settings
- Embedded reports are viewable by ##ANYONE## who can access the webpage.
- Alerts are continuously running searches
