Android work is in progress. 

Add the plugin
```
tns plugin add nativescript-http-formdata
```
Usage

```
import { TNSHttpFormData, TNSHttpFormDataParam } from 'nativescript-http-formdata';
```
use the ImagePicker plugin or any other.
https://github.com/NativeScript/nativescript-imagepicker

```
  private test() {
    let context = imagepicker.create({
        mode: "single" // use "multiple" for multiple selection
    });
    context.authorize()
    .then(function() {
        return context.present();
    })
    .then((selection) => {
      let item = selection[0];
      item.getImageAsync((image: UIImage, error) => {
        // console.dir(image);
        let imageData = UIImagePNGRepresentation(image);
        let fo = new TNSHttpFormData();

        let params = [];
        let param: TNSHttpFormDataParam = {
          data: imageData,
          contentType: 'image/png',
          fileName: 'test.png',
          parameterName: 'file1'
        };
        params.push(param);

        fo.upload('http://10.10.10.154:10011/home/fileupload', params)
        .then((isUploaded) => {
          console.log('isUploaded: ' + isUploaded);
        }, (error) => {
          console.log(error);
        });
      });

      // let assetLibrary = ALAssetsLibrary.alloc().init();
      // assetLibrary.assetForURLResultBlockFailureBlock(item.)
    }).catch(function (e) {
        alert(e);
    });
  }
  ```
