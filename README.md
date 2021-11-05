# Algoverse-concept
Concept for an open metaverse using WebXR running on the Algorand blockchain

## A-frame VR

There is a web technology previously referred to as WebVR, now (I think) called WebXR, that allows browsers in VR headsets to enter into VR mode. [A-frame VR](https://aframe.io/) is a library that allows you to use HTML-like markup to declaratively create VR environments in the browser (maybe slightly similar concept to VRML).  

This is the github repo: https://github.com/aframevr/aframe/

```html
<html>
  <head>
    <script src="https://aframe.io/releases/1.2.0/aframe.min.js"></script>
  </head>
  <body>
    <a-scene>
      <a-box position="-1 0.5 -3" rotation="0 45 0" color="#4CC3D9"></a-box>
      <a-sphere position="0 1.25 -5" radius="1.25" color="#EF2D5E"></a-sphere>
      <a-cylinder position="1 0.75 -3" radius="0.5" height="1.5" color="#FFC65D"></a-cylinder>
      <a-plane position="0 0 -4" rotation="-90 0 0" width="4" height="4" color="#7BC8A4"></a-plane>
      <a-sky color="#ECECEC"></a-sky>
    </a-scene>
  </body>
</html>

```

There is additionally something called networked-aframe which allows relatively trivial implementation of multiplayer VR:
https://github.com/networked-aframe/networked-aframe

```html
<html>
  <head>
    <title>My Networked-Aframe Scene</title>
    <script src="https://aframe.io/releases/1.2.0/aframe.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/socket.io/2.3.0/socket.io.slim.js"></script>
    <script src="/easyrtc/easyrtc.js"></script>
    <script src="https://unpkg.com/networked-aframe@^0.8.0/dist/networked-aframe.min.js"></script>
  </head>
  <body>
    <a-scene networked-scene>
      <a-assets>
        <template id="avatar-template">
           <a-sphere></a-sphere>
        </template>
      </a-assets>
      <a-entity id="player" networked="template:#avatar-template;attachTemplateToLocal:false;" camera wasd-controls look-controls>
      </a-entity>
    </a-scene>
  </body>
</html>
```

