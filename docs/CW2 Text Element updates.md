# Download binary from browser

All changes are done in Text element. A new attribute value for `Style` attribute is added. 

A couple of new functions are available in exposeObject (and rwItem). 

The flow is following:

`<input type="file" ... >` is used as file  upload element in browser. 

`FileReader` HTML5 API is used for reading the selected file to binary content in browser main thread. 

A blob with internal url is created. the url is sent to the webworker (runtimeworker). 

The runtimeworker instance of the text element triggers if the value of the text element is an url and if the text element is configured as a file element. 

the blob is read from ram and if someone has registered the `onFileChange` callback function on the text elment, that callback function is called with blob as first parameter. 

The download link is also a text element. both file and value attribute is updated, and the element is already configured as an `OpenLink` click action. Via file attribute, the url is updated and used in a custom openlink call in `OnManeuver`. 

## Changes in Text element

### `this.file()`

Method. 

Text element is enhanced with new get/set method for file attribute.

How to configure Text element for file download:

Set following attributes:

- Name: `downloadlink` (or other name)

- ManeuverStyle: `Editable`

- ManeuverAccess: `None`  (or desired access)

- VisibleAccess: `None` (or desired access)

- ShowTitle: `No`

- Value: `Waiting for file to download...` (or other initial text)

- ClickAction: `Custom`

- OnManevuer: 
  ```this.session.openLink( 
  this.session.openLink{
   file: this.file(), //this is the important part, here we get the current dynamically set url for file. 
   target: 'link',
   name: 'TxtDesign_LinkInBrowser',
   openedFrom: this
  }
  ,
  {});
  ```

In another  element,  use `this.view.downloadlink.file(newUrl)` and `this.view.downloadlink.value('Click here to download!');` to both set the new file url to which the elements openlink file attribute sets to, and to set/change the caption of the textelement value. 



### `this.onFileChanged(callbackfn)`

Method.

Text element is enhanced with new get/set method for a file change callback. 

The text element has a new style attribute `file` (among `text` and `password`). 

How to configure the text element for file upload (from device to browser):

Set following attributes on the newly created text element: 

- Name: `fileupload` (or other name)
- ManeuverStyle: `Editable`
- ManeuverAccess: `None`  (or desired access)
- Style: `file`
- VisibleAccess: `None` (or desired access)
- ShowTitle: `No`
- Value: `Select file` (or other initial text)
- OnOpen: 

```
const me = this;
this.onFileChange(function(blob){
    const url = URL.createObjectURL(blob); // create valid url link from blob
    me.view.downloadlink.file(url); //assign the url to 
    me.view.downloadlink.value("Download file!");
})
```





Complete view example:

```xml
<?xml version="1.0" encoding="utf-8"?>
<EXOconfigData format="Rwav" version="2019.4.100.136">
  <Object type="View">
    <Attribute name="Name">Default</Attribute>
    <Attribute name="Width">615</Attribute>
    <Attribute name="Height">467</Attribute>
    <Attribute name="Zoom">100%</Attribute>
    <Attribute name="ScaleValue">1</Attribute>
    <Attribute name="ServerSideFunctionRPC">accounts.%account%.services.ssf.execute</Attribute>
    <Object type="ArgumentsFolder">
      <Attribute name="Name">Arguments</Attribute>
      <Attribute name="Comment">This folder contains all arguments for the view. The arguments can be sent to the view when it is used in run-time.</Attribute>
    </Object>
    <Object type="ElementsFolder">
      <Attribute name="Name">Elements</Attribute>
      <Attribute name="Comment">This folder contains all visual elements for the view.</Attribute>
      <Object type="Text">
        <Attribute name="Name">downloadlink</Attribute>
        <Attribute name="ShowTitle">No</Attribute>
        <Attribute name="Value">Waiting for file to download...</Attribute>
        <Attribute name="ManeuverStyle">ClickOnly</Attribute>
        <Attribute name="Access">None</Attribute>
        <Attribute name="ClickAction">Custom</Attribute>
        <Attribute name="FontSize">XLarge</Attribute>
        <Attribute name="VisibleAccess">None</Attribute>
        <Attribute name="Left">135</Attribute>
        <Attribute name="Top">120</Attribute>
        <Attribute name="Width">265</Attribute>
        <Attribute name="Height">35</Attribute>
        <Attribute name="OnOpen">debugger;this.file("testing testing");</Attribute>
        <Attribute name="OnManeuver">debugger;
this.session.openLink( 
{
 file: this.file(),
 target: 'link',
 name: 'downloadlink_LinkInBrowser',
 openedFrom: this
}
,
{

}
);</Attribute>
      </Object>
      <Object type="Text">
        <Attribute name="Name">upload</Attribute>
        <Attribute name="ShowTitle">No</Attribute>
        <Attribute name="Value">No file selected</Attribute>
        <Attribute name="ManeuverStyle">Editable</Attribute>
        <Attribute name="Access">None</Attribute>
        <Attribute name="Style">password</Attribute>
        <Attribute name="VisibleAccess">None</Attribute>
        <Attribute name="Left">140</Attribute>
        <Attribute name="Top">80</Attribute>
        <Attribute name="Width">260</Attribute>
        <Attribute name="Height">20</Attribute>
        <Attribute name="OnOpen">const me = this;
this.onFileChange(function(blob){
    const url = URL.createObjectURL(blob);
    me.view.downloadlink.file(url);
    me.view.downloadlink.value("Download uploaded file");
})</Attribute>
      </Object>
    </Object>
  </Object>
</EXOconfigData>
```

