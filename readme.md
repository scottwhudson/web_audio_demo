# JavaScript Web Audio API

Today, we're going to cover the basic concepts of the JavaScript Web Audio API, a fully functional synthesizer interface that ships in all modern browsers.

The Web Audio API can create & modulate tones, import external sound files & process them, access sound streams via client microphone, integrate with HTML5 canvas to create visualizations to function alongside audio, among many others.

By the end of this talk, you'll be able to create basic synth tones in the browser and modify audio parameters such as pitch and volume.

### Example 1

We're going to start out with perhaps the simplest setup for our Web Audio app, demonstrating the bare necessities for making the browser produce tones.

```js   
    var audioCtx = new (window.AudioContext ||
    window.webkitAudioContext)();

    var oscillator;

    oscillator = audioCtx.createOscillator();

    oscillator.connect(audioCtx.destination);

    oscillator.start();
```

### Example 2

### Example 3


## Examples In The Wild:

* [Violent Theramin](https://mdn.github.io/violent-theremin/)
* [AudioPhonic](https://stevekinney.github.io/audiophonic/)
