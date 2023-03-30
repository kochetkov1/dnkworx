<template>
  <div ref='vantaRef' class="background">
  </div>
</template>

<script>
import * as THREE from "three";
import HALO from 'vanta/dist/vanta.halo.min'
// Make sure window.THREE is defined, e.g. by including three.min.js in the document head using a <script> tag

export default {
  mounted() {
    this.vantaEffect = HALO({
      el: this.$refs.vantaRef,
      THREE: THREE
    })
  },
  beforeUnmount() {
    if (this.vantaEffect) {
      this.vantaEffect.destroy()
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
.background {
  min-width: 800px;
  min-height: 800px;
  height: 100%;
}

h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
