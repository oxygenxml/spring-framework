Steps to creata a patch for a spring framework module:
1. Checkout the tag with the version that you want to pacth. 
E.g. v5.2.9.RELEASE

2. Add the proxy settings in gradle.properties file (it is located in the root folder):
systemProp.http.proxyHost=${httpProxyHost}
systemProp.http.proxyPort=${httpPort}
systemProp.https.proxyHost=${httpsProxyHost}
systemProp.https.proxyPort=${httpsPort}

3. In the same file, gradle.properties, update the version property to w.x.y.z.OXYGEN-PATCHED. 
E.g. version=5.2.9.1.OXYGEN-PATCHED

4. Modify the files for the module you want to create the patch.

5. Open a terminal in the root folder and run the following command:
gradlew -x test -x checkstyleTest clean :${module_name}:build
E.g for srping-web module: gradlew -x test -x checkstyleTest clean :spring-web:build

6. The jar should be created in {$module_name}/build/libs

7. Deploy the jar on maven.

## License

The Spring Framework is released under version 2.0 of the [Apache License](https://www.apache.org/licenses/LICENSE-2.0).
