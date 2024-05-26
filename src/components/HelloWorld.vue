<script setup>
import { ref } from 'vue'

defineProps({
  msg: String
})

const count = ref(0);
</script>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      posts: null,
      loading: null
    }
  },
  methods: {
    async getPosts() {
      this.loading = true

      this.posts = await axios.get('/.env');

      document.getElementById("data").textContent = this.posts.data;
      console.log(this.posts.data);

      this.loading = null
    }
  }
}
</script>

<template>
  <div id="header">
    <h1>{{ msg }}</h1>
    <h2 id="data"></h2>
  </div>

  <div class="card">
    <button type="button" @click="count++; getPosts();">count is {{ count }}</button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Install
    <a href="https://github.com/vuejs/language-tools" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
