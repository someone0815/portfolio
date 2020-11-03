<template>
  <div class="main-view">
    <div class="sider sidebar">
      <div class="holder">
        <!-- <div class="xx">
          <a class="title">ON THIS PAGE</a>
          <a
            class="listitem"
            :href="`#${stringToID(subcont.title)}`"
            v-for="subcont in toc[0].onThisPage"
            :key="subcont.title"
          >
            {{ subcont.title }}
          </a>
        </div> -->
        <div class="xx" v-for="content in toc" :key="content.title">
          <a class="listitem mainitem">{{ content.title }}</a>
          <a
            class="listitem"
            :href="`#${stringToID(subcont.title)}`"
            v-for="subcont in content.onThisPage"
            :key="subcont.title"
          >
            {{ subcont.title }}
          </a>
        </div>
      </div>
    </div>
    <div class="main">
      <section
        :id="`${stringToID(subcont.title)}`"
        v-for="subcont in toc[0].onThisPage"
        :key="subcont.title"
      >
        <h2>{{ subcont.title }}</h2>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Recusandae
        inventore architecto illo ratione aspernatur quod expedita, fugiat
        labore perferendis molestiae vitae pariatur earum culpa reprehenderit
        quis id, nulla saepe veniam suscipit! A praesentium maxime cumque
        explicabo ducimus dicta error ex soluta nemo eius esse similique est
        dolorem in ipsa laboriosam veniam ratione, numquam aperiam eligendi vero
        rerum accusamus iste porro. Aliquam, vero. Obcaecati nobis dolore optio,
        sint deleniti iusto molestiae cumque in nesciunt, adipisci vero, autem
        aut velit debitis nemo. Quo similique omnis at sit voluptas animi
        aliquid mollitia debitis repellendus iusto autem amet unde, illo illum
        ratione. Numquam, nulla?
      </section>
      <section id="Overview">
        <h2>Overview</h2>
        <ProjectCard v-for="item in 3" :key="item" />
      </section>
    </div>
    <div class="sider sideoptions">
      <div class="holder">
        <CheckboxGroup :options="filter" />
      </div>
    </div>
  </div>
</template>

<script>
import ProjectCard from './globals/ProjectCard.vue';
import CheckboxGroup from './globals/CheckboxGroup.vue';

export default {
  components: {
    ProjectCard,
    CheckboxGroup,
  },
  data: () => ({
    toc: {
      0: {
        title: 'Frontpage',
        onThisPage: [
          {
            title: 'dolorum eaque nisi',
          },
          {
            title: 'qui ducimus tempore',
          },
          {
            title: 'aperiam incidunt magni',
          },
          {
            title: 'quis quo eos incidunt',
          },
          {
            title: 'deserunt occaecati et',
          },
        ],
      },
      1: {
        title: 'Projects',
        onThisPage: [
          {
            title: 'Overview',
          },

          {
            title: 'Featured',
          },

          {
            title: 'Behance Clone',
          },
          {
            title: 'Clothing Store App',
          },
          {
            title: 'Tutoring Platform',
          },
        ],
      },
    },
    filter: {
      framework: ['Vue', 'React', 'Angular', 'Electron'],
      backend: ['nodeJS', 'Express', 'PHP', 'GraphQL'],
      database: ['MongoDB', 'MySQL', 'SQLite', 'PostgreSQL'],
      system: ['Python', 'Robotics', 'C#', 'C++'],
      general: ['Frontend', 'Backend', 'E-commerze', 'ML'],
    },
  }),
  mounted() {
    window.onscroll = this.lodash.debounce(this.scrollcalc, 5);
    this.scrollcalc();
    let anchorlinks = document.querySelectorAll('a[href^="#"]');

    for (let item of anchorlinks) {
      // relitere
      item.addEventListener('click', (e) => {
        let hashval = item.getAttribute('href');
        let target = document.querySelector(hashval);
        target.scrollIntoView({
          behavior: 'smooth',
          block: 'start',
        });
        history.pushState(null, null, hashval);
        e.preventDefault();
      });
    }
  },
  methods: {
    stringToID(string) {
      return string
        .split(' ')
        .join('-')
        .replace(/[^a-z0-9]/gi, '');
    },
    scrollcalc() {
      let mainNavLinks = document.querySelectorAll('.xx a');
      // console.log(mainNavLinks);
      let fromTop = document.documentElement.scrollTop;
      // console.log(fromTop);
      let navbarHeight = 60;

      let allFirsts = document.querySelector('.first');
      if (allFirsts != null) {
        allFirsts.classList.remove('first');
      }

      mainNavLinks.forEach((link) => {
        if (link.hash == '') return;

        let section = document.querySelector(link.hash);
        if (section == null) return;
        if (
          section.offsetTop <= fromTop + window.innerHeight &&
          section.offsetTop + section.offsetHeight > fromTop + navbarHeight
        ) {
          link.classList.add('current');
          let allCurrents = document.querySelectorAll('.current');
          allCurrents[0].classList.add('first');
        } else {
          link.classList.remove('current');
        }
      });
    },
  },
};
</script>

