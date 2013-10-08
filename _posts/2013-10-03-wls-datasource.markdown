---
layout: post
title:  "Create a WebLogic DataSource with WLST"
date:   2013-10-04
categories: weblogic datasource wlst
---
I. Set your MW_HOME environment variable

``
export MW_HOME=/Developer/oracle/wls12120 
``

II. From your "wlst-datasource" directory:

``
$ . $MW_HOME/wlserver/server/bin/setWLSEnv.sh
``

Notice the "." before invoking setWLSEnv.sh.

III. Change the ds.properties file accordingly and can call

``java weblogic.WLST create-ds.py``

You should see an output similar to:

```
Initializing WebLogic Scripting Tool (WLST) ...

Welcome to WebLogic Server Administration Scripting Shell

Type help() for help on available commands

@@@ Starting the script ...
Connecting to t3://localhost:7001 with userid weblogic ...
Successfully connected to Admin Server "AdminServer" that belongs to domain "base_domain".

Warning: An insecure protocol was used to connect to the
server. To ensure on-the-wire security, the SSL port or
Admin port should be used instead.

Location changed to edit tree. This is a writable tree with
DomainMBean as the root. To make changes you will need to start
an edit session via startEdit().

For more help, use help('edit')

Starting an edit session ...
Started edit session, please be sure to save and activate your
changes once you are done.
Resource Name: SampleDataSource
MBean type JDBCSystemResource with name SampleDataSource has been created successfully.
JDBC file name: jdbc/SampleDataSource-4141-jdbc.xml
```

Check out the full project at [Github][wlst-datasource].

[wlst-datasource]: https://github.com/gmaggess/wlst-datasource
