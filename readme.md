# Stylus Library (Java)
## _Stylus Pressure Input for Java, corresponding **library** for **stylus-jni**_

This is my corresponding **_mod_** for [stylus-jni mod](https://github.com/sdneon/stylus-lib).

It adds attributes for keyboard modifiers, i.e. ALT, SHIFT, and CONTROL keys.

## Use With

Use with [Stylus JNI](https://github.com/sdneon/stylus-lib).

You don't need to use this mod if you don't need modifiers with stylus events. Is so, simply use the original [org.lecturestudio.stylus](https://github.com/lectureStudio/stylus/tree/main/stylus/src/main/java/org/lecturestudio/stylus) Java classes for the stylus listener interface and events.

To use this mod,
* Refer to [stylus-jni mod Readme](https://github.com/sdneon/stylus-jni#deficiency) to listen to modifier changes globally.
* In your StylusListener implementation, when creating a StylusEvent, mesh in the modifiers. E.g.:
```java
//in StylusListener implementation:
@Override
public void onCursorChange(StylusEvent event) {
	translateToComponent(component, event);

	if (componentContains(component, event)) {
	    event.setModifiers(alt, shift, ctrl); //mesh in current modifiers' states
		listener.onCursorChange(event);
	}
}
```

## Thanks

Thanks to [org.lecturestudio.stylus](https://github.com/lectureStudio/stylus) for the awesome Stylus JNI set.