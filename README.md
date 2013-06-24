webkitAudioContext monkeypatch
==============================

This monkeypatch library is intended to be included in projects that use 
webkitAudioContext (instead of AudioContext), and that may use the now-
deprecated bits of the Web Audio API (e.g. using AudioBufferSourceNode.noteOn()
instead of AudioBufferSourceNode.start().

This library should be harmless to include if the browser does not have
the unprefixed "AudioContext" implemented.  If unprefixed AudioContext is
supported, but the deprecated method names are already implemented, this
library will have created a few shim functions on create* methods, but 
will not damage or override anything else.  It also will not take effect
if webkitAudioContext is implemented.

Ideally, the use of this library will go to zero - it is only intended as
a way to quickly get script written to the old Web Audio methods to work
in browsers that only support the new, approved methods.

The patches this library handles:
---------------------------------

* AudioBufferSourceNode.noteOn() is aliased to start()
* AudioBufferSourceNode.noteGrainOn() is aliased to start()
* AudioBufferSourceNode.noteOff() is aliased to stop()
* AudioContext.createGainNode() is aliased to createGain()
* AudioContext.createDelayNode() is aliased to createDelay()
* AudioContext.createJavaScriptNode() is aliased to createScriptProcessor()
* OscillatorNode.noteOn() is aliased to start()
* OscillatorNode.noteOff() is aliased to stop()
* AudioParam.setTargetValueAtTime() is aliased to setTargetAtTime()
* OscillatorNode's old enum values are aliased to the Web IDL enum values.
* BiquadFilterNode's old enum values are aliased to the Web IDL enum values.
* PannerNode's old enum values are aliased to the Web IDL enum values.
* AudioContext.createWaveTable() is aliased to createPeriodicWave().
* OscillatorNode.setWaveTable() is aliased to setPeriodicWave().

You can copy the webkitAudioContextMonkeyPatch.js into your project if you
like, or include it as http://cwilso.github.com/webkitAudioContext-MonkeyPatch/webkitAudioContextMonkeyPatch.js.
