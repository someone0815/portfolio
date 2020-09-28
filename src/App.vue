<template>
  <div id="app">
    <div id="header">
      <!-- <div class="side"></div> -->
      <div class="mid">
        <a href="fb.com">
          <img
            class="logo"
            src="/svg/personal-logo.svg"
            alt="Kiwi standing on oval"
          />
        </a>
        <div class="search">
          <input type="search" name="search" id="search" />
        </div>
        <div class="links">
          <a href="fb.com">Projects</a>
          <a href="fb.com">Contact</a>
          <a href="fb.com">Impressum</a>
        </div>
      </div>
      <!-- <div class="side"></div> -->
    </div>
    <div class="splash"></div>
    <MainView />
  </div>
</template>

<script>
import MainView from './components/MainView.vue';

export default {
  name: 'App',
  components: {
    MainView,
  },
};
</script>

<style>
/* HEADER */

.splash {
  width: 100%;
  height: 36rem;
  position: absolute;
  background: hsl(0deg 0% 99%);
  z-index: -10;
  top: 0;
  background: linear-gradient(0deg, rgb(242 242 242) 0%, rgb(247 247 247) 100%);
}

#header {
  display: grid;
  grid-template: 'main ';
  grid-template-columns: minmax(600px, 1620px);
  place-content: center;
  position: fixed;
  width: 100%;
  background-color: #fff;
  height: 60px;
  box-shadow: 0 0 1px rgba(0, 0, 0, 0.25);
  z-index: 1000;
  top: 0;
}
.search > input[type='search'] {
  padding: 0.6rem 1rem;
  border: 0;
  background: #f7f7f7;
  border-radius: 100px;
  width: 350px;
}
div.mid {
  /* max-width: 1000px; */
  width: 100%;
  display: flex;
  place-items: center;
  justify-content: space-between;
}
.links {
  gap: 1rem;
  display: flex;
}
.mid > .links > a:hover {
  text-decoration: underline;
}
.mid > .links > a {
  text-decoration: none;
  color: gray;
}
.side {
  /* width: 250px; */
  /* padding: 1rem; */
}
.logo {
  height: 60px;
}
</style>

<style>
:root {
  --txt: ##3a322c;
  /* --bg: #fff; */
  --bg: #ffffff;
  --bg-root: #fff;
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
</style>
