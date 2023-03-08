<script setup>
  import { ref } from 'vue';
  import { randomHsl } from '../utils/color.js';

  import BoxColorChanging from './BoxColorChanging.vue';
  import TheCameraRig from './TheCameraRig.vue';
  import TheNavMesh from './TheNavMesh.vue';

  import '../aframe/life-like-automaton';
  import '../aframe/clickable';
  import '../aframe/grabbable';
  import '../aframe/animation-mixer';
  import '../aframe/emit-when-near';
  import '../aframe/teleport-camera-rig';

  defineProps({
    scale: Number,
    overlaySelector: String,
  });

  const colorBoxLeft = ref(randomHsl());
  const colorBoxRight = ref(randomHsl());
  const allAssetsLoaded = ref(false)
  const showText = ref(false)
  const showTextIntro = ref(false)
  const showTextIntroSuite = ref(false)
  const showSpeechIntro= ref(false)
  const showSpeechIntroSuite= ref(false)
  const showTextLink= ref(false)
  const showTextLinkSuite=ref(false)
  const showSpeechBubbleLink=ref(false)
  const textJack=ref(true)
  const speechJack=ref(true)
  const textDepart=ref(false)
  const compassGrabbed=ref(false)
  const naviGrabbed=ref(false)


  function manageClick(){
 showText.value = true;

  setTimeout(() => {
    showText.value = false;
  }, 5000);
  
  }

  function OpenIntro() {
  showSpeechIntro.value=true;
  showTextIntro.value=true;
}

  function ClickIntro(){
 if (showTextIntro) {
  showTextIntroSuite.value = true;
  showSpeechIntroSuite.value = true;
  showTextIntro.value = false;
  showSpeechIntro.value = false;
 }
  }

  function ClickIntroSuite(){
 if (showTextIntroSuite) {
  showTextIntroSuite.value = false;
  showSpeechIntroSuite.value = false;
  document.querySelector("#reticle").setAttribute("material","color", "white")
 }
  }


function ClickNavi(evt){
  const navi = evt.target;
   // navi.components['sound'].stopSound();
   navi.removeAttribute('sound');
   navi.setAttribute("grabbable", "target: #hand-right; auto: true");
  naviGrabbed.value=true;
  // navi.emit('say-hello');
}

function ClickCompass(evt){
  const compassMain = document.querySelector("#compassPirate")
   compassMain.setAttribute("grabbable", "target: #hand-right; auto: true");
  compassGrabbed.value=true;

}

function OpenTextLink() {
  showTextLink.value=true;
  showSpeechBubbleLink.value=true;
}

function CloseTextLink() {
  showTextLink.value=false;
  showTextLinkSuite.value=false;
  showSpeechBubbleLink.value=false;
}

function ClickSuite() {
  showTextLink.value=false;
    showTextLinkSuite.value=true;
}

function clickRemove(){
  const navi2 = document.querySelector("#naviVraie");
  console.log(navi2)
  if (naviGrabbed.value) {
    navi2.removeAttribute("grabbable");
  navi2.setAttribute("position", "-3 0 -44");
  }

 
}

function clickRemoveCompass(){
  const compass = document.querySelector("#compassPirate");
  if (compassGrabbed.value) {
    compass.removeAttribute("grabbable");
    compass.setAttribute("position", "148.7 -200 -67.5");
  }
}

function FermerTexteJack(){
  textJack.value=false;
  textDepart.value=true;
}

function stopKnight(){  
  const knighty = document.querySelector("#knighty");
  const boxKnighty = document.querySelector("boxknight");
  boxKnighty.components.sound.stopSound();
  knighty.components.sound.stopSound();
}


</script>

