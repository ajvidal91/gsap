<template>
    <!-- <div ref="box" class="box"></div> -->
    <div class="bubble-wrapper">
  <div ref="bubble" class="bubble">
    <img class="bubble-image"
         src="https://cdn-images-1.medium.com/max/800/1cuOEeHUXmh4F7QX613vKFw.png" />
  </div>
  <div ref="bubblePulse" class="bubble-pulse"></div>
</div>
</template>

<script>
    // import { TimelineLite } from 'gsap'
    // export default {
    //     mounted() {
    //     const { box } = this.$refs
    //     const timeline = new TimelineLite()
    //
    //     timeline.to(box, 5, { x: 300, rotation: 360, y: 200})
    //     }
    // }

    // import { TimelineLite, Back } from 'gsap'
    // export default {
    //   mounted() {
    //     const { box } = this.$refs
    //     const timeline = new TimelineLite()
    //
    //     timeline.to(box, 1, {
    //       x: 400,
    //       rotation: 90,
    //       ease: Back.easeInOut, // Specify an ease
    //     })
    //     timeline.to(box, 5, {
    //       background: 'green',
    //       rotation: 180,
    //       x: -200
    //     },
    //     '1' // Run the animation 1s early
    //     )
    //   }
    // }
    import { TimelineLite, Back, Elastic, Expo } from "gsap"
export default {
  mounted() {
    const { bubble, bubblePulse } = this.$refs
    const timeline = new TimelineLite()

    timeline.to(bubble, 0.4, {
      scale: 0.8,
      rotation: 16,
      ease: Back.easeOut.config(1.7),
    })
    timeline.to(
      bubblePulse,
      0.5,
      {
        scale: 0.9,
        opacity: 1,
      },
     '-=0.6'
    )

    this.timeline.to(bubble, 1.2, {
      scale: 1,
      rotation: '-=16',
      ease: Elastic.easeOut.config(2.5, 0.5),
    })
    this.timeline.to(
      bubblePulse,
      1.1,
      {
        scale: 3,
        opacity: 0,
        ease: Expo.easeOut,
      },
      '-=1.2'
    )
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.bubble-wrapper {
position: relative;
}
.bubble {
position: relative;
z-index: 2;
display: flex;
align-items: center;
justify-content: center;
border: 1px solid white;
background: #272727;
border-radius: 50%;
height: 100px;
width: 100px;
}
.bubble-pulse {
position: absolute;
z-index: 1;
height: 120px;
width: 120px;
top: 50%;
left: 50%;
margin-top: -60px;
margin-left: -60px;
background: #272727;
border-radius: 50%;
opacity: 0;
transform: scale(0);
}
.bubble-image {
height: 50%;
}
</style>
