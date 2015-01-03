Fork of https://github.com/chocolatey/chocolatey

The intention of this fork is is to add features / do changes that are needed for my companys use of Chocolatey.

Hopefully some of these changes will make it to master.

First (and for the time only) feature is this:

Add support for .run packages.

.run packages are pure scripts. The packages are not installed to lib\ folder, but in every other aspects they are identical to ordinary packages.

For ordinary packages, this is what happens during install:
  1. The package is downloaded to lib
  2. tools\chocolateyinstall.ps1 script is executed.
     This script will usually (but not always) download installer application from web, and execute it with silent args.
  3. Shims are created for any .exe file found in package. (unless .ignore file is present)
  (If any of above fails, package is moved to lib-bad)

When a package has the extension '.run' this happens instead:
  1. The package is downloaded to lib-run
  2. tools\chocolateyinstall.ps1 script is executed
  3. Package is removed from lib-run
   

  
