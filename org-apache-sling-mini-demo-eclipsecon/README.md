Apache Sling Mini - Demo EclipseCon Project
====

The Apache Sling Mini - Demo EclipseCon Project showcases how to build a Sling instance capable of rendering
a website based on remote resources stored in a Dropbox folder.

This feature extends Apache Sling Mini with the bundles found in [./src/main/features](./src/main/features), which can
be summarised to:
1. the Dropbox Remote Storage Provider
2. the Apache Sling Scripting Bundle Tracker, which allows executing precompiled scripts for rendering
3. the HTL script engine and runtime, with support for precompiled scripts
4. the actual application code (in this case only HTL scripts)

In order to run the application, first follow the steps from
[`org-apache-sling-remote-resourceprovider-dropbox`](../org-apache-sling-remote-resourceprovider-dropbox)
to set up a Dropbox application.
Copy the generated access token into the `dropbox.accesstoken` file.

Copy the content from [`org-apache-sling-mini-demo-content`](../org-apache-sling-mini-demo-content) into the Dropbox
application folder you created above. Make sure the `.sling.json` files are present in your Dropbox folder when copying
the content.

Run `mvn clean install` to create the needed Docker image.

Run `docker-compose -f docker-compose-1.yml up` from this folder and go to
[http://localhost/content/demo/menu.html](http://localhost/content/demo/menu.html).

To test script resolution (or better said how requirements are not satisfied) run the following commands:

```bash
    mvn clean install -Pwebapp-2
    docker-compose -f docker-compose-2.yml up
```

Notice how the http://localhost/content/demo/menu.html URL will provide a resource dump rendering instead of the previous content. On top
of that, head over to http://localhost/system/console/bundles and notice the state of the `org.apache.sling.mini.demo.coffee` bundle. Check
the `docker-compose` logs to see the resolving error.
