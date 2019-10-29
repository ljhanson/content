### Splunk Components
  * Indexer - Process, stores and creates events.  Does this via time stamped directories.
  * Search Head - Front End, consolidate and enrich results
  * Forwarder -  Agent that sends data to indexer
    - These three represent the minimal install of splunk.
  * Deployment Server
  * Cluster Master
  * License Master
    
 
### Roles
* Admin
	* Can install apps, and create knowledge objects
* Power
	* Can create and share knowledge objects for app users and do realtime searches.
* User
	- Will only see own knowledge objects and those shared with them. 

### Links
[Splunkbase](https://splunkbase.splunk.com) - App store for Splunk  
[Splunk Howto's](https://www.splunk.com/en_us/resources/videos.html#How-To)  
[Splunk Documentation](https://docs.splunk.com)  

### Splunk Index Time Process

* Input Phase
	- Handled at source (Usually the Forwarder)
  - Data sent as stream, any config applies to whole stream
* Parsing Phase
        - Handled by Indexer or Heavy Forwarder
        - Datastream broken into events
        - Advanced processing **can** occur
    * Indexing Phase
        - License meter runs as data and is initially written to disk, prior to compression
        - Can't be changed after written

### Index's

- Index's are directories where data will be stored.
- Separate index can be more efficient
- Allow access limits
- Allow Different retention policies