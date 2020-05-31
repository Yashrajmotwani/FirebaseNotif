# FirebaseNotif

After creating app on firebase and downloading google-services.json file, we need to add dependencies in both the build.gradle files.

Then in command Prompt, we need to write

npm install --save react-native-firebase

Then we need to link it

react-native link react-native-firebase

This didnt link properly for me though, so I had to add, in the MainActivity.java

import io.invertase.firebase.RNFirebasePackage;

import io.invertase.firebase.messaging.RNFirebaseMessagingPackage;

import io.invertase.firebase.notifications.RNFirebaseNotificationsPackage;

@Override

protected List<ReactPackage> getPackages() {

return Arrays.<ReactPackage>asList(

new MainReactPackage(),

new RNFirebasePackage(),

new RNFirebaseMessagingPackage(),

new RNFirebaseNotificationsPackage()

);                               

}

After this I had to had, the following to the settings.gradle file

include ':react-native-firebase'                       

project(':react-native-firebase').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-firebase/android')

And then this to the build.gradle file

dependencies {

   compile(project(':react-native-firebase')) {   
       
       transitive = false
   
   }

}

Then we go to firebase, and send message from there.
