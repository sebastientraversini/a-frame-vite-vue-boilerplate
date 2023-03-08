<script setup>
  import { ref } from 'vue';

  defineProps({
    loaded: Boolean,
  });

  const showOnboarding = ref(true);

  function enterScene() {
    showOnboarding.value = false;
    if (AFRAME.utils.device.checkHeadsetConnected() && !AFRAME.utils.device.isMobile()) {
      document.querySelector('a-scene').enterVR();
    }
  }
</script>

<template>
  <div id="onboarding" v-if="showOnboarding">
    <div>
      <h1>A-Frame + Vite + Vue Boilerplate</h1>
      <p v-if="!loaded">loading...</p>
      <button v-if="loaded" @click="enterScene()">Enter scene</button>
      <div class="licences">
        <dl>
          <dt>
            <i>Included</i>
          </dt>
          <dt>
            <a href="https://github.com/c-frame/aframe-extras" target="_blank">aframe-extras controls and animation-mixer</a>
          </dt><dd>
            <a href="https://github.com/c-frame/aframe-extras/blob/master/LICENSE" target="_blank">MIT License</a>
          </dd>

          <dt>
            <a href="https://github.com/jure/aframe-blink-controls/" target="_blank">aframe-blink-controls</a>
          </dt><dd>
            <a href="https://github.com/jure/aframe-blink-controls/blob/main/LICENSE" target="_blank">MIT License</a>
          </dd>

          <dt>
            <a href=" https://github.com/AdaRoseCannon/aframe-xr-boilerplate" target="_blank">simple-navmesh-constraint</a>
          </dt><dd>
            By Ada Rose Cannon under MIT License
          </dd>

          <dt>
            <a href="https://sketchfab.com/3d-models/vr-gallery-1ac32ed62fdf424498acc146fad31f7e" target="_blank">VR Gallery</a>
          </dt>
          <dd>
            by <a href="https://sketchfab.com/mvrc.art" target="_blank">Maxim Mavrichev</a>
            under <a href="https://creativecommons.org/licenses/by/4.0/" target="_blank">CC BY 4.0</a>
          </dd>
          <dt>
            <a href="https://sketchfab.com/3d-models/mage-knight-e6b2bf93414b41299543886035513e45" target="_blank">Mage Knight</a>
          </dt>
          <dd>
            by <a href="https://sketchfab.com/Nathan." target="_blank">Nathan</a>
            under <a href="https://creativecommons.org/licenses/by/4.0/" target="_blank">CC BY 4.0</a>
          </dd>

          <dt>
            <a href="https://sketchfab.com/3d-models/warrior-solaire-e8a94fa8ba0b4d80b9c03f05ff45273d" target="_blank">Warrior Solaire</a>
          </dt>
          <dd>
            by <a href="https://sketchfab.com/Keita-sama" target="_blank">Keita-sama</a>
            under <a href="https://creativecommons.org/licenses/by/4.0/" target="_blank">CC BY 4.0</a>
          </dd>

          <dt>
            <a href="https://sketchfab.com/3d-models/castle-village-scene-675b3afce21a4acaa1140645a5206db3" target="_blank">Castle village scene</a>
          </dt>
          <dd>
            by <a href="https://sketchfab.com/blackspire" target="_blank">BlackSpire</a>
            under <a href="https://creativecommons.org/licenses/by/4.0/" target="_blank">CC BY 4.0</a>
          </dd>

          <dt>
            <a href="https://sketchfab.com/3d-models/mage-knight-e6b2bf93414b41299543886035513e45" target="_blank">Mage Knight</a>
          </dt>
          <dd>
            by <a href="https://sketchfab.com/Nathan." target="_blank">Nathan</a>
            under <a href="https://creativecommons.org/licenses/by/4.0/" target="_blank">CC BY 4.0</a>
          </dd>

          <dt>
            <a href="https://sketchfab.com/3d-models/game-cube-the-wind-waker-link-bceac86d674841389b552f3ea5509993" target="_blank">Game Cube - The Wind Waker- Link</a>
          </dt>
          <dd>
            by <a href="https://sketchfab.com/skelezone2_0" target="_blank">skelebone2.0</a>
            under <a href="https://creativecommons.org/licenses/by/4.0/" target="_blank">CC BY 4.0</a>
          </dd>

          <dt>
            <a href="https://sketchfab.com/3d-models/game-pirate-adventure-map-696dfa212fda4240817615bdccb373d0" target="_blank">Game pirate adventure map</a>
          </dt>
          <dd>
            by <a href="https://sketchfab.com/zsm123" target="_blank">noyou</a>
            under <a href="https://creativecommons.org/licenses/by/4.0/" target="_blank">CC BY 4.0</a>
          </dd>

          <dt>
            <a href="https://sketchfab.com/3d-models/jack-sparrow-pirates-of-caribbean-53b7afe2e33d413db3f94fcba4da9943" target="_blank">Jack Sparrow Pirate of Carribean</a>
          </dt>
          <dd>
            by <a href="https://sketchfab.com/Elite3DModelling" target="_blank">Elite 3D</a>
            under <a href="https://creativecommons.org/licenses/by/4.0/" target="_blank">CC BY 4.0</a>
          </dd>

          <dt>
            <a href="https://sketchfab.com/3d-models/speech-bubble-01-b286a2bb0f7341b294124f71cca36bd7" target="_blank">Speech Bubble 01</a>
          </dt>
          <dd>
            by <a href="https://sketchfab.com/Khairulddin.Joha" target="_blank">Khairulddin.Joha</a>
            under <a href="https://creativecommons.org/licenses/by/4.0/" target="_blank">CC BY 4.0</a>
          </dd>

          <dt>
            <a href="https://sketchfab.com/3d-models/door-wood-afed9756ba974d1395a336124ff326fd" target="_blank">Door (wood)</a>
          </dt>
          <dd>
            by <a href="https://sketchfab.com/diggendigga" target="_blank">DiggenDigga</a>
            under <a href="https://creativecommons.org/licenses/by/4.0/" target="_blank">CC BY 4.0</a>
          </dd>

          <dt>
            <a href="https://sketchfab.com/3d-models/low-poly-treasure-chest-ca63751326084866b8df9a6b4c196b3d" target="_blank">low poly treasure chest</a>
          </dt>
          <dd>
            by <a href="https://sketchfab.com/cattleya" target="_blank">cattleya</a>
            under <a href="https://creativecommons.org/licenses/by/4.0/" target="_blank">CC BY 4.0</a>
          </dd>

          <dt>
            <a href="https://sketchfab.com/3d-models/pirate-compass-3a51cfca26b34da7a8ac02af373cd130" target="_blank">Pirate Compass</a>
          </dt>
          <dd>
            by <a href="https://sketchfab.com/VincentBrindisi" target="_blank">VicentBrindisi</a>
            under <a href="https://creativecommons.org/licenses/by/4.0/" target="_blank">CC BY 4.0</a>
          </dd>

          <dt>
            <a href="https://sketchfab.com/3d-models/pirate-props-a221c41019a54a1e83d154f5d3fca6e1" target="_blank">Pirate Props</a>
          </dt>
          <dd>
            by <a href="https://sketchfab.com/kuamoto" target="_blank">Iago Kuamoto</a>
            under <a href="https://creativecommons.org/licenses/by/4.0/" target="_blank">CC BY 4.0</a>
          </dd>

          <dt>
            <a href="https://sketchfab.com/3d-models/legend-of-zelda-links-awakeningrichards-villa-7a1ba628fc5640fbb7af6732c47615e2" target="_blank">Legend of Zelda Link's Awakening:Richard's Villa</a>
          </dt>
          <dd>
            by <a href="https://sketchfab.com/Eibho" target="_blank">Eibho</a>
            under <a href="https://creativecommons.org/licenses/by/4.0/" target="_blank">CC BY 4.0</a>
          </dd>

          <dt>
            <a href="https://sketchfab.com/3d-models/jar-b39c8663081c4c9e8c5e14dda1c67bd8" target="_blank">Jar</a>
          </dt>
          <dd>
            by <a href="https://sketchfab.com/Yoshiboy721" target="_blank">Josh Smith</a>
            under <a href="https://creativecommons.org/licenses/by/4.0/" target="_blank">CC BY 4.0</a>
          </dd>

          <dt>
            <a href="https://sketchfab.com/3d-models/arrow-v1-9c5b6c4ddbcc496a809e50e1fa019d6a" target="_blank">Arrow V1</a>
          </dt>
          <dd>
            by <a href="https://sketchfab.com/mobileEY" target="_blank">mobileEY</a>
            under <a href="https://creativecommons.org/licenses/by/4.0/" target="_blank">CC BY 4.0</a>
          </dd>

        </dl>
      </div>
    </div>
  </div>
</template>

<style scoped>
  h1 { font-size: 1.5rem }
  a {
    color: #eee;
    text-decoration: none;
  }
  .licences {
    margin: 2rem 0;
    font-size: 1rem;
    text-align: left;
  }
  .licences dt {
    padding-top: 0.75rem;
    font-size: 0.9rem;
    font-weight: bold;
  }
  .licences dd {
    margin-left: 0;
    font-size: 0.8rem;
  }

  #onboarding {
    position: absolute;
    top: 0;
    left: 0;
    background-color: #333;
    color: #ccc;
    width: 100vw;
    height: 100vh;
    padding: 1rem;
    font-family: monospace;
    z-index: 10000;
    overflow: auto;
  }
  #onboarding > * {
    margin: 0 auto;
    max-width: 50rem;
    width: calc(100vw - 10rem);
    text-align: center;
    border-radius: 0.3rem;
    padding: 1rem;
    font-size: 1.3rem;
  }
  #onboarding button {
    font-size: 1.3rem;
    padding: 0.5rem 1rem;
    border-radius: 0.3rem;
    background-color: white;
    color: black;
    border: none;
    cursor: pointer;
  }
</style>