<template>
  <header>
    <div class="container">
      <span>Lina Audronytė</span>
      <a href="mailto:lina.audronyte@gmail.com">
        <img src="./assets/mail.svg" alt="email" />
        lina.audronyte@gmail.com
      </a>
    </div>
  </header>
  <main>
    <div class="container">
      <nav>
        <span
          @click="activeItem = 'about'"
          class="parent"
          :class="{ active: activeItem === 'about' }"
          >About</span
        >
        <div class="projects">
          <span class="parent" @click="activeItem = projects[0]"
            >Projects:</span
          >
          <ul>
            <li
              v-for="project in projects"
              :key="project.title"
              @click="activeItem = project"
              :class="{ active: activeItem === project }"
            >
              {{ project.title }}
            </li>
          </ul>
        </div>
      </nav>
      <article ref="article">
        <div v-if="activeItem === 'about'" class="about">
          <div class="block">
            <h4>Education:</h4>
            <ul>
              <li>2011 - Graduated Vilnius Art Academy, painting</li>
              <li>2011-2012 - "Fluxus ministerija" resident</li>
              <li>
                2020 - participant in projects "Art without roof", COCA art
              </li>
            </ul>
          </div>
          <div class="block">
            <h4>Exhibitions:</h4>
            <ul>
              <li>
                2006 - ANTIPOPS alternative art and music festival, painting,
                Kaunas
              </li>
              <li>
                2020 - "Culture Night 2020" participant, solo exhibition in
                Ramintoja church, Vilnius
              </li>
            </ul>
          </div>
        </div>
        <div v-else>
          <div class="block">
            <h4>{{ activeItem.title }}</h4>
            <div
              v-if="activeItem.description"
              v-html="activeItem.description"
            ></div>
            <div class="images">
              <a
                v-for="imgPath in activeItem.imgs"
                :key="imgPath"
                class="img-wrapper"
                :href="imageSrc(imgPath)"
                target="_blank"
              >
                <img :alt="activeItem.title" :src="imageSrc(imgPath)" />
              </a>
            </div>
          </div>
        </div>
      </article>
    </div>
  </main>
</template>

<script>
export default {
  data() {
    return {
      imagesModules: {},
      projects: [
        {
          title: "Primavera Adrenaline",
          description:
            "Jausmas, šokant parašiutu?<br>Tai nėra kritimo jausmas, greičiau - skrydžio.<br>Daug vėjo, garso. Labai intensyvus jausmas. <br>Adrenalinas pulsuoja ir visi pojūčiai maksimaliai aštrūs.<br><br>Šis pavasaris atrodė, niekada neateis. Prasidėjo karas Ukrainoje.<br>Tačiau gamta išsiveržė visomis ryškiomis spalvomis ir nauja gyvybe.<br>Fone pajuodusių nuo bombų pastatų, išdygusios raudonos tulpės, išsprogę beržų lapeliai atrodo siurrealistiškai.<br>Žmonės, bėgantys nuo karo, taip apibūdino savo būseną: - Jaučiausi taip, lyg būčiau gavusi švirkštą adrenalino tiesiai į smegenis, todėl labai gerai suvokiau esamą akimirką ir buvau pasiruošusi bet kurią sekundę pulti. (Katerina Kovalenko).<br><br>Kaštonas savo didžiuliais lapais ir baltomis žiedų žvakėmis įkūnija pavasario gaivalą. Praeitą pavasarį mane aplankė vizija - parašiutininkas neria į žydinčius kaštonus. 2022 m pavasario įvykiai sukrėtė apsnūdusią Europą ir privertė plačiai atmerkti akis.",
          imgs: [
            "/adrenaline/1.jpg",
            "/adrenaline/2.jpg",
            "/adrenaline/3.jpg",
            "/adrenaline/4.jpg",
            "/adrenaline/5.jpg",
            "/adrenaline/6.jpg",
            "/adrenaline/7.jpg",
            "/adrenaline/8.jpeg",
            "/adrenaline/9.jpeg",
            "/adrenaline/10.jpeg",
          ],
        },
        {
          title: "Culture Night 2020",
          description:
            '"Naktinės veiklos"<br><br>Naktinės akistatos su savimi<br>Naktinis narcizų žydėjimas<br>Naktinis Tengo laukimas<br>Naktinės maudynės<br>Naktinis pomidorų augimas',
          imgs: [
            "/culture-night-2020/1.jpg",
            "/culture-night-2020/2.jpg",
            "/culture-night-2020/3.jpg",
            "/culture-night-2020/4.jpg",
            "/culture-night-2020/5.jpg",
            "/culture-night-2020/6.jpg",
            "/culture-night-2020/7.jpg",
          ],
        },
        {
          title: "Art without roof",
          imgs: ["/art-without-roof/1.jpeg"],
        },
        {
          title: "Coca Art",
          imgs: ["/seskine/1.jpeg", "/seskine/2.jpeg", "/seskine/3.jpeg"],
        },
        {
          title: "Šeškinė",
          imgs: ["/coca-art/1.jpg", "/coca-art/2.jpg", "/coca-art/3.jpg"],
        },
      ],
      activeItem: "",
    };
  },
  // watch: {
  //   activeItem() {
  //     if (window.innerWidth < 769)
  //       this.$refs.article.scrollIntoView({
  //         behavior: "smooth",
  //         top: -100,
  //       });
  //   },
  // },
  mounted() {
    this.activeItem = this.projects[0];
    this.imagesModules = import.meta.globEager("./assets/**");
  },
  methods: {
    imageSrc(path) {
      const fullPath = "./assets" + path;
      return this.imagesModules[fullPath].default;
    },
  },
};
</script>

