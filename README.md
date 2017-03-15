# ImagePicker
A simple Image picker for android to simplify the process of getting an image from different sources

* Permissions:
```
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.CAMERA" />
<uses-feature android:name="android.hardware.camera" />
<uses-feature android:name="android.hardware.camera.autofocus" />
```

* Usage in fragment:
```
private void selectImage() {
    Intent takeImageIntent = ImagePicker.getPickImageIntent(this);
    if (takeImageIntent.resolveActivity(getActivity().getPackageManager()) != null) {
        startActivityForResult(takeImageIntent, REQUEST_IMAGE_CAPTURE);
    }
}
```
* Usage in Activity:
```
private void selectImage() {
    Intent takeImageIntent = ImagePicker.getPickImageIntent(this);
    if (takeImageIntent.resolveActivity(this.getPackageManager()) != null) {
        startActivityForResult(takeImageIntent, REQUEST_IMAGE_CAPTURE);
    }
}
```
```
@Override
protected void onActivityResult(int requestCode, int resultCode, Intent data) {
    Bitmap bitmap = ImagePicker.getBitmapFromResult(this, resultCode, data);
    if (null != bitmap && resultCode == RESULT_OK) {
    //do what you want with the bitmap here

   }
}
```
* To Write a bitmap to jpeg:
```
    // Write Bitmap to /storage/images
    String savedTo = ImagePicker.writeImage(getContext(), bitmap, imageName);
```
* To Read a jpeg into a bitmap:
```
    // Read Bitmap from /storage/images
    Bitmap bitmap = ImagePicker.readImage(getContext(), imageName);
```
# Note
Please creadit the developer in your app if you like the library
