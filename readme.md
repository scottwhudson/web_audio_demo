# JavaScript Web Audio API

Today, we're going to cover the basic concepts of the JavaScript Web Audio API, a fully functional synthesizer interface that ships in all modern browsers.

The Web Audio API can create & modulate tones, import external sound files & process them, access sound streams via client microphone, integrate with HTML5 canvas to create visualizations to function alongside audio, among many others.

By the end of this talk, you'll be able to create basic synth tones in the browser and modify audio parameters such as pitch and volume.

### Example 1

We're going to start out with perhaps the simplest setup for our Web Audio app, demonstrating the bare necessities for making the browser produce tones.

```js   
    var audioCtx = new (window.AudioContext || window.webkitAudioContext)();
    var oscillator = audioCtx.createOscillator();

    oscillator.connect(audioCtx.destination);

    oscillator.start();
```

In the above sample, we've created all of the objects needed to generate a sound and deliver it to the browser.

First, we instantiate an `AudioContext` object (prefixing needed for Safari), which we will use to create the other necessary nodes and connect them to the destination.

Next, we create an oscillator node using the `AudioContext` object, which generates the tone. The oscillator has a few properties that can be customized, but for now, we'll stick with the default configuration.

Finally, we connect the oscillator to the `AudioContext` destination and call the `start` function, which starts the node.

### Example 2

In the second example, we're going to instantiate a `gainNode` that we can use to control the volume of the oscillator.  The `gainNode` will sit between the oscillator and the destination, modifying the node volume as it passes through.

```js   
    var audioCtx = new (window.AudioContext || window.webkitAudioContext)();
    var oscillator = audioCtx.createOscillator();
    var gainNode = audioCtx.createGain();

    oscillator.connect(gainNode);

    gainNode.connect(audioCtx.destination);

    gainNode.gain.value = someVar;

    oscillator.start();
```


#### Code walk-through
1. Create AudioContext
1. Create oscillator
1. Create gainNode
1. Connect the oscillator to the gainNode
1. Connect the gainNode to the destination
1. modify the gainNode value if necessary
1. start the oscillator



### Example 3

In our third example, we're going to modify the default frequency on the oscillator, thus modifying the pitch of the tone.

```js   
    var audioCtx = new (window.AudioContext || window.webkitAudioContext)();
    var oscillator = audioCtx.createOscillator();
    var gainNode = audioCtx.createGain();

    oscillator.connect(gainNode);

    gainNode.connect(audioCtx.destination);

    gainNode.gain.value = someVar;

    oscillator.frequency.value = someOtherVar; // pitch val here

    oscillator.start();
```

### Parting Notes on The Web Audio API
* Once `stop()` is called on an oscillator, it can't be restarted. A new instance must be created
* Many different nodes and filters can be applied to an oscillator, providing many different tone possibilities
* Comprehensive documentation on the Web Audio API can be found on [MDN](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API)

## Examples In The Wild:

* [Violent Theramin](https://mdn.github.io/violent-theremin/)
* [AudioPhonic](https://stevekinney.github.io/audiophonic/)
