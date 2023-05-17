# Onsite Tracks: StepLogger for Android

Competitors of IPIN are required to code an Android application designed for smartphones (no tablet are allowed) that:
-computes the location of the target user during the measurement session
-reports the estimated position twice per second to the measurement application (aka the StepLogger app).

We provide 3 Android-based applications:
- StepLogger
- StepLogger in full-screen mode
- StepLoggerClient

StepLogger provides two operations:

a logging service designed to log the position computed by the applications of the competitors (Section 1) as well as the time you press the buttons shown by the app
a GUI to perform the measurements. We provide two versions of the StepLogger app, v1 designed to run on foreground, v2 designed to run also as overlay app (see Section 2)
StepLoggerClient provides one operation: a fake localization system generating fake positions and invoking the logging system of the StepLogger application
