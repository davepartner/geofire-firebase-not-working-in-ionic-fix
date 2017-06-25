# geofire-firebase-not-working-in-ionic-fix
This is a fix to get geofire working in your ionic or angular app. If you are having trouble getting geofire to work in your ionic or angular app,
this will solve it for you.


## Setup and installation
1. Install geofire with `npm install -g geofire`
2. Then create a file in `/src/app/` and name it `geofire.d.ts`. Then paste the below content into it. 


```
declare module 'geofire' {

    type EventType = 'ready' | 'key_entered' | 'key_exited' | 'key_moved';

    interface GeoQueryCriteria {
        center: number[];
        radius: number;
    }

    interface GeoQueryUpdateCriteria {
        center?: number[];
        radius?: number;
    }

    interface GeoCallbackRegistration {
        cancel();
    }

    interface GeoQuery {
        center(): number[];
        radius(): number;
        updateCriteria(criteria: GeoQueryUpdateCriteria);
        on(eventType: EventType, callback: (key:string, location: number[], distance: number) => void): GeoCallbackRegistration;
        cancel();
    }

    class GeoFire {
        constructor(ref: any);
        ref(): any;
        set(key: string, loc: number[]): Promise<void>;
        get(key: string): Promise<number[]>;
        remove(key: string): Promise<void>;
        query(criteria: GeoQueryCriteria): GeoQuery;
        static distance(location1: number[], location2: number[]);  
    }

    export = GeoFire;
    
    }

```


3. You can now use Gefire in any of your components by importing it like so:
` import Geofire from 'geofire';
//if you are working with ionic, dont forget to import Geolocation too
`
import { Geolocation } from '@ionic-native/geolocation';`


## Important links to contact me
I'd like to join your team
Follow me on my social media handles
* Subscribe to my channel on [Youtube](https://www.youtube.com/c/braintemorg?sub_confirmation=1)
* Follow on [Braintemple on Twitter](http://twitter.com/braintem) and [Dave Partner on Twitter](http://twitter.com/daveozoalor)
* Follow me on [Instagram](http://instagram.com/daveozoalor)
* Like on [Braintemple on Facebook](http://fb.com/braintem) , [Chat me up on Facebook](http://fb.com/daveozoalor)
* You can reach the me on `daveozoalor@gmail.com`, I'd like to join your team.

* Documentation for the Lumen framework can be found on the [Lumen website](http://lumen.laravel.com/docs).
* You going hard or you going home?


## License
This project is open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT).