<style scoped>
/* Navbar */
section {
  padding: 2rem 0rem;
  /* margin-top: 60px; */
  margin-bottom: 6rem;
}
.mainitem-active {
  border-radius: 6px;
  background: hsl(220 100% 71% / 0.11);
  color: hsl(220 100% 53% / 1) !important;
  margin-bottom: 0.3rem;
}
.title {
  font-size: 12px !important;
  font-weight: 700 !important;
  cursor: default;
  margin: 0.2em 0em 1rem 0rem;
  display: block;
  text-transform: capitalize;
  color: #b2b2b2;
  text-transform: uppercase;
  letter-spacing: 0.02rem;
}

.xx {
  /* border: 1px solid #e2e2e2; */
  /* border-radius: 3px; */
  /* margin-top: 20px; */
}

.listitem:hover {
  background-color: hsla(0, 0%, 94%, 1);
}
.listitem {
  text-decoration: none;
  display: block;
  padding: 0.5rem 1.3rem;
  /* text-align: center; */
  color: gray;
  font-size: 0.95em;
  /* border-bottom: 1px solid #e2e2e2; */
  cursor: pointer;
  transition: border 0.3s, color 0.3s, padding 0.3s;
  border-left: 2px solid transparent;
  font-weight: 500;
}
.mainitem {
  padding: 0.5rem 0.5rem;
}
.current {
  /* color: #0057ff; */
  /* border-left: 4px solid hsla(220, 100%, 66%, 1); */
  border-left: 2px solid #0000003d;
  /* font-weight: 600; */
}
.first {
  color: black;
  color: #0057ff !important;
  padding-left: 1.6rem;
  font-weight: 600;
}
</style>

<style scoped>
.sidebar,
.sideoptions {
  transition: width 0.3s;
}
@media screen and (max-width: 1300px) {
  .main-view {
    grid-template: 'siderbar main main';
  }
  .sideoptions {
    display: none;
  }
}
@media screen and (max-width: 1023px) {
  .main-view {
    grid-template: 'main main main' !important;
    grid-template-columns: 1fr !important;
    width: auto !important;
  }
  .sidebar {
    display: none;
  }
}

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
/* .holder::-webkit-scrollbar-track { */
/* box-shadow: inset 0 0 5px grey; */
/* background: #f1f1f1; */
/* border-radius: 10px; */
/* } */

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
.sidebar {
  justify-self: right;
}

.link .fas {
  font-size: 0.8rem;
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
.main-view {
  display: grid;
  grid-template: 'siderbar main side';
  grid-template-columns: 1fr minmax(600px, 1000px) 1fr;
  background: hsl(0 0% 97% / 1);
  margin-top: 60vh;
  width: fit-content;
  /* margin: auto; */
  margin-left: auto;
  margin-right: auto;
  z-index: 100;
  box-shadow: 0 2px 49px -30px rgba(0, 0, 0, 0.25) !important;
}
div > .main {
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
