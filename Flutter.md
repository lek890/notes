## Flutter

1. Cannot connect to service protocol

For Android, Have you added internet permission in android manifest file?.

<uses-permission android:name="android.permission.INTERNET"/>
For iOS,

in Info.plist

<key>NSAppTransportSecurity</key>
<dict>
<key>NSAllowsArbitraryLoads</key>
<true/>
</dict>

2. Verbose for error

flutter run -v

3. to repair
   flutter packages pub cache repair

4. state management
   blocs > repositories > providers > models
