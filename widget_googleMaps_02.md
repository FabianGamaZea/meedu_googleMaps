1. Se sefine la nueva estructura de trabajo:
     ~~~bash
     lib
    ├── app
    │  ├── data
    │  ├── domain
    │  └── ui
    │     ├── home
    │     │  └── home_pages.dart
    │     └── pages
    └── main.dart
     ~~~
2. se modifica `meedu_googlemaps/lib/main.dart` y se hace referencia al nuevo home:
     ~~~Dart
                primarySwatch: Colors.blue,
            ),
            home:  HomePage(),
            );
        }
     ~~~
3. se modifica `meedu_googlemaps/lib/app/ui/home/home_pages.dart` y se agrega la pantalla:
     ~~~dart
    import 'package:flutter/material.dart';
    import 'package:google_maps_flutter/google_maps_flutter.dart';

    class HomePage extends StatefulWidget {
    HomePage({Key? key}) : super(key: key);

    @override
    _HomePageState createState() => _HomePageState();
    }

    class _HomePageState extends State<HomePage> {
    final _initialCameraPosition = const CameraPosition(
        target: LatLng(19.4047811,-99.0005758),
        zoom : 15,
        );
    
    @override
    Widget build(BuildContext context) {
        return  Scaffold(
        appBar: AppBar(),
        body: GoogleMap(initialCameraPosition: _initialCameraPosition),
        );
    }
    }
     ~~~