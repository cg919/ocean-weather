# @turf/interpolate

# interpolate

Takes a set of points and estimates their 'property' values on a grid using the [Inverse Distance Weighting (IDW) method](https://en.wikipedia.org/wiki/Inverse_distance_weighting).

**Parameters**

-   `points` **[FeatureCollection](http://geojson.org/geojson-spec.html#feature-collection-objects)&lt;[Point](http://geojson.org/geojson-spec.html#point)>** with known value
-   `cellSize` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** the distance across each grid point
-   `gridType` **\[[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)]** defines the output format based on a Grid Type (options: 'square' | 'point' | 'hex' | 'triangle') (optional, default `'square'`)
-   `property` **\[[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)]** the property name in `points` from which z-values will be pulled, zValue fallbacks to 3rd coordinate if no property exists. (optional, default `'elevation'`)
-   `units` **\[[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)]** used in calculating cellSize, can be degrees, radians, miles, or kilometers (optional, default `kilometers`)
-   `weight` **\[[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)]** exponent regulating the distance-decay weighting (optional, default `1`)

**Examples**

```javascript
var points = turf.random('points', 30, {
    bbox: [50, 30, 70, 50]
});
// add a random property to each point
turf.featureEach(points, function(point) {
    point.properties.solRad = Math.random() * 50;
});
var grid = turf.interpolate(points, 100, 'points', 'solRad', 'miles');

//addToMap
var addToMap = [grid];
```

Returns **[FeatureCollection](http://geojson.org/geojson-spec.html#feature-collection-objects)&lt;([Point](http://geojson.org/geojson-spec.html#point) \| [Polygon](http://geojson.org/geojson-spec.html#polygon))>** grid of points or polygons with interpolated 'property'

<!-- This file is automatically generated. Please don't edit it directly:
if you find an error, edit the source file (likely index.js), and re-run
./scripts/generate-readmes in the turf project. -->

---

This module is part of the [Turfjs project](http://turfjs.org/), an open source
module collection dedicated to geographic algorithms. It is maintained in the
[Turfjs/turf](https://github.com/Turfjs/turf) repository, where you can create
PRs and issues.

### Installation

Install this module individually:

```sh
$ npm install @turf/interpolate
```

Or install the Turf module that includes it as a function:

```sh
$ npm install @turf/turf
```