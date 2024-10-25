<script setup>
import MailSlot from './components/MailSlot.vue'
</script>

<template>
  <header>
    <h1>ICメール</h1>
    <div></div>
  </header>

  <main>
    <MailSlot />
  </main>
</template>

<style scoped>
header {
  display: flex;
  flex-direction: column;
  place-items: center;
}

header h1 {
  display: flex;
  flex-direction: column;
  place-items: center;
  height: 80px;
  line-height: 80px;
}

header > div {
  border-bottom: 4px solid #000000;
  width: 100%;
  height: 80px;
  background-color: #1D4ED8;
}

main {
  display: flex;
  justify-content: center;
  place-items: center;
  width: 100%;
  height: 100%;
}
</style>
