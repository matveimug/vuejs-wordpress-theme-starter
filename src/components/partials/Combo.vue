<template>
  <div class="Combo">
    <h-product class="Product" :colors="combo" :scale=".3"/>
  </div>
</template>

<script>
  import Color from "color"

  export default {
    props: ['combo'],
    methods: {
      bgColor() {
        const color = Color(this.combo.accent).mix(Color(this.combo.main), 0.3).hsl();
        // color.color[1] = 20;
        color.color[2] = 97;
        const bgColor = 'background-color: ' + color;
        const bgGradient = 'background-image: linear-gradient(132deg,' + this.combo.accent + ',' + this.combo.main + ')'
        return bgColor
      }
    },
  }

</script>

<style scoped>
  .Combo {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    background: white;
  }

  .Product {
    width: 100%;
    height: 100%;
  }

  span {
    padding-top: 2em;
    text-align: center;
    font-size: .7em;
  }
</style>