<template>
  <div id="area" ref="area"/>
</template>

<script>
  import { SVG } from '@svgdotjs/svg.js'

  export default {
    name: 'DrawArea',
    mounted() {
      const { width, height } = this.$refs.area.getBoundingClientRect();
      this.rootSvgArea = SVG().addTo(this.$refs.area).size(width, height);
      // this.rootSvgArea.rect(100, 100).attr({ fill: '#f06' });

      this.rootSvgArea.click(this.clickAreaHandler);
    },
    methods: {
      clickAreaHandler(event) {
        console.log(event.target.getBoundingClientRect());
      },
    },
    data: () => ({
      rootSvgArea: null,
    })
  }
</script>

<style lang="scss">
  #area {
    width: 100%;
    height: 500px;
  }
</style>