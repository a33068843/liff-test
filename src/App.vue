<template>
  <div>
    <a href="https://vite.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>
  <div>
    <h1>create-liff-app</h1>
    <p v-if="message">{{ message }}</p>
    <p v-if="error">
      <code>{{ error }}</code>
    </p>
    <a
      href="https://developers.line.biz/ja/docs/liff/"
      target="_blank"
      rel="noreferrer"
    >
      LIFF Documentation
    </a>
  </div>
  <HelloWorld msg="Vite + Vue" />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue';
</script>

<script lang="ts">
import { defineComponent } from 'vue';
import liff from '@line/liff';

export default defineComponent({
  data() {
    return {
      message: '',
      error: '',
    };
  },
  mounted() {
    liff
      .init({
        liffId: import.meta.env.VITE_LIFF_ID,
      })
      .then(() => {
        this.message = 'LIFF init succeeded.';
      })
      .catch((e: Error) => {
        this.message = 'LIFF init failed.';
        this.error = `${e}`;
      });
  },
});
</script>
