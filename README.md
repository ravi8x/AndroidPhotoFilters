# Android Photo Filters

[ ![Download](https://api.bintray.com/packages/androidhive-info/maven/imagefilters/images/download.svg) ](https://bintray.com/androidhive-info/maven/imagefilters/_latestVersion)
[ ![Example](https://img.shields.io/badge/Example-Instagram%20Filters-green.svg)](https://www.androidhive.info/2017/11/android-building-image-filters-like-instagram/)

This library is forked from [here](https://github.com/Zomato/AndroidPhotoFilters). All credits goes to respective owners.

An example article demonstrating Instagram Like Interface can be found [here](https://www.androidhive.info/2017/11/android-building-image-filters-like-instagram/)

![Instagram Filters](https://www.androidhive.info/wp-content/uploads/2017/11/android-instagram-filters-youtube-min.jpg)

## How to use the Library

1. Include the Filters library in build.gradle
```java
dependencies {
    implementation fileTree(dir: 'libs', include: ['*.jar'])
    // ...
 
    implementation 'info.androidhive:imagefilters:1.0.7'
}

```

2. Load the native library in your activity
```java
public class MainActivity extends AppCompatActivity {
    static
    {
        System.loadLibrary("NativeImageProcessor");
    }
```

3. Get the pre defined Filter Pack to generate the thumbnails. Refer [FilterPack.java](https://github.com/ravi8x/AndroidPhotoFilters/blob/master/imagefilters/src/main/java/com/zomato/photofilters/FilterPack.java) to generate your own filters.
```java
List<filter> filters = FilterPack.getFilterPack(getActivity());
 
for (Filter filter : filters) {
        ThumbnailItem item = new ThumbnailItem();
        item.image = thumbImage;
        item.filter = filter;
        item.filterName = filter.getName();
        ThumbnailsManager.addThumb(tI);
}
```

4. Apply desired filter on to bitmap image.
```java
// Accessing single filter...
Bitmap bitmap = your_bitmap_;
Filter clarendon = FilterPack.getClarendon();
// apply filter
imagePreview.setImageBitmap(filter.processFilter(bitmap));
```

## The Filter Pack

Currently the below filters are available in filer pack. More will be added in future.

<table border="0" width="100%" class="center-align">
<tbody>
<tr>
<td><img src="https://www.androidhive.info/wp-content/uploads/2017/11/struck-min.jpg" alt="" width="230" height="230" class="alignnone size-full wp-image-41227" /><em>Struck</em></td>
<td><img src="https://www.androidhive.info/wp-content/uploads/2017/11/clarendon-min.jpg" alt="" width="230" height="230" class="alignnone size-full wp-image-41226" /><em>Clarendon</em></td><td><img src="https://www.androidhive.info/wp-content/uploads/2017/11/oldman-min.jpg" alt="" width="230" height="230" class="alignnone size-full wp-image-41225" /><em>OldMan</em></td>
</tr>
<tr>
<td class="center"><img src="https://www.androidhive.info/wp-content/uploads/2017/11/mars-min.jpg" alt="" width="230" height="230" class="alignnone size-full wp-image-41224" /><em>Mars</em></td>
<td><img src="https://www.androidhive.info/wp-content/uploads/2017/11/rise-min.jpg" alt="" width="230" height="230" class="alignnone size-full wp-image-41223" /><em>Rise</em></td><td><img src="https://www.androidhive.info/wp-content/uploads/2017/11/april-min.jpg" alt="" width="230" height="230" class="alignnone size-full wp-image-41222" /><em>April</em></td>
</tr>
<tr>
<td class="center"><img src="https://www.androidhive.info/wp-content/uploads/2017/11/amazon-min.jpg" alt="" width="230" height="230" class="alignnone size-full wp-image-41221" /><em>Amazon</em></td>
<td><img src="https://www.androidhive.info/wp-content/uploads/2017/11/starlit-min.jpg" alt="" width="230" height="230" class="alignnone size-full wp-image-41220" /><em>Starlit</em></td><td><img src="https://www.androidhive.info/wp-content/uploads/2017/11/whisper-min.jpg" alt="" width="230" height="230" class="alignnone size-full wp-image-41219" /><em> Whisper</em></td>
</tr>
<tr>
<td class="center"><img src="https://www.androidhive.info/wp-content/uploads/2017/11/lime-min.jpg" alt="" width="230" height="230" class="alignnone size-full wp-image-41218" /><em>Lime</em></td>
<td><img src="https://www.androidhive.info/wp-content/uploads/2017/11/haan-min.jpg" alt="" width="230" height="230" class="alignnone size-full wp-image-41217" /><em>Haan</em></td><td><img src="https://www.androidhive.info/wp-content/uploads/2017/11/bluemess-min.jpg" alt="" width="230" height="230" class="alignnone size-full wp-image-41216" /><em> Bluemess</em></td>
</tr>
<tr>
<td class="center"><img src="https://www.androidhive.info/wp-content/uploads/2017/11/adele-min.jpg" alt="" width="230" height="230" class="alignnone size-full wp-image-41215" /><em>Adele</em></td>
<td><img src="https://www.androidhive.info/wp-content/uploads/2017/11/cruz-min.jpg" alt="" width="230" height="230" class="alignnone size-full wp-image-41214" /><em>Cruz</em></td><td><img src="https://www.androidhive.info/wp-content/uploads/2017/11/metropolis-min.jpg" alt="" width="230" height="230" class="alignnone size-full wp-image-41213" /><em> Metropolis</em></td>
</tr>
<tr>
<td class="center"><img src="https://www.androidhive.info/wp-content/uploads/2017/11/audrey-min.jpg" alt="" width="230" height="230" class="alignnone size-full wp-image-41212" /><em>Audrey</em></td>
<td>&nbsp;</td><td>&nbsp;</td>
</tr>
</tbody>
</table>

## Features
(This is the older documentation from original page)

PhotoFiltersSDK processes filter on any Image within fraction of second since processing logic is in NDK. At present following image filters are included: 

* **[ToneCurveSubfilter](#tonecurve) :** With this powerful filter you can change RGB channels of any image to create great results.
* **[SaturationSubfitler](#saturation) :** Used for changing color saturation of an image.
* **[ColorOverlaySubfilter](#coloroverlay) :** As name suggests you can overlay any image with color of your choice.
* **[ContrastSubfilter](#contrast) :** Used for changing contrast value of image.
* **[BrightnessSubfilter](#brightness) :** To change brightness levels.
* **[VignetteSubfilter](#vignette) :** To apply vignette effect on image. 

```java
Filter myFilter = new Filter();
myFilter.addSubFilter(new BrightnessSubFilter(30));
myFilter.addSubFilter(new ContrastSubFilter(1.1f));
Bitmap outputImage = myFilter.process(inputImage);
```

Above code snippet will give you outputImage with increased brightness and contrast. You can further refer [example project](example).

## Documentation
Although there are few inbuilt filters already present, you may want to create and customize one specific to your need and show your creativity. For that you would require to know how all the Subfilters can be used. Let me take you through all of them.

### <a name="tonecurve"></a>ToneCurveSubfilter
This is most awesome filter present in this library which differentiates **PhotoFiltersSDK** from other image processing libraries out there. ToneCurveSubFilter applies the changed RGB Channel curve to create effect on image.

![CurveDialog](art/curvedialog_photoshop.png)

Here is the code snippet the apply the above RGB curve on an image : 

```java
Filter myFilter = new Filter();
Point[] rgbKnots;
rgbKnots = new Point[3];
rgbKnots[0] = new Point(0, 0);
rgbKnots[1] = new Point(175, 139);
rgbKnots[2] = new Point(255, 255);
       
myFilter.addSubFilter(new ToneCurveSubfilter(rgbKnots, null, null, null));
Bitmap outputImage = myFilter.process(inputImage);
```

The results are nearly same as we would see in photoshop and other tools. We can also specify knots for Red, Green and Blue channels (in the ToneCurveSubfilter's constructor).

### <a name="saturation"></a>SaturationSubfilter
This fitler can be used to tweak color saturation of an image. Here is the example : 

```java
Filter myFilter = new Filter();
myFilter.addSubFilter(new SaturationSubfilter(1.3f));
Bitmap outputImage = myFilter.process(inputImage);
```

SaturationSubfilter takes float as an argument and has no effect for value 1.

### <a name="coloroverlay"></a>ColorOverlaySubfilter
Increases the specified red, green and blue values for each pixel in an image.

```java
Filter myFilter = new Filter();
myFilter.addSubFilter(new ColorOverlaySubfilter(100, .2f, .2f, .0f));
Bitmap outputImage = myFilter.process(inputImage);
```

### <a name="contrast"></a>ContrastSubfilter
To change the contrast levels of an image use this filter : 

```java
Filter myFilter = new Filter();
myFilter.addSubFilter(new ContrastSubfilter(1.2f));
Bitmap outputImage = myFilter.process(inputImage);
```

ContrastSubfilter takes float as an argument where value 1 has no effect on the image.

### <a name="brightness"></a>BrightnessSubfilter
As the name suggest, this filter is used for changing brightness levels : 

```java
Filter myFilter = new Filter();
myFilter.addSubFilter(new BrightnessSubfilter(30));
Bitmap ouputImage = myFilter.process(inputImage);
```
BrightnessSubfilter takes int as an argument where value 0 has no effect. Negative values can be used to decrease brightness of the image.

### <a name="vignette"></a>VignetteSubfilter
This filter can be used to put vignette effect on the image. 

```java
Filter myFilter = new Filter();
myFilter.addSubFilter(new VignetteSubfilter(context, 100));
Bitmap outputImage = myFilter.process(inputImage);
```

VignetteSubfilter takes int as an argument whoes value ranges from 0-255, which defines intesity of the vignette effect.

## Proguard
If you are using proguard, consider adding the following to your proguard rules:

```proguard
-keep class com.zomato.photofilters.** {*;}
-keepclassmembers  class com.zomato.photofilters.** {*;}
```

## License
This library falls under [Apache v2](LICENSE)
