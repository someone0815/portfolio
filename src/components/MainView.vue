<template>
  <div class="main-view">
    <div class="sider sidebar">
      <div class="holder" id="myHeader2">
        <span v-for="x in 1" :key="x">Lorem Text {{ x }}<br /></span>
      </div>
    </div>
    <div class="main">
      <h2>Projects</h2>
      <div class="filters">
        <!-- <span class="text">
          Select topics of your interest or
          <input type="text" placeholder="search" />
          manually.
        </span> -->
        <!-- <div class="group">
          <ol v-for="(category, index) in filter" :key="category">
            <h4>{{ index }}</h4>
            <li v-for="subcat in category" :key="subcat">
              <input
                class="checkbox"
                type="checkbox"
                :id="subcat"
                :name="subcat"
              />
              <label :for="subcat">{{ subcat }}</label>
            </li>
          </ol>
        </div> -->
      </div>
      <div class="project-card" v-for="item in 3" :key="item">
        <div class="thumbnail">
          <img src="https://i.imgur.com/GHfGzEv.png" alt="" />
        </div>
        <a href="fb.com">
          <h3>Sneaker & Clothing Store</h3>
        </a>
        <span class="time">
          <div class="links">
            4 weeks ago -
            <a href="fb.com" class="tag">Vue</a>,
            <a href="fb.com" class="tag">nodeJS</a>,
            <a href="fb.com" class="tag">MongoDB</a> &
            <a href="fb.com" class="tag">more</a>.
          </div>
        </span>
        <p class="description">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam
          illum, porro repellendus, error maiores facilis provident vel. Sunt
          recusandae mollitia aut explicabo unde rerum.
        </p>
        <div class="links pins">
          <!-- <button>Demo</button> -->
          <!-- <button>GitHub</button> -->
          <a href="fb.com" class="link">
            Demo <fa fas="external-link-alt"></fa>
          </a>
          <a href="fb.com" class="link">
            Github <fa fas="external-link-alt"></fa>
          </a>
        </div>
      </div>
    </div>
    <div class="sider">
      <div class="holder" id="myHeader">
        <div class="item">
          <!-- <h4>Projects</h4> -->
          <div class="group sidebargroup">
            <ol v-for="(category, index) in filter" :key="category">
              <h4>{{ index }}</h4>
              <li v-for="subcat in category" :key="subcat">
                <input
                  class="checkbox"
                  type="checkbox"
                  :id="subcat"
                  :name="subcat"
                />
                <label :for="subcat">{{ subcat }}</label>
              </li>
            </ol>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    filter: {
      framework: ['Vue', 'React', 'Angular', 'Electron'],
      backend: ['nodeJS', 'Express', 'PHP', 'GraphQL'],
      database: ['MongoDB', 'MySQL', 'SQLite', 'PostgreSQL'],
      system: ['Python', 'Robotics', 'C#', 'C++'],
      // general: ['Frontend', 'Backend', 'E-commerze', 'ML'],
    },
  }),
  mounted() {
    // var element = document.getElementById('myHeader');
    // console.log(element);
    // console.log('mounted');
    // window.onscroll = function() {
    // myFunction();
    // };
    // var realheader = document.getElementById('header');
    // var header = document.getElementById('myHeader');
    // // var header2 = document.getElementById('myHeader2');
    // var sticky = header.offsetTop - realheader.clientHeight;
    // function myFunction() {
    // var space = window.innerHeight - element.offsetTop + element.offsetHeight;
    // console.log(space);
    // }
  },
};
</script>

<style scoped>
/* width */

.holder {
  scrollbar-color: #bebebe transparent;
  /* where red is the bar and green is thumb */
  scrollbar-width: thin;
  /* other option is thick */
}
.holder:hover {
  scrollbar-color: #bebebe #f2f2f2;

  scrollbar-width: revert !important;
}

.holder::-webkit-scrollbar {
  width: 15px;
  padding: 10px;
}

/* Track */
.holder::-webkit-scrollbar-track {
  /* box-shadow: inset 0 0 5px grey; */
  /* background: #f1f1f1; */
  /* border-radius: 10px; */
}

/* Handle */
.holder::-webkit-scrollbar-thumb {
  /* background: red; */
  border-radius: 10px;
  /* width: 10px !important; */
  background-color: #bebebe;
  /* background-color: #818b99; */
  border: 5px solid transparent;
  /* border-radius: 9px; */
  background-clip: content-box;
  /* box-shadow: 0 0 5px grey; */
}

/* Handle on hover */
/* .holder::-webkit-scrollbar-thumb:hover {
  background: #818b99;
} */

.sider:hover .holder::-webkit-scrollbar {
  width: 15px;
}

.sider:hover .holder::-webkit-scrollbar-track {
  /* box-shadow: inset 0 0 5px grey; */
  border-radius: 10px;
}

