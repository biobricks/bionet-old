
Project currently undergoing pre-alpha testing.

Code will appear here later in 2016.

# About

bionet will be a global decentralized system for inventory tracking and for the free exchange of physical biomaterials. 

bionet will be an asynchronous versioned network for sharing and collaborating on biological data.

bionet will be a web app.

bionet will be a command line tool.

# Inventory tracking features

Expect the following features in the first public release:

* Lab inventory tracking: Create/edit/lookup/search of items and their locations.
* Permissions system: Users can grant other users read/write/admin access on their projects
* Versioned data sharing: Users can share data with automatic tracking of all changes.
* Web-based crytube scanning: Ability to scan cryo tube barcodes (DataMatrix) directly from the web app with a smartphone.
* Plate reader integration: Ability to scan full 96 well plates of barcoded tubes using hardware built from off-the-shelf parts.
* Label printing integration: Integration with cheap off-the-shelf thermal label printer that generates and prints labels with QR codes and human readable text/symbols
* Open Source: Everything will be released under an Open Source license

Working features as of this commit: Everything listed above except for the cryotube scanning and plate reader is in a working state.

# Technology

bionet will be an offline-capable web app that uses replication of merkle-DAGs between clients and servers and between servers and servers for most types of communication. Think git but with continous replication and capable of versioning schemaless databases as well as files/directories supporting both the git-style "one merkle-DAG per repository" model and the wiki-style "one merkle-DAG per document/file/object" model. In addition, bionet will provide a flexible (but optional) web front-end that allows users to write their own visualizations/widgets for custom data types that are sandboxesd 

Anyone can run a bionet server, but the idea is that each lab deploys their own server and users create accounts on their home lab's server. The servers take care of continuously replicating data when user's from different servers grant each-other access to their data. There is no reason why the bionet could not fairly easily be made to operate entirely without servers (browser to browser) except that it's problematic when all the browser tabs hosting a certain piece of data suddenly get closed because the users decided to shut down their laptops.

# Modules and libraries

bionet is built with node.js and browserify and uses levelup with leveldb as the default back-end on the server and IndexedDB in the browser. 

bionet loads the entire web app into the client on first "boot" using hyperboot and uses a single websocket connection for all communications between server and client. rpc-multistream is used to allow transparent RPC between client and server and multiplexes both binary, object and text streams onto this single socket. rpc-multiauth is used for authentication.

See the package.json for some of the currently used node modules (not entirely up to date).

# Who

bionet is being developed by the [BioBricks Foundation](https://biobricks.org/)

# When

Expect a beta launch announcement at the 2016 iGEM jamboree.

# License and copyright

License: AGPLv3

Copyright 2016 BioBricks Foundation



