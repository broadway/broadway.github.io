---
permalink: /serializing
title: Serializing
---

# Serializing

Serializing is a highly opinionated subject.
In Broadway we use a simple self-built serializer. Why? Because it allows us
to test (de)serialization on all our objects using the 
[SerializableEventTestCase](https://github.com/broadway/broadway/blob/master/src/Broadway/Serializer/Testing/SerializableEventTestCase.php). 
We've seen a lot of bugs resulting from incorrectly implemented serializers.

But feel free to use your own! Have a look at the [Broadway Serialization helper library](https://github.com/matthiasnoback/broadway-serialization)
by Matthias Noback or use anything you like! 

## Further reading

* [Experimenting with Broadway](https://matthiasnoback.nl/2015/07/experimenting-with-broadway/)
  by Matthias Noback
