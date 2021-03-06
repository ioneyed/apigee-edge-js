# Example Tools for Apigee Edge

These are example tools implemented in nodejs/Javascript, that use the apigee-edge-js library.

They all can retrieve credentials from a .netrc file, or you can pass in user credentials interactively.
Also, they use the OAuth authentication mechanism for Apigee Edge.

## Disclaimer

These tools are not an official Google product, nor are they part of an official Google product, nor are they included under any Google support contract.
Support is available on a best-effort basis via github or community.apigee.com .


# Import a proxy

Import a proxy, using a bundle zip as the source. Derive the name for the proxy from the *.xml in the apiproxy directory:

```
./importAndDeploy.js -n -v -o ORGNAME  -d ../bundles/oauth2-cc.zip
```

Import a proxy, using an exploded directory as the source. Derive the name from the *.xml in the apiproxy directory:
```
./importAndDeploy.js -n -v -o ORGNAME  -d ../bundles/oauth2-cc
```

Import, but override the name specified in the proxy XML file in the apiproxy dir:

```
./importAndDeploy.js -n -v -o ORGNAME  -d ../bundles/oauth2-cc  -N demo-oauth2-cc
```


# Import and Deploy a proxy

Deploy to one environment:
```
./importAndDeploy.js -n -v -o ORGNAME  -d ../bundles/protected-by-oauth -e test
```
Deploy to multiple environments:

```
./importAndDeploy.js -n -v -o ORGNAME  -d ../bundles/protected-by-oauth -e test,prod
```


# Import and Deploy a sharedflow

```
./importAndDeploy.js -n -v -o ORGNAME  -d ../bundles/sharedflow-1 -e main -S
```

# Create a product

```
./provisionApiProduct.js -n -v -o ORGNAME  -p demo-protected-by-oauth -N Demo-Product-1
```


# Create a developer

```
 ./createDeveloper.js -n -v -o ORGNAME -E dchiesa+2017@google.com -F Dino -L Chiesa
```

# Create a developer app

```
./createDeveloperApp.js -n -v -o ORGNAME -N DemoApp1 -E dchiesa+2017@google.com -p Demo-Product-1
```


# Delete a developer app

```
./deleteDeveloperApp.js -n -v -o ORGNAME -N DemoApp3 -E dchiesa+2017@google.com
```


# Export a set of proxies with a name matching a RegExp pattern

```
./exportApi.js -n -v -o ORGNAME -P ^r.\*
```

If you  want to just see which proxies would be exported, you can use the -T option.

```
./exportApi.js -n -v -o ORGNAME -P ^r.\* -T
```


# Export all proxies in an org

This just uses a regex pattern that matches all names.

```
./exportApi.js -n -v -o ORGNAME -P .
```


# Export a single named proxy

In lieu of the -P (pattern) option you can use -N (name) for a specific proxy.


```
./exportApi.js -n -v -o ORGNAME -N runload
```

By defaut the script will export the latest revision of the proxy.
If you know  the revision you'd like to export, you can use the -R option to specify it.


```
./exportApi.js -n -v -o ORGNAME -N runload -R 3
```

