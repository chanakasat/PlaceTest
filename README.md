# PlaceTest

Targets releasing a .jar library for outside world to help carrying out coordinate transformation work in Sri Lankan domain.
Algorithm focuses on **SLD99** datum and utilizes 7 parameter Helmert transformation and transverse Mercator projection to carry out forward and backward transformations. 

The project is created with eclipse.
Look inside /PlaceTest/src/test/Test.java for an example usage.

**If you are interested in using the library, please ask for permision from the author.
You should also attribute the author in your work.**

Name: Chanaka Alahakoon

email: chanakasat@gmail.com

Note: /lib/place_pg.jar which holds the core transformation logic, is obfuscated reviling only the important parts.

Example usage:

```java
package test;

import place.coordinatetransform.Calculate;
import place.coordinatetransform.Place;

public class Test {
	
	public static void main(String[] args) {
		
		// From wgs84 to projected example
		double lat = 7.1324253;
		double lon = 80.4231543;
		double h = 100;
				
		Place place = Calculate.xyhFromLatLonH(lat, lon, h);
				
		double x = place.getGridX();
		double y = place.getGridY();
		double nh = place.getHeight();
				
		System.out.println("x: " + x);
		System.out.println("y: " + y);
		System.out.println("h: " + nh);
				
		// From projected to wgs84 example	
		Place place2 = Calculate.latLonHFromxyh(x, y, nh);
				
		lat = place2.getLatitude();
		lon = place2.getLongitude();
		h = place2.getHeight();
				
		System.out.println("lat: " + lat);
		System.out.println("lon: " + lon);
		System.out.println("h: " + h);	
		
		// Output
		/*
		x: 461276.82835468283
		y: 514569.83370149805
		h: 199.0952384294942
		lat: 7.132425281741064
		lon: 80.42315419149371
		h: 100.00387735292315
		*/

	}
}
```

