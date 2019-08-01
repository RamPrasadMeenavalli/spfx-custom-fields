## spfx-custom-fields

This SPFx package is for demonstrating how to deploy a Field Customizer without provisioning a custom field in the solution. And use the installed Field Customizer on an existing column.

### Building the code

```bash
git clone the repo
npm i
npm i -g gulp
gulp clean
gulp build
gulp bundle --ship
gulp package-solution --ship
```

This package produces the following:

* sharepoint/solution/solutio-name.sppkg - The app package file

Add this package to the App Catalog and publish/install the app.
### Create a list and add the Field Customizer

Create a list. A single line of text column is need, to which we will associate the Field Customizer.
Run the following PnP Powershell code to associate the extension
```Powershell
$list = Get-PnPList -Identity $listTitle  
$fld = Get-PnPField -List $list -Identity $fieldTitle  
$fld.ClientSideComponentId = "0407eb29-728c-47c3-9f9b-bb1d2e04c4cc"  
$fld.Update()  
Invoke-PnPQuery 
```