.sider:hover .holder::-webkit-scrollbar-thumb {
  /* background: red; */

  border: 0;
  border-radius: 10px;
}

.sider:hover .holder::-webkit-scrollbar-thumb:hover {
  background: #818b99;
}

/* .sticky {
  position: fixed;
  top: 60px;
  width: 100%;
}
.sticky + .holder {
  padding-top: 102px;
} */
/* #myHeader {
  position: -webkit-sticky;
  position: sticky;
  top: 60px;
} */
.sider {
  height: 100%;
  width: 310px;
  background: #fcfcfc;
}
.holder {
  background: hsl(0 0% 99% / 1);
  padding: 1rem;
  position: -webkit-sticky;
  position: sticky;
  top: 60px;
  height: calc(100vh - 90px);
  overflow-y: auto;
}
.sidebargroup > ol {
  flex: 1 1 10em !important;
}
.sidebargroup {
  margin-left: 0.5rem;
}
.sidebargroup h4 {
  margin: 0.2em 0em 0.4rem 0rem;
  text-transform: capitalize;
  color: #b2b2b2;
  font-size: 15px;
  text-transform: uppercase;
  letter-spacing: 0.02rem;
  font-size: 12px !important;
  font-weight: 700 !important;
  cursor: default;
}
.sidebargroup label {
  display: grid;
  grid-auto-flow: column;
  grid-template-columns: auto 1fr;
  align-items: center;
  gap: 0.9rem;
  padding: 0.3rem 0rem;
}
.sidebargroup li {
  color: hsl(210 1% 45% / 1);
}
.sidebargroup {
  display: flex;
  flex-wrap: wrap;
  gap: 1.5rem !important;
  /* background: hsl(0 0% 99% / 1); */
  padding: 1rem 0rem;
  overflow: hidden;
  border-radius: 0.5rem;
}
.item > h4 {
  margin: 0.2em 0em 0.2rem 0rem;
  text-transform: capitalize;
  color: #2d2d2d;
  font-weight: bold;
  font-size: 15px;
  text-transform: uppercase;
  letter-spacing: 0.02rem;
}
.sidebar {
  justify-self: right;
}

.link .fas {
  font-size: 0.8rem;
}

input[type='checkbox'] {
  display: none;
}
label {
  display: grid;
  grid-auto-flow: column;
  grid-template-columns: auto 1fr;
  align-items: center;
  gap: 0.9rem;
  padding: 0.5rem 0rem;
}
input[type='checkbox'] + label::before {
  -webkit-mask-box-image-repeat: round;
  -webkit-mask-repeat: no-repeat;
  height: 16px;
  width: 16px;
  background-color: #dadada;
  -webkit-mask-image: url(/svg/check-square-regular.svg);
  mask-image: url(/svg/check-square-regular.svg);
  display: block;
  content: '';
  float: left;
}
input[type='checkbox'] + label:hover {
  /* text-shadow: 1px 0 0 red; */
  /* outline: solid 5px #fc5185; */
  -webkit-text-stroke: 0.02rem black;
}
input[type='checkbox'] + label:hover::before {
  background-color: gray !important;
}
input[type='checkbox']:checked + label::before {
  /* box-shadow: inset 0px 0px 0px 3px #fff; */
  /* background-image: url('/svg/check-square-solid.svg'); */
  -webkit-mask-image: url(/svg/check-square-solid.svg);
  mask-image: url(/svg/check-square-solid.svg);
  background-color: #595959;
  /* background-color: gray; */
}
input[type='checkbox']:checked + label {
  font-weight: bold;
}

.group li > label,
.group li > input {
  cursor: pointer;
}
.group li {
  /* display: grid; */
  /* grid-auto-flow: column; */
  /* grid-template-columns: auto 1fr; */
  /* align-items: center; */
  /* gap: 0.9rem; */
  color: hsl(210 1% 33% / 1);
  /* font-size: 14px; */
  letter-spacing: 0.2px;
  font-size: 14px;
  font-weight: 500;
  /* padding: 0.5rem 0rem;*/
}

