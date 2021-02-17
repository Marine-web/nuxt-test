<template>
  <b-container>
    <div>
      <h1  class="text"> 
        TESTING
      </h1>
      <div :style="cursorCircle" class="cursor">
      </div>
    </div>
    <video autoplay muted loop id="myVideo">
      <source src="~/assets/video/video.mp4" type="video/mp4">
    </video>
  </b-container>
  
</template>

<script>

export default {
  data() {
    return {
      xParent: 0,
      yParent: 0,
    }
  },
  computed: {
    cursorCircle() {
      return `transform: translateX(${this.xParent}px) translateY(${this.yParent}px) translateZ(0) translate3d(0, 0, 0);`
    },
  },
  mounted(){
    
    window.addEventListener('mousemove',this.moveCursor)
  },
  methods:{
    moveCursor(e) {
      this.xChild = e.clientX;
      this.yChild = e.clientY;
      setTimeout(() => {
        this.xParent = e.clientX - 15;
        this.yParent = e.clientY - 15;
      }, 10);
    }
  }

}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.text {
  position: relative;
  mix-blend-mode: difference;
  z-index: 1;
  -webkit-text-stroke: 2px #fff;
  font-family: sans-serif;
  display: block;
  font-weight: 300;
  font-size: 10em;
  color: #ffffff;
  letter-spacing: 1px;
}
video{
  position: fixed;
  right: 0;
  bottom: 0;
  min-width: 100%;
  min-height: 100%;
}


.cursor {
  position: fixed;
  pointer-events: none;
  -webkit-user-select: none;
  mix-blend-mode: difference;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  top: 0;
  left: 0;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
  border-radius: 100%;
  z-index: 2;
  opacity: 1;
  background: #fff;
  width: 8em;
  height: 8em;
  transition: width .6s ease, height .6s ease, opacity .6s ease;
}
</style>
