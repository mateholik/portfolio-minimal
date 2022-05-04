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
          <div class="me">
            <img src="./assets/me.jpeg" alt="me" />
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
                v-for="img in activeItem.imgs"
                :key="img.thumb"
                class="img-wrapper"
                :href="imageModule(img.full)"
                target="_blank"
              >
                <img :alt="activeItem.title" :src="imageModule(img.thumb)" />
                <p>{{ img.name }}</p>
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
            {
              name: "",
              thumb: "/adrenaline/thumbs/1-thumb.jpg",
              full: "/adrenaline/1.jpg",
            },
            {
              name: "",
              thumb: "/adrenaline/thumbs/4-thumb.jpeg",
              full: "/adrenaline/4.jpg",
            },
            {
              name: "",
              thumb: "/adrenaline/thumbs/5-thumb.jpeg",
              full: "/adrenaline/5.jpg",
            },
            {
              name: "",
              thumb: "/adrenaline/thumbs/6-thumb.jpeg",
              full: "/adrenaline/6.jpg",
            },
            {
              name: "",
              thumb: "/adrenaline/thumbs/7-thumb.jpeg",
              full: "/adrenaline/7.jpg",
            },
            {
              name: "",
              thumb: "/adrenaline/thumbs/8-thumb.jpeg",
              full: "/adrenaline/8.jpg",
            },
            {
              name: "",
              thumb: "/adrenaline/thumbs/9-thumb.jpeg",
              full: "/adrenaline/9.jpg",
            },
            {
              name: "",
              thumb: "/adrenaline/thumbs/10-thumb.jpeg",
              full: "/adrenaline/10.jpg",
            },
          ],
        },
        {
          title: "Culture Night 2020",
          description:
            '"Naktinės veiklos"<br><br>Naktinės akistatos su savimi<br>Naktinis narcizų žydėjimas<br>Naktinis Tengo laukimas<br>Naktinės maudynės<br>Naktinis pomidorų augimas',
          imgs: [
            {
              name: "Driving to heaven, 2020",
              thumb: "/culture-night-2020/thumbs/1-thumb.jpg",
              full: "/culture-night-2020/1.jpg",
            },
            {
              name: "",
              thumb: "/culture-night-2020/thumbs/2-thumb.jpg",
              full: "/culture-night-2020/2.jpg",
            },
            {
              name: "Pomidorai, 2020",
              thumb: "/culture-night-2020/thumbs/3-thumb.jpg",
              full: "/culture-night-2020/3.jpg",
            },
            {
              name: "Narcizai, 2020",
              thumb: "/culture-night-2020/thumbs/4-thumb.jpg",
              full: "/culture-night-2020/4.jpg",
            },
            {
              name: "Besimaudantys, 2020",
              thumb: "/culture-night-2020/thumbs/5-thumb.jpg",
              full: "/culture-night-2020/5.jpg",
            },
            {
              name: "Kur tu, Tengo? 2020",
              thumb: "/culture-night-2020/thumbs/6-thumb.jpg",
              full: "/culture-night-2020/6.jpg",
            },
            {
              name: "Mauduoliai, 2020",
              thumb: "/culture-night-2020/thumbs/7-thumb.jpg",
              full: "/culture-night-2020/7.jpg",
            },
          ],
        },
        {
          title: "Art without roof",
          imgs: [
            {
              name: "Autoportretas, 2004",
              thumb: "/art-without-roof/thumbs/1-thumb.jpeg",
              full: "/art-without-roof/1.jpeg",
            },
          ],
        },
        {
          title: "Coca Art",
          description:
            " <a href='https://cocaproject.art/artists/lina-audronyte-vladimirova-coca20/' target='_blank'>https://cocaproject.art/artists/lina-audronyte-vladimirova-coca20/</a>",
          imgs: [
            {
              name: "Bare, 2020",
              thumb: "/coca-art/thumbs/1-thumb.jpg",
              full: "/coca-art/1.jpg",
            },
            {
              name: "Studenčių vakaras Antakalnyje, 2013",
              thumb: "/coca-art/thumbs/2-thumb.jpeg",
              full: "/coca-art/2.jpg",
            },
            {
              name: "Kur tu, Tengo? 2020",
              thumb: "/coca-art/thumbs/3-thumb.jpg",
              full: "/coca-art/3.jpg",
            },
          ],
        },
        {
          title: "Šeškinė",
          imgs: [
            {
              name: "Čiuožykla, 2020",
              thumb: "/seskine/thumbs/1-thumb.jpg",
              full: "/seskine/1.jpeg",
            },
            {
              name: "Šeškinė, 2021",
              thumb: "/seskine/thumbs/2-thumb.jpg",
              full: "/seskine/2.jpeg",
            },
            {
              name: "Sūpuoklės, 2020",
              thumb: "/seskine/thumbs/3-thumb.jpg",
              full: "/seskine/3.jpeg",
            },
          ],
        },
      ],
      activeItem: "",
    };
  },
  watch: {
    activeItem() {
      if (window.innerWidth < 769) {
        let y =
          this.$refs.article.getBoundingClientRect().top +
          window.pageYOffset -
          20;

        window.scrollTo({ top: y, behavior: "smooth" });
      }
    },
  },
  mounted() {
    this.activeItem = this.projects[0];
    this.imagesModules = import.meta.globEager("./assets/**");
  },
  methods: {
    imageModule(path) {
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
a {
  text-decoration: none;
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
    &:hover {
      color: #039a7f;
    }
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
    &:hover {
      color: #039a7f;
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
      margin-bottom: 24px;
      h4 {
        font-size: 22px;
        font-weight: 500;
        margin-bottom: 16px;
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
    .me {
      max-width: 300px;
      img {
        width: 100%;
        height: auto;
        display: block;
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
      p {
        margin-top: 10px;
        color: #222;
        font-weight: 500;
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
