<script setup>
  import '../aframe/disable-in-vr';
  import '../aframe/hide-in-vr';
  import '../aframe/simple-navmesh-constraint';
  import '../aframe/blink-controls';
  import '../aframe/emit-when-near';
  import '../aframe/event-set';
  import '../aframe/clickable';
  import '../aframe/grabbable';
  import '../aframe/animation-mixer';
  import { ref } from 'vue';



</script>

<template>
  <a-entity
    id="camera-rig"

    movement-controls="camera: #head; speed:1;"
    disable-in-vr="component: movement-controls;" 
  > 

      <a-entity
        id="head"
        look-controls="pointerLockEnabled: true"
        simple-navmesh-constraint="navmesh: [data-role='nav-mesh']; height: 1.65; fall: 1"
        disable-in-vr="component: simple-navmesh-constraint;"
        camera
        position="0 1.65 0"
        
      >
          <a-entity
          id="reticle"
            geometry="primitive: circle; radius: 0.001;"
            material="shader: flat; color: white;"
            cursor
            raycaster="far: 5; objects: [clickable]; showLine: false;"
            position="0 0 -0.1"
            disable-in-vr="component: raycaster; disableInAR: false;"
            hide-in-vr="hideInAR: false"
          ></a-entity>
      </a-entity>

      <a-entity
        id="hand-left"
        hand-controls="hand: left"
        blink-controls="
          cameraRig: #camera-rig;
          teleportOrigin: #head;
          collisionEntities: [data-role='nav-mesh'];
          snapTurn: false;"
          
      ></a-entity>

      <a-entity
        id="hand-right"
        hand-controls="hand: right"
        laser-controls="hand: right"
        raycaster="far: 4; objects: [clickable]; showLine: true;"
      ></a-entity>

  </a-entity>
</template>