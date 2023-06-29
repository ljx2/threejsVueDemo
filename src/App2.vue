<script setup>
import * as THREE from 'three'; // 全局引入
import { GLTFLoader } from 'three/addons/loaders/GLTFLoader.js';
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls.js'

const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);

const scene = new THREE.Scene();

const camera = new THREE.PerspectiveCamera(45, window.innerWidth / window.innerHeight, 1, 10000);
camera.position.set(0, 0, 500);
camera.lookAt(100, 0, 0);

const controls = new OrbitControls(camera, renderer.domElement);
controls.update();

const loader = new GLTFLoader();
loader.load('src/model/scene.gltf', function (gltf) {
  scene.add(gltf.scene);
  function animate() {
    requestAnimationFrame(animate);
    // required if controls.enableDamping or controls.autoRotate are set to true
    controls.update();
    renderer.render(scene, camera);
  }
  animate()
}, function (ProgressEvent) {
  console.log(ProgressEvent);
}, function (error) {
  console.error(error);
});

</script>

<template>
</template>

<style scoped>
</style>
