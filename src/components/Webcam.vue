<script setup>
import { onMounted, ref } from 'vue'
import Webcam from '@/vendors/webcam-easy';

onMounted(() => {
    const webcamElement = document.getElementById('webcam');
    const canvasElement = document.getElementById('canvas');
    const snapSoundElement = document.getElementById('snapSound');
    const webcam = new Webcam(webcamElement, 'user', canvasElement, snapSoundElement);

    webcam.start()
    .then(result =>{
        console.log("webcam started");
    })
    .catch(err => {
        console.log(err);
    });
})
</script>

<template>
    <video id="webcam" autoplay playsinline width="640" height="480"></video>
    <canvas id="canvas" class="d-none"></canvas>
    <audio id="snapSound" src="audio/snap.wav" preload = "auto"></audio>
</template>