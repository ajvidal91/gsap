<template>
    <div ref="box" class="box"></div>
</template>

<script>
    import { TimelineLite } from 'gsap'
    export default {
        mounted() {
        const { box } = this.$refs
        const timeline = new TimelineLite()

        timeline.to(box, 5, { x: 300, rotation: 360, y: 200})
        }
    }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .box {
      height: 60px;
      width: 60px;
      background: red;
    }
</style>
