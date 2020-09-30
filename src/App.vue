<template>
  <div id="app">
    <div id="header">
      <!-- <div class="side"></div> -->
      <div class="mid">
        <div class="logo-holder">
          <a href="fb.com">
            <img
              class="logo"
              src="/svg/personal-logo.svg"
              alt="Kiwi standing on oval"
            />
          </a>
        </div>

        <SearchBox />
        <div class="links">
          <div class="buttons">
            <button>Projects</button>
            <button>Contact</button>
            <button>Impressum</button>
          </div>
          <div class="lang">
            <div class="option">
              <input type="radio" name="Lang" id="ger-radio" />
              <label for="ger-radio">
                <img
                  src="/svg/flags/rounded/germany.svg"
                  alt="German Language"
                />
              </label>
            </div>
            <div class="option">
              <input type="radio" name="Lang" id="rus-radio" />
              <label for="rus-radio">
                <img
                  src="/svg/flags/rounded/russia.svg"
                  alt="Russian Language"
                />
              </label>
            </div>
            <div class="option">
              <input type="radio" name="Lang" id="eng-radio" checked />
              <label for="eng-radio">
                <img
                  src="/svg/flags/rounded/united-kingdom.svg"
                  alt="English Language"
                />
              </label>
            </div>
          </div>
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
import SearchBox from './components/globals/SearchBox.vue';

export default {
  name: 'App',
  components: {
    MainView,
    SearchBox,
  },
};
</script>

<style scoped>
/* LANGUAGE */
.lang {
  display: grid;
  grid-auto-flow: column;
  background: #f1f1f1;
  border-radius: 100px;
  height: 100%;
  gap: 0.4rem;
}
.lang input[type='radio'] {
  display: none;
}

.lang .option {
  width: 2rem;
  height: 100%;
}
.lang:hover > .option > label > img {
  opacity: 1;
  filter: grayscale(0);
}
.lang > .option > label > img {
  width: 2rem;
  height: 100%;
  padding: 0.4rem;
  box-sizing: border-box;
  cursor: pointer;
  transition: transform 0.1s, opacity 0.1s;
  opacity: 0.45;
  filter: grayscale(1);
}
.lang > .option > label > img:hover {
  filter: grayscale(0), saturate(10%);
}

input[type='radio']:checked + label > img {
  border-radius: 100px;
  transform: scale(1.45);
  filter: grayscale(0) !important;
  opacity: 1;
}
</style>

<style scoped>
/* HEADER */

@media screen and (max-width: 1650px) {
  #header {
    padding: 0rem 1rem;
    box-sizing: border-box;
  }
}
.buttons > button:hover {
  color: gray;
}
.buttons > button {
  margin: 0;
  height: 100%;
  background: 0;
  border: 0;
  font-weight: 600;
  cursor: pointer;
  padding: 0.5rem;
  color: #585858;
}
.buttons {
  height: 100%;
  display: flex;
  justify-content: space-evenly;
  width: inherit;
  max-width: 20rem;
  justify-self: center;
  /* margin: auto; */
  /* justify-self: center;*/
}

.logo-holder {
  justify-self: flex-start;
}

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
div.mid {
  place-items: center;
  display: grid;
  grid-auto-flow: column;
  grid-template-columns: 1fr auto 1fr;
}
.links {
  gap: 1rem;
  display: grid;
  grid-auto-flow: column;
  grid-template-columns: 1fr auto;
  align-items: center;
  /* justify-self: flex-end; */
  width: 100%;
}
.mid > .links > a:hover {
  text-decoration: underline;
}
.mid > .links > a {
  text-decoration: none;
  color: gray;
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
