<template>
  <div id="app">
    <Navbar />
    <div class="splash"></div>
    <MainView />
  </div>
</template>

<script>
import Navbar from './components/globals/Navbar.vue';
import MainView from './components/MainView.vue';

export default {
  name: 'App',
  components: {
    Navbar,
    MainView,
  },
  data: () => ({
    size: 'xl',
  }),
  mounted() {
    window.onresize = this.lodash.debounce(this.detectSize, 50);
    this.detectSize();
  },
  methods: {
    detectSize() {
      const width = window.innerWidth;
      let result = {};
      switch (true) {
        case width < 425:
          result = {
            size: 'mobile',
            sizeint: 425,
            range: [0, 425],
            includes: ['mobile'],
          };
          break;
        case width < 680:
          result = {
            size: 's',
            sizeint: 680,
            range: [426, 680],
            includes: ['mobile', 's'],
          };
          break;
        case width < 1024:
          result = {
            size: 'm',
            sizeint: 1024,
            range: [680, 1024],
            includes: ['mobile', 's', 'm'],
          };
          break;
        case width < 1300:
          result = {
            size: 'l',
            sizeint: 1300,
            range: [1025, 1300],
            includes: ['mobile', 's', 'm', 'l'],
          };
          break;
        case width < 1600:
          result = {
            size: 'xl',
            sizeint: 1600,
            range: [1301, 1600],
            includes: ['mobile', 's', 'm', 'l', 'xl'],
          };
          break;
        default:
          result = {
            size: 'xl',
            sizeint: 1600,
            range: [1301, 1600],
            includes: ['mobile', 's', 'm', 'l', 'xl'],
          };
      }
      this.size = {
        width: width,
        size: result.size,
        sizeint: result.sizeint,
        range: result.range,
        includes: result.includes,
      };
    },
  },
};
</script>

<style scoped>
.splash {
  width: 100%;
  height: 36rem;
  position: absolute;
  background: hsl(0deg 0% 99%);
  z-index: -10;
  top: 0;
  background: linear-gradient(0deg, rgb(242 242 242) 0%, rgb(247 247 247) 100%);
}
</style>

<style scoped>
/* HEADER */
</style>

<style>
:root {
  --txt: ##3a322c;
  /* --bg: #fff; */
  --bg: #ffffff;
  --bg-root: #fff;
}

img {
  display: block;
}
#app {
  /* font-family: 'Roboto', sans-serif; */
  font-family: 'Inter', sans-serif;
  /* font-family: 'Source Sans Pro', 'HelveticaNeue', sans-serif; */
  /* font-family: 'HelveticaNeue', sans-serif; */
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
@font-face {
  font-family: 'HelveticaNeue';
  src: url('/fonts/HelveticaNeue.ttf') format('ttf');
  font-weight: normal;
}

@font-face {
  font-family: 'HelveticaNeue';
  src: url('fonts/HelveticaNeue-Bold.ttf') format('ttf');
  font-weight: bold;
}
@font-face {
  font-family: 'HelveticaNeue';
  src: url('fonts/HelveticaNeue-Medium.ttf') format('ttf');
  font-weight: 500;
}
@font-face {
  font-family: 'HelveticaNeue';
  src: url('fonts/HelveticaNeue-Light.ttf') format('ttf');
  font-weight: 300;
}
/* 
@font-face {
  font-family: 'myfont';
  src: url('fonts/awesome-font-boldoblique.woff') format('woff');
  font-weight: bold;
  font-style: italic;
}

@font-face {
  font-family: 'myfont';
  src: url('fonts/awesome-font-oblique.woff') format('woff');
  font-style: italic;
} */
body {
  background: #f1f1f1;
}
html {
  scroll-padding-top: 70px; /* height of sticky header */
  scroll-behavior: smooth !important;
}
</style>