/* .group button:focus {
  outline: 0;
} */
/* .group button:hover {
  -webkit-text-stroke: 0.04rem black;
} */
/* .group button {
  border: 0;
  background: 0;
  cursor: pointer;
  width: 100%;
  text-align: left;
  padding: 0.4rem 0rem;
  white-space: nowrap;
} */
.group h4 {
  margin: 0.2em 0em 1rem 0rem;
  text-transform: capitalize;
  color: #b2b2b2;
  font-size: 15px;
  text-transform: uppercase;
  letter-spacing: 0.02rem;
}
.group {
  display: flex;
  flex-wrap: wrap;
  gap: 2.5rem;
  /* background: hsl(0 0% 99% / 1); */
  padding: 1rem 0rem;
  overflow: hidden;
  border-radius: 0.5rem;
  /* box-shadow: 0 10px 15px -3px rgba(0,0,0,.1),0 4px 6px -2px rgba(0,0,0,.05)!important; */
}
.group > ol {
  flex: 1 1 7em;
  list-style: none;
  margin: 0;
  padding: 0;
}
.filters > .text {
  padding: 0.5em 0em;
  display: block;
}
.filters > .text > input {
  width: 125px;
  border: 0;
  background: 0;
  margin: 0rem 0.3rem;
  border-bottom: 1px solid gray;
}
.filters {
  margin: 2rem 0rem;
}

h2 {
  font-size: 35px;
  border-bottom: 2px solid gainsboro;
  /* padding: 0em 1em; */
  color: #3f3f3f;
  cursor: default;
}
/* .pins > .exp { */
/* font-size: 1.1rem; */
/* align-self: center; */
/* } */

.links > a:hover {
  text-decoration: underline;
}
.links > a {
  color: #545454;
  font-weight: 600;
  text-decoration: none;
}
.links > * {
  /* margin: 0.2rem; */
}
.tag:hover {
  text-decoration: underline;
}
.links {
  overflow: hidden;
  text-overflow: ellipsis;
  -webkit-line-clamp: 1;
  -webkit-box-orient: vertical;
  display: -webkit-box;
  color: gray !important;
  cursor: default;
}
.tags {
  color: gray;
  /* font-style: italic; */
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 1;
  -webkit-box-orient: vertical;
}
h3 {
  font-weight: 500 !important;
  color: hsl(25 5% 15% / 1);
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 1;
  -webkit-box-orient: vertical;
}
a.tag {
  margin: 0 !important;
  color: gray !important;
  font-weight: 400 !important;
  text-decoration: none;
  /* font-style: italic; */
}
.link a {
  color: gray;
  font-weight: 400;
  font-style: italic;
}
.link {
  padding: 0.5rem 1rem 0.5rem 0rem;
}

.pins.group > button {
  margin-bottom: 0.7rem;
}
.pins > button:focus {
  border: 1px solid black !important;
  outline: 0;
}
.pins > button:hover {
  background: #efefef87;
  border: 1px solid gray;
  cursor: pointer;
}
.pins > button {
  color: #494949;
  border-radius: 100px;
  cursor: default;
  margin-right: 0.7rem;
  display: inline-block;
  background: rgb(0 0 0 / 0.04);
  letter-spacing: 0.03rem;
  padding: 0.4em 1.4em;
  font-size: 15px;
  border: 1px solid transparent;
}
/* .pins { */
/* display: flex; */
/* } */
img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.thumbnail {
  grid-area: thumb;
  border-radius: 0.5rem;
  overflow: hidden;
  /* width: 100px; */
  /* height: 60px; */
}
.description {
  color: hsl(0 0% 25% / 1);
  max-width: 500px;
  margin: 0;
  /* font-family: 'Merriweather', 'Montserrat', sans-serif; */
  /* font-style: italic; */
  font-weight: 300;
  font-size: 15px;
  max-height: 80px;
  line-height: 1.7;
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
}
.time {
  color: gray;
  font-size: 14px;
  margin: 0.1rem 0;
}

.project-card > a {
  text-decoration: none;
}
.project-card > a:hover {
  text-decoration: underline;
}

.project-card h3 {
  margin-top: 0rem;
  margin-bottom: 0rem;
  font-weight: 400;
  letter-spacing: 0.02rem;
  font-size: x-large;
}
.project-card {
  display: grid;
  grid-template:
    'thumb title'
    'thumb time'
    'thumb desc'
    'thumb link'
    'thumb pins';
  grid-template-rows: auto auto 1fr auto;
  grid-template-columns: auto 1fr;
  height: 180px;
  column-gap: 2rem;
  padding: 2.5rem 0rem;
  /* border-bottom: 1px solid hsl(0 0% 90% / 1); */
}
.main-view {
  display: grid;
  grid-template: 'siderbar main side';
  grid-template-columns: 1fr minmax(600px, 1000px) 1fr;
  background: hsl(0 0% 97% / 1);
  margin-top: 12rem;
  width: fit-content;
  /* margin: auto; */
  margin-left: auto;
  margin-right: auto;
  z-index: 100;
  box-shadow: 0 2px 49px -30px rgba(0, 0, 0, 0.25) !important;
}
div.main {
  max-width: 1000px;
  margin: auto;
  padding: 2rem;
  box-sizing: border-box;
  line-height: 1.6;
  color: var(--txt);
  padding: 1.5rem 1.5rem 80rem 1.5rem;
  width: 100%;
  background: white;
  z-index: 100;
}
</style>
