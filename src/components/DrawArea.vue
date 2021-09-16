<template>
  <div id="area" ref="area"/>
  <button @click="clearArea">Clear Area</button>
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
      /* eslint-disable */
      clickAreaHandler(event) {
        const { layerX: x, layerY: y } = event;
        this.shapes.circle.push(this.rootSvgArea.circle(5).move(x, y))
      },
      clearArea() {
        for (let shape in this.shapes) {
          this.shapes[shape] = [];
        }
        this.rootSvgArea.clear();
      },
    },
    data: () => ({
      rootSvgArea: null,

      shapes: {
        circle: [],
      },
    })
  }
</script>

<style lang="scss">
  #area {
    width: 100%;
    height: 500px;
  }
</style>