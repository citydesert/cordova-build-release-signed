# cordova-build-release-signed
#how to build android app using cordova and sign release 
# to create a release go to your project folder in CMD and enter this code
`cordova build --release android`
# generate a key to sign your build by entering this command and follow steps>
`keytool -genkey -v -keystore myKey.keystore -alias myKeyAlias -keyalg RSA -keysize 2048 -validity 10000`
#this command generated file named myKey.keystore Keep in in safe place.
#now sign your build by coping generated platforms/android/app/build/output/apk/app-release-unsigned.apk to main project directory (it means myKey.keystore and apk file in the same folder)
# to sign apk run this command
`jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore myKey.keystore app-release-unsigned.apk myKeyAlias`
# now compress signed file and upload it to google play store
`zipalign -v 4 app-release-unsigned.apk signedandcompressed.apk`