<style lang="scss">
body {
  margin: 0;
  padding: 0;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-rendering: optimizeLegibility;
  color: 222;
  font-family: "Roboto", sans-serif;
}
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 16px;
}
header {
  padding: 60px 0;
  @media (max-width: 768px) {
    padding: 24px 0 32px;
  }
  .container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    @media (max-width: 768px) {
      flex-direction: column-reverse;
      align-items: flex-start;
    }
  }
  span {
    font-weight: 500;
    font-size: 22px;
    letter-spacing: 4px;
  }
  a {
    display: flex;
    align-items: center;
    font-weight: 500;
    font-size: 20px;
    color: #039a7f;
    text-decoration: none;
    @media (max-width: 768px) {
      margin-bottom: 32px;
    }
    img {
      margin-right: 8px;
    }
  }
}
nav {
  width: 290px;

  border-right: 1px solid #b3b3b3;
  margin-right: 5%;
  flex-shrink: 0;
  @media (max-width: 768px) {
    width: 100%;
    border-right: none;
    border-bottom: 1px solid #b3b3b3;
    margin-right: 0;
    margin-bottom: 24px;
    padding-bottom: 24px;
  }
  .parent {
    display: block;
    font-weight: 500;
    font-size: 20px;
    margin-bottom: 24px;
    cursor: pointer;
    transition: 0.2s;
  }
  li {
    list-style: none;
    font-weight: 500;
    font-size: 20px;
    margin-bottom: 16px;
    cursor: pointer;
    transition: 0.2s;
    margin-left: 32px;
    &:last-of-type {
      margin-bottom: 0;
    }
  }
  .active {
    color: #039a7f;
  }
}
main {
  .container {
    display: flex;
    @media (max-width: 768px) {
      display: block;
    }
  }
  article {
    height: calc(100vh - 145px);
    overflow-y: auto;
    width: 100%;
    padding-right: 40px;
    padding-bottom: 40px;
    box-sizing: border-box;
    @media (max-width: 768px) {
      height: auto;
      overflow-y: auto;
      padding-right: 0;
    }
    .block {
      h4 {
        font-size: 22px;
        font-weight: 500;
        margin-bottom: 16px;
      }
      ul {
      }
      li {
        font-size: 18px;
        list-style: none;
        margin-bottom: 16px;
      }
      div {
        line-height: 1.5;
      }
    }
    .images {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      grid-gap: 40px;
      margin-top: 40px;
      @media (max-width: 768px) {
        height: auto;
        grid-template-columns: repeat(1, 1fr);
        grid-gap: 32px;
      }
      .img-wrapper {
        width: 100%;
      }
      img {
        display: block;
        width: 100%;
        height: auto;
      }
    }
  }
}

/* width */
::-webkit-scrollbar {
  width: 5px;
}

/* Track */
::-webkit-scrollbar-track {
  box-shadow: inset 0 0 5px grey;
  border-radius: 10px;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: grey;
  border-radius: 10px;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #b30000;
}
</style>
