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

## Networked a-frame

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

## Entities

Each entity in the A-frame entity-component-system has a position, rotation, and scale.

## Algorand Wallets and NFTs

An Algorand wallet for an NFT collector may contain a number of NFTs such as images, videos, or 3D models (such as the GLTF/GLB format supported by A-frame).

## Algorand Stateful Contracts (Applications)

Algorand applications provide a way to store variable state on a blockchain, with access control based on wallet ownership. 

## IPFS and assets

Assets such as 3d models would be stored on IPFS. Alternatively, A-frame markup snippets could be stored, along with any pre-requisite script references, with 3D models refrenced from IPFS gateways.

## Idea

The idea is that a VR space is represented by an Algorand application, with the properties of objects inside of it such as rotation and position (or component-specific properties) represented as global state variables. The keys for these variables may be the asset ids, and the values may be strings that would be property declarations in a-frame.  Or, simply serialize the normal markup into a group of byte slices to be concatenated together.

The system could optionally limit the items in the VR space to ones that are owned by the application creator. And it would probably limit changes to asset properties (such as repositioning them) 

The networked aframe system takes care of synchronizing live state changes. An application transaction call by the owner of the VR space saves the current state.

## VR-Friendly Algorand Wallet

With an Algorand wallet system, perhaps built similarly to My Algo Connect, but with confirmation and data entry integrated into the VR environment, would facilitate the application calls and perhaps the integration of commerce.

## Commerce

A-frame applications may use components that extend their functionality and available markup properties. There could be properties that invoke the VR friendly integrated wallet for purchase of a 3d model, for example.


