<template>
  <mark ref="marker"></mark>
</template>

<script>
  import { mapState, mapGetters } from 'vuex'
  import { TimelineLite } from 'gsap';
  export default {
    props: ['top'],
    computed: {
      ...mapState('mittens', ['selected']),
      ...mapGetters('mittens', ["watchSelected"]),
    },
    data() {
      return {
        timeline: {},
        marker: {},
        parent_y: {}
      }
    },
    mounted() {
      this.doAnimation(this.top);
    },
    methods: {
      doAnimation: function (val) {
        const timeline = new TimelineLite();
        const { marker } = this.$refs;
        timeline.to(marker, 1, {
          ease: Expo.easeInOut,
          top: val
        });
      }
    },
    watch: {
      deep: true,
      top: function(newVal) {
        this.doAnimation(newVal);
      }
    }
  }
</script>

<style lang="scss" scoped>
  @import "../../assets/scss/variables";
  mark {
    position: absolute;
    border-radius: 50%;
    border: $h-border;
    width: $h-markersize;
    height: $h-markersize;
    margin: $h-markermargin;
    background: transparent;
  }
</style>