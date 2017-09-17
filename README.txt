Knopflerfish OSGi framework bundle, forked from 
https://github.com/knopflerfish/knopflerfish.org

Modified for compatibility with OGEMA:
https://github.com/ogema/ogema

Build: 
mvn clean install

Changes:
 * SecurityManager & FrameworkPolicy: avoid endless loop during class loading with activated security
   -- use default security manager for FilePermission checks
   -- shortcut permission checks for system bundle classloader
 * PermissionOps & FrameworkContext: enable limited permission checks for user login even if security is disabled
   -- register ConditionalPermissionAdmin even if security is inactive
 * SystemBundle: ensure org.osgi.* packages are exported
   -- additional package exports read from included file
 * FrameworkContext: fixed an error when a second framework instance is launched in the same VM
   -- on init, clear URL.class and URLConnection.class static variables by reflection, to 
 	enable a reinitialisation