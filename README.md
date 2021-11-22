<!--

@license Apache-2.0

Copyright (c) 2018 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->

# Single-Hop Sensor Network

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Labeled wireless sensor network data set collected from a simple single-hop wireless sensor network deployment using TelosB motes.

<section class="installation">

## Installation

```bash
npm install @stdlib/datasets-suthaharan-single-hop-sensor-network
```

</section>

<section class="usage">

## Usage

```javascript
var dataset = require( '@stdlib/datasets-suthaharan-single-hop-sensor-network' );
```

#### dataset()

Returns a dataset consisting of labeled wireless sensor network data set collected from a simple single-hop wireless sensor network deployment using TelosB motes.

```javascript
var data = dataset();
/* returns
    [
        {
            'reading': 1,
            'mote_id': 1,
            'indoor': 1,
            'humidity': 45.93,
            'temperature': 27.97,
            'label': 0
        },
        ...
    ]
*/
```

</section>

<!-- /.usage -->

<section class="notes">

## Notes

-   Humidity and temperature measurements were collected at `5` second intervals over a six hour period on May 9, 2010.
-   Temperature is in degrees Celsius.
-   Humidity is temperature corrected relative humidity, ranging from 0-100%.
-   The label `0` denotes normal data, and the label `1` denotes an introduced event.
-   If a mote was an indoor sensor, the corresponding indicator is `1`. If a mote was an outdoor sensor, the indoor indicator is `0`.

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```javascript
var incrgrubbs = require( '@stdlib/stats-incr-grubbs' );
var data = require( '@stdlib/datasets-suthaharan-single-hop-sensor-network' );

var acc;
var d;
var i;
var j;
var k;

// Get the sensor data:
d = data();

// For each mote, test for an outlier temperature measurement...
i = 0;
for ( j = 0; j < 4; j++ ) {
    k = j + 1;

    // Create a new accumulator for performing Grubbs' test:
    acc = incrgrubbs();

    // Update the accumulator with temperature data...
    while ( i < d.length && d[ i ].mote_id === k ) {
        acc( d[ i ].temperature );
        i += 1;
    }
    // Print test results:
    console.log( '' );
    console.log( 'Mote: %d', k );
    console.log( '' );
    console.log( acc().print() );
}
```

</section>

<!-- /.examples -->

* * *

<section class="cli">

## CLI

<section class="installation">

## Installation

To use the module as a general utility, install the module globally

```bash
npm install -g @stdlib/datasets-suthaharan-single-hop-sensor-network
```

</section>

<section class="usage">

### Usage

```text
Usage: suthaharan-single-hop-sensor-network [options]

Options:

  -h,    --help                Print this message.
  -V,    --version             Print the package version.
         --format fmt          Output format: 'csv' or 'ndjson'.
```

</section>

<!-- /.usage -->

<section class="examples">

### Examples

```bash
$ suthaharan-single-hop-sensor-network
```

</section>

<!-- /.examples -->

</section>

<!-- /.cli -->

* * *

<section class="references">

## References

-   Suthaharan, Shan, Mohammed Alzahrani, Sutharshan Rajasegarar, Christopher Leckie, and Marimuthu Palaniswami. 2010. "Labelled data collection for anomaly detection in wireless sensor networks." In _Proceedings of the Sixth International Conference on Intelligent Sensors, Sensor Networks and Information Processing (ISSNIP 2010)_. Brisbane, Australia: IEEE.

</section>

<!-- /.references -->

<!-- <license> -->

## License

The data files (databases) are licensed under an [Open Data Commons Attribution 1.0 License][odc-by-1.0] and their contents are licensed under a [Creative Commons Attribution 4.0 International Public License][cc-by-4.0]. The original dataset is attributed to Shan Suthaharan, Mohammed Alzahrani, Sutharshan Rajasegarar, Christopher Leckie, and Marimuthu Palaniswami and can be found [here][suthaharan-single-hop-sensor-network-data]. The software is licensed under [Apache License, Version 2.0][apache-license].

<!-- </license> -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

* * *

## See Also

-   <span class="package-name">[`@stdlib/datasets/suthaharan-multi-hop-sensor-network`][@stdlib/datasets/suthaharan-multi-hop-sensor-network]</span><span class="delimiter">: </span><span class="description">labeled wireless sensor network data set collected from a multi-hop wireless sensor network deployment using TelosB motes.</span>

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## Copyright

Copyright &copy; 2016-2021. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/datasets-suthaharan-single-hop-sensor-network.svg
[npm-url]: https://npmjs.org/package/@stdlib/datasets-suthaharan-single-hop-sensor-network

[test-image]: https://github.com/stdlib-js/datasets-suthaharan-single-hop-sensor-network/actions/workflows/test.yml/badge.svg
[test-url]: https://github.com/stdlib-js/datasets-suthaharan-single-hop-sensor-network/actions/workflows/test.yml

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/datasets-suthaharan-single-hop-sensor-network/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/datasets-suthaharan-single-hop-sensor-network?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/datasets-suthaharan-single-hop-sensor-network.svg
[dependencies-url]: https://david-dm.org/stdlib-js/datasets-suthaharan-single-hop-sensor-network/main

-->

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://gitter.im/stdlib-js/stdlib/

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[suthaharan-single-hop-sensor-network-data]: http://www.uncg.edu/cmp/downloads/lwsndr.html

[odc-by-1.0]: http://opendatacommons.org/licenses/by/1.0/

[cc-by-4.0]: http://creativecommons.org/licenses/by/4.0/

[apache-license]: https://www.apache.org/licenses/LICENSE-2.0

<!-- <related-links> -->

[@stdlib/datasets/suthaharan-multi-hop-sensor-network]: https://github.com/stdlib-js/datasets-suthaharan-multi-hop-sensor-network

<!-- </related-links> -->

</section>

<!-- /.links -->
