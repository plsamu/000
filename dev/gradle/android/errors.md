# Errors

```
The minCompileSdk (31) specified in a
    dependency's AAR metadata (META-INFcomandroidbuildgradleaar-metadata.properties)
    is greater than this module's compileSdkVersion (android-30).
```

Try to downgrade the dependencies:

```
implementation 'androidx.core:core-ktx:1.6.0'
implementation 'androidx.appcompat:appcompat:1.4.0'
implementation 'com.google.android.material:material:1.4.0'

implementation 'androidx.constraintlayout:constraintlayout:2.1.3'
testImplementation 'junit:junit:4.13.2'
androidTestImplementation 'androidx.test.ext:junit:1.1.3'
androidTestImplementation 'androidx.test.espresso:espresso-core:3.4.0'
```
