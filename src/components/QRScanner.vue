<template>
    <div id="qr-code-full-region"></div>
  </template>
  
  <script setup>
  import { onMounted } from 'vue';
  import { Html5QrcodeScanner } from 'html5-qrcode';
  
  const qrbox = 250; // Set the size of the QR code scanning region
  const fps = 1; // Set the desired frames per secondss
  // eslint-disable-next-line
  const emit  = defineEmits('result');

  const onScanSuccess = (decodedText, decodedResult) => {
    // Handle the scanned QR code result
    console.log('Decoded Text:', decodedText);
    console.log('Decoded Result:', decodedResult);
    emit('result', decodedText, decodedResult )
  };
  
  onMounted(() => {
    const config = {
      fps: fps,
      qrbox: qrbox,
    };
  
    const html5QrcodeScanner = new Html5QrcodeScanner(
      "qr-code-full-region", // ID of the element to render the scanner
      config
    );
  
    html5QrcodeScanner.render(onScanSuccess, () => {});
  });
  </script>
  
  