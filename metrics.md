---
layout: default
title: "Metrics"
description: "Observatory's metrics allow you to collect data on your program."
---

# Metrics

Observatory's metrics feature allows you to collect data on your program.
You can register a metric that you care about, like how many queries are
being performed per second, or how many bodies are in a scene.

You register your metrics programmatically using the
[Metrics](https://api.dartlang.org/stable/dart-developer/Metric-class.html)
class in the
[dart:developer](https://api.dartlang.org/stable/dart-developer/dart-developer-library.html)
library.  You can observe the metrics, as they collect,
using the `metrics` link on the VM page.

[Counter](https://api.dartlang.org/stable/dart-developer/Counter-class.html) and
[Gauge](https://api.dartlang.org/stable/dart-developer/Gauge-class.html)
are two metric classes provided for you. The following screenshot
shows an example of a user-defined Counter metric named "Bodies":

<img src="images/ObservatoryMetrics.png" alt="example showing Metrics using a Counter">

The "Bodies" counter is registered on the `numBodies` variable and is
set up with just a few lines of code:

``` dart
import 'dart:async';
import 'dart:developer';

Counter numBodies = new Counter("Bodies", "number of Bodies created");

main() {
  Metrics.register(numBodies);
  numBodies.value = 17;
  print(numBodies);
  new Timer.periodic(new Duration(seconds: 1), (t) {
    numBodies.value++;
  });
}
```

{% include observatory_fyi.html %}

{% include observatory_footer.html %}