<template>



  <a-scene
    background="color: black;"
    renderer="colorManagement: true;"
    :webxr="`
      requiredFeatures: local-floor;
      referenceSpaceType: local-floor;
      optionalFeatures: dom-overlay;
      overlayElement: ${overlaySelector};
    `"
  >



    <a-assets @loaded="allAssetsLoaded = true">
      <!--
        Title: VR Gallery
        Model source: https://sketchfab.com/3d-models/vr-gallery-1ac32ed62fdf424498acc146fad31f7e
        Model author: https://sketchfab.com/mvrc.art (Maxim Mavrichev)
        Model license: CC BY 4.0 ( https://creativecommons.org/licenses/by/4.0/ )
      -->
      <a-asset-item  id="map1" src="assets/castle_village_scene.glb"></a-asset-item>
      <a-asset-item  id="solaire" src="assets/warrior_solaire.glb"></a-asset-item>
      <a-asset-item  id="link" src="assets/game_cube_-__the_wind_waker-_link.glb"></a-asset-item>
      <a-asset-item id="sun" response-type="arraybuffer" src="assets/Praise.mp3" preload="auto"></a-asset-item>
      <a-asset-item id="Hey" response-type="arraybuffer" src="assets/Hey.mp3" preload="auto"></a-asset-item>
      <a-asset-item id="kass" response-type="arraybuffer" src="assets/Kass_Theme.mp3" preload="auto"></a-asset-item>
      <a-asset-item id="linkScream" response-type="arraybuffer" src="assets/LinkScream.mp3" preload="auto"></a-asset-item>
      <a-asset-item id="OpenChest" response-type="arraybuffer" src="assets/OpenChest.mp3" preload="auto"></a-asset-item>
      <a-asset-item id="Glass" response-type="arraybuffer" src="assets/Glass.mp3" preload="auto"></a-asset-item>
      <a-asset-item id="giberish" response-type="arraybuffer" src="assets/giberish.mp3" preload="auto"></a-asset-item>
      <a-asset-item  id="speech" src="assets/speech_bubble.glb"></a-asset-item>
      <a-asset-item  id="speech2" src="assets/speech_bubble.glb"></a-asset-item>
      <a-asset-item  id="speech3" src="assets/speech_bubble.glb"></a-asset-item>
      <a-asset-item  id="speech4" src="assets/speech_bubble.glb"></a-asset-item>
      <a-asset-item  id="speech5" src="assets/speech_bubble.glb"></a-asset-item>
      <a-asset-item  id="kassPerso" src="assets/kass.glb"></a-asset-item>
      <a-asset-item  id="door1" src="assets/door_wood.glb"></a-asset-item>
      <a-asset-item  id="door2" src="assets/door_wood.glb"></a-asset-item>
      <a-asset-item  id="map2" src="assets/pirate_map.glb"></a-asset-item>
    <a-asset-item  id="Jack" src="assets/Jack.glb"></a-asset-item>
    <a-asset-item  id="sign" src="assets/sign.glb"></a-asset-item>
    <a-asset-item  id="compass" src="assets/pirate_compass.glb"></a-asset-item>
    <a-asset-item  id="barrel" src="assets/pirate_props.glb"></a-asset-item>
    <a-asset-item  id="navi" src="assets/navi.glb"></a-asset-item>
    <a-asset-item  id="map_zelda" src="assets/legend_of_zelda.glb"></a-asset-item>
    <a-asset-item  id="jar" src="assets/jar.glb"></a-asset-item>
    <a-asset-item  id="chest" src="assets/chest.glb"></a-asset-item>
    <a-asset-item  id="arrow" src="assets/arrow.glb"></a-asset-item>
    <a-asset-item  id="knight" src="assets/knight.glb"></a-asset-item>
    <img id="asky" src="/assets/asky.jpg">
    </a-assets>

    <a-sky src="#asky" position="0 0 0"></a-sky>

    <a-entity
      v-if="allAssetsLoaded"
      gltf-model="#map1"
      rotation="0 0 0"
      position="3 0 -53"
      scale="80 80.80 80"
    >  
    </a-entity>

 
    <a-entity
      v-if="allAssetsLoaded"
      gltf-model="#solaire"
      rotation="0 -45 0"
      position="1.7 0 -5.3"
      scale="1 1 1"
      clickable
      @click="manageClick()"
      sound="src: #sun; on:click; volume: 1; refDistance: 1; rolloffFactor: 1 "    
    >  
    </a-entity>


    <a-entity
    v-if="showText"
      gltf-model="#speech"
      rotation="270.000 -45.000 90.000"
      position="-4.397 3.970 -5.550"
      scale="0.280 0.100 0.070"   
    >  
    </a-entity>

    <a-text
    v-if="showText"
        rotation="0 45 0"
        position=" -3.399 2.788 -6.543"
        value="Praise the sun !"
        color="black" 
    >
    </a-text>

    <a-entity 
      v-if="allAssetsLoaded"
      gltf-model="#arrow"
      rotation="270 0 0"
      position=" -0.081 4.578 -11.273"
      scale="0.2 0.2 0.2"
     
      
    >  
    </a-entity>


    <a-entity 
      v-if="allAssetsLoaded"
      gltf-model="#link"
      rotation="0 45 0"
      position="-4 0.1 -43"
      scale="0.018 0.018 0.018"
      clickable
      @click="ClickSuite()"
      
    >  
    </a-entity>

    <a-entity 
    id="knighty"
      v-if="allAssetsLoaded"
      gltf-model="#knight"
      rotation="0 0 0"
      position="-2.849 0.010 -72.525"
      scale="2 2 2"
      clickable
      sound="src: #giberish; on: click; volume: 1; refDistance: 1; rolloffFactor: 1;"  
    >  
    </a-entity>

    <a-box id="boxknight" color="red" depth="15" height="3" width="10" position="-2.349 1.6 -63.890" visible="false"
    emit-when-near=" event: Speak; eventFar: stopSpeak"
    sound="src: #giberish;  on:Speak;  volume: 1; refDistance: 1; rolloffFactor: 1;"  
    @stopSpeak="stopKnight()"


    ></a-box>

    <a-text
    v-if="showTextLink"
        rotation="0 45 0"
        position=" -4.491 2.860 -42.203"
        scale="0.6 0.8 0.6"
        value="Hey ! peux tu m'aider ?
        Il faut que tu trouves Navi, une fee bleue enervante et que tu l'enferme dans un bocal"
        color="black" 
        clickable
            
    >
    </a-text>

    <a-text
    v-if="showTextLinkSuite"
        rotation="0 45 0"
        position=" -4.591 2.860 -42"
        scale="0.6 0.8 0.6"
        value="Elle est dans ma maison et le bocal est juste la !
        hate toi s'il te plait elle me tape sur les nerfs"
        color="black" 
        clickable
            @click="ClickSuite()"
    >
    </a-text>

    <a-box id="boxLink" color="red" depth="15" height="3" width="15" position="-3.010 1.6 -38.769" visible="false"
    emit-when-near=" event: showTextLink; eventFar: hideTextLink" 
    sound="src: #linkScream;  on:showTextLink;  volume: 1; refDistance: 1; rolloffFactor: 1;"  
    @showTextLink=" OpenTextLink()"
    @hideTextLink=" CloseTextLink()"

    ></a-box>

    <a-entity
    v-if="showSpeechBubbleLink"
            gltf-model="#speech2"
            rotation="270.000 -45 90.000"
            position=" -6.366 4.9 -40.333 "
            scale="0.500 0.020 0.120"   
            
            clickable
            @click="ClickSuite()"
          >  
    </a-entity>

    <a-entity 
      v-if="allAssetsLoaded"
      gltf-model="#jar"
      rotation="0 45 0"
      position="-3 0 -44.000"
      scale="1 1 1"
      clickable
      @click="clickRemove()"
      sound="src: #Glass; on:click; volume: 1; refDistance: 1; rolloffFactor: 1 "
      
    >  
    </a-entity>


<!--     <a-entity
        id="hand-left"
        hand-controls="hand: left"        
      ></a-entity>

    <a-entity
        id="hand-right"
        hand-controls="hand: right"        
    >
    </a-entity> -->


    <a-entity
    v-if="showSpeechIntro"
            gltf-model="#speech2"
            rotation="270.000 90.000 90.000"
            position="3.957 5.700 -18.727"
            scale="0.500 0.100 0.200"   
            
            clickable
            @click="ClickIntro()"
          >  
    </a-entity>

    <a-text
    v-if="showTextIntro"
        rotation="0 0 0"
        position=" -1.450 2.25 -18.672"
        scale="0.9 1 0.9"
        value="Bienvenue dans le chateau du la VR !
         (cliquer pour la suite)"
        color="black" 
        clickable
            @click="ClickIntro()"
    >
    </a-text>

    <a-entity
    v-if="showSpeechIntroSuite"
            gltf-model="#speech3"
            rotation="270.000 90.000 90.000"
            position="3.957 5.700 -18.727"
            scale="0.500 0.100 0.200"   
            clickable
            @click="ClickIntroSuite()"
          >  
    </a-entity>


    <a-text
    v-if="showTextIntroSuite"
        rotation="0 0 0"
        position=" -1.250 2.28 -18.672"
        scale="0.9 1 0.9"
        value="Baladez vous et explorer
        les differentes maisons
            
         (cliquer pour fermer)"
        color="black" 
        clickable
            @click="ClickIntroSuite()"
    >
    </a-text>

    <a-box color="red" depth="15" height="3" width="15" position="0 1.6 -10.827" visible="false"
    emit-when-near=" event: showTextValue;"
    sound="src: #kass; loop:true; on: showTextValue;  volume: 0.1; refDistance: 5; rolloffFactor: 1 "  
    @showTextValue=" OpenIntro()"
    ></a-box>


    <a-entity
    v-if="allAssetsLoaded"
      gltf-model="#barrel"
      rotation="00 180 00"
      position="9.7 0.3 -38"
      scale="1 1 1"    
      
    >  
    </a-entity>

    <a-entity
    v-if="allAssetsLoaded"
    id="travelToPirates"
      gltf-model="#door1"
      rotation="00 -77 00"
      position="9.7 0 -39.85"
      scale="1 0.8 1"    
      clickable
      teleport-camera-rig="x: 4; y: -199.9; z: -53;"
    >  
    </a-entity>

    <a-text
    v-if="allAssetsLoaded"
        rotation="0 -80 0"
        position="9.3 2.95 -40.5"
        scale=" 0.9 0.9 0.9"
        value="Monde des pirates"
        color="black" 
    >
    </a-text>

    <a-entity
    v-if="allAssetsLoaded"
      gltf-model="#speech4"
      rotation="270.000 -170.000 90.000"
      position="9 4.5 -42.5"
      scale="0.40 0.200 0.090"   
    >  
    </a-entity>


    <a-entity
    v-if="allAssetsLoaded"
    id="travelToLinkHouse"
      gltf-model="#door2"
      rotation="00 -30 00"
      position="2.72 0 -57.5"
      scale="1 0.8 1"    
      clickable
      teleport-camera-rig="x: 2; y:-95.4; z: -38;"
    >   
    </a-entity>

    <a-text
    v-if="allAssetsLoaded"
        rotation="0 -30 0"
        position="1.7 2.95 -57.5"
        scale=" 0.9 0.9 0.9"
        value="Maison de Link"
        color="black" 
    >
    </a-text>

    <a-entity
    v-if="allAssetsLoaded"
      gltf-model="#speech4"
      rotation="270.000 -120 90.000"
      position="0 4.5 -58.5"
      scale="0.40 0.200 0.090"   
    >  
    </a-entity>

    <!-- map pirate -->


    <a-entity
      v-if="allAssetsLoaded"
      gltf-model="#map2"
      rotation="0 102 0"
      position="3 -200 -53"
      scale="0.002 0.002 0.002"
    >  
    </a-entity>

    <a-entity
      v-if="allAssetsLoaded"
      gltf-model="#Jack"
      rotation="0 190 0"
      position="147.042 -200 -67.050"
      scale="0.18 0.18 0.18"
      clickable
      teleport-camera-rig="x:-0.068; y:0; z:-32.889;"
    >  
    </a-entity>

    <a-text
    v-if="textJack"
        rotation="0 -110 0"
        position="148 -198.3 -70.1"
        scale=" 0.4 0.4 0.4"
        value="toux doux moussaillon, pourrais tu deposer ma 
        boussole dans ce beau coffre a mes pieds ?"
        color="black" 
        @click="FermerTexteJack()"
    >
    </a-text>

    <a-text
    v-if="textDepart"
        rotation="0 -110 0"
        position="148.200 -198.3 -69.531"
        scale=" 0.4 0.4 0.4"
        value="Des que tu m'auras rendu ma boussole,
        tu pourras partir en me cliquant dessus"
        color="black" 
        teleport-camera-rig="x:-0.068; y:0; z:-32.889;"
    >
    </a-text>

    <a-entity
    v-if="allAssetsLoaded"
      gltf-model="#speech5"
      rotation="268.000 160 90.000"
      position="149 -196.65 -71.7"
      scale="0.40 0.200 0.090"   
      clickable
      @click="FermerTexteJack()"
    >  
    </a-entity>


    <a-box id="boxJack" color="red" depth="5" height="3" width="5" position="146.042 -200.036 -72.050" visible="false"
    emit-when-near=" event: showTextJack;" 
    @showTextJack=" OpenTextJack()"
    ></a-box>


    <a-entity
      v-if="allAssetsLoaded"
      gltf-model="#sign"
      rotation="0 -45 0"
      position="18 -199 -54"
      scale="1 1 1"
      clickable
      teleport-camera-rig="x:147.042; y:-200,036; z:-70.050;"
    >  
    </a-entity>

    <a-text
    v-if="allAssetsLoaded"
        rotation="0 -130 0"
        position="19 -198.1 -55.2"
        scale="0.4 0.4 0.4"
        value="Cliquez pour aller vers jack 
        Sparrow"
        color="white" 
        clickable
      teleport-camera-rig="x:147.042; y:-200,036; z:-70.050;"
    >
    </a-text>

    <a-text
    v-if="allAssetsLoaded"
        rotation="0 -130 0"
        position="19 -198.4 -55.2"
        scale="0.4 0.4 0.4"
        value="Amenez lui sa boussole"
        color="white" 
    >
    </a-text>

    <a-entity 
    id="compassPirate"
      v-if="allAssetsLoaded"
      gltf-model="#compass"
      rotation="0 -125 0"
      position="18 -199.7 -55"
      scale="0.2 0.2 0.2"
      clickable
      @click="ClickCompass()"
      grabbable
      
    >  
    </a-entity>

    <a-entity 
    
      v-if="allAssetsLoaded"
      gltf-model="#chest"
      rotation="0 220 0"
      position="148.7 -199.8 -67.5"
      scale="0.01 0.01 0.01"
      clickable
      @click="clickRemoveCompass()"
      sound="src: #OpenChest; on:click; volume: 1; refDistance: 1; rolloffFactor: 1 "
      
    >  
    </a-entity>


      <!-- map zelda -->

    <a-entity 
    v-if="allAssetsLoaded"
      id="naviVraie"
      gltf-model="#navi"
      rotation="0 0 0"
      position="1 -94 -41"
      scale="0.1 0.1 0.1"
      
      emit-when-near__sound="target: #camera-rig; distance: 10; event: navi-say;"
      clickable
      @click="ClickNavi($event)"
      sound="src: #Hey; loop:true; on: navi-say;  volume: 0.5; refDistance: 1; rolloffFactor: 1 "    
      grabbable
    >  
    </a-entity>

    <a-entity 
      v-if="allAssetsLoaded"
      gltf-model="#map_zelda"
      rotation="0 0 0"
      position="0 -100 -50"
      scale="2 2 2"
      clickable
    >  
    </a-entity>

    <a-text
    v-if="allAssetsLoaded"
        rotation="0 150 0"
        position="-3.4 -93.5 -35.7"
        scale=" 1 1 1"
        value="Retour"
        color="black" 
        clickable
        teleport-camera-rig="x:-0.068; y:0; z:-32.889;"
    >
    </a-text>

    <a-entity
    v-if="allAssetsLoaded"
      gltf-model="#speech4"
      rotation="270.000 -120 90.000"
      position="-5 -92 -36.5"
      scale="0.20 0.200 0.090"  
      clickable
        teleport-camera-rig="x:-0.068; y:0; z:-32.889;"
    >  
    </a-entity>

    

    <TheNavMesh />

    <TheCameraRig />

  </a-scene>
</template>      
