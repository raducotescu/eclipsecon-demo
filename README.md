Using OSGi for script deployment in Apache Sling
====

This repository hosts a set of PoC modules, based on [0], meant to support the "Using OSGi for script deployment in Apache Sling" [1]
presentation from EclipseCon 2019.

The purpose of this demo is to show how a Sling instance can be developed in a cloud friendly way,
with a remote content store provided by storage services (e.g. Dropbox, Google Drive, Box, OneDrive, etc.). Application code is provided
solely through bundles, including the component scripts which are now precompiled as opposed to being provided by the content store.

Available modules:
1. [`org.apache.sling.remote.resourceprovider`](./org-apache-sling-remote-resourceprovider) - new API for exposing remote files and folders
as `Resources` in the Sling tree
2. [`org.apache.sling.remote.resourceprovider.dropbox`](./org-apache-sling-remote-resourceprovider-dropbox) - a Dropbox implementation of
the API from 1.
3. [`org.apache.sling.mini`](./org-apache-sling-mini) - builds a Sling feature providing most of the core bundles needed to build a web
application, with the exception of a `ResourceProvider` and a `ScriptEngine`
4. [`org.apache.sling.mini.demo.eclipsecon`](./org-apache-sling-mini-demo-eclipsecon) - builds a Sling web application, by extending the feature provided by
`org.apache.sling.mini`
5. [`org-apache-sling-mini-demo-content`](./org-apache-sling-mini-demo-content) - demo content to be deployed on Dropbox for
`org.apache.sling.mini.demo`

[0] - https://github.com/apache/sling-whiteboard/tree/master/it-is-cloudy-here  
[1] - https://www.eclipsecon.org/europe2019/sessions/using-osgi-script-deployment-apache-sling
