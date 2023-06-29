<script setup>
import * as THREE from 'three'; // 全局引入
import { GLTFLoader } from 'three/addons/loaders/GLTFLoader.js';

const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);

const camera = new THREE.PerspectiveCamera(45, window.innerWidth / window.innerHeight, 1, 500);
camera.position.set(0, 0, 500);
camera.lookAt(0, 0, 0);

const scene = new THREE.Scene();

// const material = new THREE.LineBasicMaterial({ color: 0x0000ff });
// const points = [];
// points.push(new THREE.Vector3(- 10, 0, 0));
// points.push(new THREE.Vector3(0, 10, 0));
// points.push(new THREE.Vector3(10, 0, 0));

// const geometry = new THREE.BufferGeometry().setFromPoints(points);

// const line = new THREE.Line(geometry, material);

const loader = new GLTFLoader();

loader.load('src/model/scene.gltf', function (gltf) {
  scene.add(gltf.scene);
  // scene.add(line);
  renderer.render(scene, camera);
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
