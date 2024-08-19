<template>
  <div class="container">
    <div>
      <div class="qr-text">
        {{ scanResult }}
      </div>
      <button class="btn" @click="openScanner()">
        Button
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import liff from '@line/liff';

const scanResult = ref('')

const openScanner = async () => {
  try {
    const result = await liff.scanCodeV2()
    scanResult.value = result.value
    alert('scan สำเร็จ')
  } catch (error) {
    console.error('[ERROR] open scanner =>', error)
  }
}
</script>

<style scoped>
.container {
  max-width: 500;
  height: 100vh;
  margin: 0 auto;
  padding: 16px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.btn {
  padding: 16px;
  height: 40px;
  border-radius: 4px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.qr-text {
  padding: 16px;
  margin-bottom: 16px;
  border: 1px solid black;
}
</style>
