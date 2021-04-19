<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" @send-value="getValue">
      <div>This is in side hello world component</div>
      <template v-slot:header>
        <div>Here might be a page title</div>
      </template>
    </HelloWorld>
    <div>Count is {{ count }}</div>
    <teleport to="#teleport">
      this is teleported content
    </teleport>
  </div>
</template>

<script>
import { ref } from 'vue';
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue';

export default {
  name: 'Home',
  setup() {
    const count = ref(1);
    return { count };
  },
  components: {
    HelloWorld,
  },
  provide() {
    return {
      testProvide: 'testInject',
    };
  },
  methods: {
    getValue(val) {
      window.console.log(val);
    },
  },
};
</script>
