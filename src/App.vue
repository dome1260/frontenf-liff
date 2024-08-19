<template>
  <router-view></router-view>
</template>

<script setup>
import { onMounted } from 'vue';
import liff from '@line/liff';

const liffInit = async () => {
  try {
    await liff.init({ liffId: '2006119518-8daoqjQj' })
    await liff.ready
    if (!liff.isLoggedIn()) {
      liff.login()
    }
  } catch (error) {
    console.error('[ERROR] liff init =>', error)
  }
}

onMounted(() => {
  liffInit()
})

</script>
