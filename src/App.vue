<script setup lang="ts">
import * as THREE from 'three';
import {onMounted} from 'vue';

onMounted(()=>{
  const camera = new THREE.PerspectiveCamera( 70, 1, 0.01, 10 );
camera.position.z = 1;
const scene = new THREE.Scene();
const geometry = new THREE.BoxGeometry( 0.2, 0.2, 0.2 );
const material = new THREE.MeshNormalMaterial();

const mesh = new THREE.Mesh( geometry, material );
scene.add( mesh );

const renderer = new THREE.WebGLRenderer( { antialias: true } );
renderer.setSize( 700, 700 );
renderer.setAnimationLoop( animation );

function animation( time: number ) {
  mesh.rotation.x = time / 2000;
  mesh.rotation.y = time / 1000;
  renderer.render( scene, camera );  
}

const threeDemoBox =  document.getElementById('three-demo-1');
if(threeDemoBox){
  threeDemoBox.appendChild( renderer.domElement );
}
})



</script>

<template>
  <div id="three-demo-1">
  </div>
</template>

<style scoped>
</style>
