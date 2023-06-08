<template>
  <div id="app">
    <div class="section" style="width: 500px; margin: auto;">
        <QRScanner
            v-bind:qrbox="250"
            v-bind:fps="10"
            style="width: 500px;"
            @result="onScan" />
       
    </div>
    <div>
  <h1>Results</h1>
  <div v-for="(item, index) in items" :key="index">{{item}}</div>
  
  
    </div>
  </div>
  </template>
  
  
  
  <script setup >
  import QRScanner from './components/QRScanner.vue';
  import { ref } from 'vue';
  
  const items = ref([])
    function onScan(decodedText, decodedResult) {
      items.value.push(decodedText)
      console.log("decodedText", decodedText);
      console.log("decodedResult", decodedResult);
    }
  
  
  </script>
  