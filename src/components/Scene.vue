<template>
  <div id="container" />
</template>

<script>
import * as THREE from "three";

const camera = new THREE.PerspectiveCamera(
  70,
  window.innerWidth / window.innerHeight,
  0.01,
  50
);

const scene = new THREE.Scene();
const renderer = new THREE.WebGLRenderer({ antialias: true });
const geometry = new THREE.BoxGeometry();
const manager = new THREE.LoadingManager();
var loader = new THREE.TextureLoader(manager);
var material = new THREE.MeshBasicMaterial({
  map: loader.load("https://threejs.org/examples/textures/crate.gif"),
  side: THREE.DoubleSide,
});
const mesh = new THREE.Mesh(geometry, material);

export default {
  mounted() {
    camera.position.z = 5;
    scene.add(mesh);
    renderer.setSize(window.innerWidth, window.innerHeight);
    renderer.setAnimationLoop(this.animation);

    // manager is mounted and when you run console.log it returns an `LoadingManager` object
    console.log(manager);

    // event not being called
    manager.onStart = function (url, itemsLoaded, itemsTotal) {
      console.log(
        "Started loading file: " +
          url +
          ".\nLoaded " +
          itemsLoaded +
          " of " +
          itemsTotal +
          " files."
      );
    };

    const canvas = document.getElementById("container");
    canvas.appendChild(renderer.domElement);
  },

  methods: {
    animation(time) {
      mesh.rotation.x = time / 2000;
      mesh.rotation.y = time / 1000;

      renderer.render(scene, camera);
    },
  },
};
</script>

<style></style>
