1. ingresar los permisos de internet fuera del modo debug, en `meedu_googlemaps/android/app/src/main/AndroidManifest.xml`
   ```xml
    <uses-permission android:name="android.permission.INTERNET"/>
   ```
2. descargar las librerias de *google maps* en el `meedu_googlemaps/pubspec.yaml`
   ~~~yaml
   dependencies:
        google_maps_flutter: ^2.2.6
   ~~~
   > Documentacion https://pub.dev/packages/google_maps_flutter
   ### Creacion de llaves para utilizar el plugin:
   1. ingresar a https://console.cloud.google.com/apis/
   2. crar un nuevo proyecto 
   3. se seleciona el API y serivcios y se habilita google maps SDK for Android y maps SDK for iso
   4. te diriges a credenciales y creas la API Key, ejemplo:
        ~~~
        AIzaSyAaAlgZK3IYtqPCunILeQtkoMd1o90JYFQ
        ~~~
   5. Restringir las peticiones para que solo sea en alplicacion Android
   6. Definir el certificado de Huella digital del certificado de depuración
      1. Para Linux o macOS:
        ~~~bash
        keytool -list -v -keystore ~/.android/debug.keystore -alias androiddebugkey -storepass android -keypass android
        ~~~
      2. y se añade la huella en Restricciones de Android con el applicationId "com.example.meedu_googlemaps":
        ~~~
        com.example.google_maps	B7:4C:A6:EC:4D:F5:57:62:26:3B:70:B7:F1:67:6D:A5:3F:0A:35:61
        ~~~
      > Si se quiere subir la aplicacion se tiene que crear un certificado de tipo SHA1
      3. Añadir la restriccion para que solo se pueda utilizar la API en Maps SDK for android and iso
3. Agregar minSdkVersion in `android/app/build.gradle`:
      ~~~gradle
      android {
            defaultConfig {
                minSdkVersion 20
            }
        }
      ~~~
4. Specificar la API key en la  application manifest `android/app/src/main/AndroidManifest.xml`:
      ~~~xml
      <manifest ...
        <application ...
            <meta-data android:name="com.google.android.geo.API_KEY"
                    android:value="YOUR KEY HERE"/>
      ~~~


