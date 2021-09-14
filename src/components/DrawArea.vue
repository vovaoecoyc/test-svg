<template>
  <div id="area" ref="area">

  </div>
</template>

<script>
  import { SVG } from '@svgdotjs/svg.js'

  export default {
    name: 'DrawArea',
    mounted() {
      this.rootSvgArea = SVG().addTo(this.$refs.area).size(150, 150);
      this.rootSvgArea.rect(100, 100).attr({ fill: '#f06' });
      setTimeout(() => {
        this.rootSvgArea.clear();
      }, 4000);
    },
    data: () => ({
      rootSvgArea: null,
    })
  }
</script>

<style lang="scss" scoped>

</style>