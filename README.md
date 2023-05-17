# Onsite Tracks: StepLogger for Android

Competitors of IPIN are required to code an Android application designed for smartphones (no tablet are allowed) that:
-computes the location of the target user during the measurement session
-reports the estimated position twice per second to the measurement application (aka the StepLogger app).

We release 3 Android-based applications:
- [StepLogger](https://github.com/wnlab-isti/steplogger)
- [StepLogger in full-screen mode](https://github.com/wnlab-isti/steplogger_fullscreen)
- [StepLoggerClient](https://github.com/wnlab-isti/steplogger_client)

StepLogger implements 2 operations:
- a logging service designed to log the position computed by the applications of the competitors, and the timestamp when you press the buttons shown by the app
- a GUI to perform the measurements. We provide 2 versions of the StepLogger:
	- designed to run on foreground
	- designed to run as overlay app

StepLoggerClient implements 1 operation: a test localization system generating fake positions and invoking the logging system of the StepLogger application.

## StepLogger Logging Interface

StepLogger implements a simple service for the applications of the competitors. The service is implemented with the Java-method:

	void logPosition(in long timestamp, in double x,in double y, in double z);

which is implemented by the StepLogger. This method must be invoked through the [AIDL](https://developer.android.com/guide/components/aidl) interface. In particular, competitors are required add the StepLogger AIDL file to their Android project and invoke the `logPosition` method twice per second.

Every time the competing app calls `logPosition`, the StepLogger app logs the following information:

- Time stamp: time in milliseconds from the Unix epoch, as returned from the `currentTimeMillis()` method provided by the Java System class
- Coordinates x, y, z : x and y are longitude and latitude, respectively, with WGS84 reference system, while z is the floor, that is an integer number, with a 0 indicating the ground floor.

These information are stored in the file `positions.log`, as detailed below under “StepLogger Logging mechanism”.