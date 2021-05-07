<template>
  <body data-spy="scroll" data-target="#rock-navigation">
    <the-dashboard v-if="login === true" @editDone="editDone"> </the-dashboard>

    <div v-else>
      <div
        class="templatemo-home"
        :style="{ backgroundImage: 'url(' + homepageImg + ')' }"
      ></div>
      <div class="title_name">
        <h1 style="font-size: 50px; font-weight: bold">
          Artificial Intelligence<br />Laboratory
        </h1>
        <p style="font-size: 20px">Chia-Yu Lin, Ph.D.</p>
      </div>

      <section id="work" style="padding-top: 100px; padding-bottom: 100px">
        <div class="container">
          <div>
            <h2 class="title"><strong>About Us</strong></h2>
          </div>
          <b-card>
            <b-card-text style="white-space: pre-line">
              {{ aboutUs }}
            </b-card-text>
          </b-card>
        </div>
      </section>

      <section id="work" style="padding-top: 0px; padding-bottom: 100px">
        <div class="container">
          <div class="row">
            <div class="col-md-offset-1 col-md-11">
              <h2 class="title"><strong>Research Areas</strong></h2>
            </div>
            <div class="col-md-4 col-sm-4">
              <div class="work-wrapper">
                <i class="fa fa-link"></i>
                <h3 class="tm-work-h3">Artificial Intelligence</h3>
                <hr />
                <img height="70px" src="./ai.png" alt="" />
              </div>
            </div>
            <div class="col-md-4 col-sm-4">
              <div class="work-wrapper">
                <i class="fa fa-flash"></i>
                <h3 class="tm-work-h3">Smart Manufacturing</h3>
                <hr />
                <img height="70px" src="./factory.png" alt="" />
              </div>
            </div>
            <div class="col-md-4 col-sm-4">
              <div class="work-wrapper">
                <i class="fa fa-dashboard"></i>
                <h3 class="tm-work-h3">Streaming Data Analysis</h3>
                <hr />
                <img height="70px" src="./data.png" alt="" />
              </div>
            </div>
          </div>
        </div>
      </section>
      <section style="padding-top: 0px; padding-bottom: 100px">
        <div class="container">
          <div>
            <h2 class="title"><strong>News</strong></h2>
          </div>

          <b-card-group deck>
            <b-card>
              <div v-if="imgSorces.length > (currentPage - 1) * 3">
                <b-card-img
                  style="height: 27vh; width: 100%"
                  :src="imgSorces[(currentPage - 1) * 3]"
                  bottom
                ></b-card-img>
                <b-card-title
                  style="margin-top: 20px; text-align: center; font-size: 22px"
                  >{{ newsTitle[(currentPage - 1) * 3] }}</b-card-title
                >
                <b-card-text style="white-space: pre-line; font-size: 15.5px">{{
                  newsText[(currentPage - 1) * 3]
                }}</b-card-text>
              </div>
            </b-card>

            <b-card>
              <div v-if="imgSorces.length > (currentPage - 1) * 3 + 1">
                <b-card-img
                  style="height: 27vh; width: 100%"
                  :src="imgSorces[(currentPage - 1) * 3 + 1]"
                  bottom
                ></b-card-img>
                <b-card-title
                  style="margin-top: 20px; text-align: center; font-size: 22px"
                  >{{ newsTitle[(currentPage - 1) * 3 + 1] }}</b-card-title
                >
                <b-card-text style="white-space: pre-line; font-size: 15.5px">{{
                  newsText[(currentPage - 1) * 3 + 1]
                }}</b-card-text>
              </div>
            </b-card>

            <b-card>
              <div v-if="imgSorces.length > (currentPage - 1) * 3 + 2">
                <b-card-img
                  style="height: 27vh; width: 100%"
                  :src="imgSorces[(currentPage - 1) * 3 + 2]"
                  bottom
                ></b-card-img>
                <b-card-title
                  style="margin-top: 20px; text-align: center; font-size: 22px"
                  >{{ newsTitle[(currentPage - 1) * 3 + 2] }}</b-card-title
                >
                <b-card-text style="white-space: pre-line; font-size: 15.5px">{{
                  newsText[(currentPage - 1) * 3 + 2]
                }}</b-card-text>
              </div>
            </b-card>
          </b-card-group>

          <b-pagination
            v-model="currentPage"
            :total-rows="rows"
            :per-page="perPage"
            align="center"
            style="margin-top: 30px"
          ></b-pagination>
        </div>
      </section>

      <section id="resume" style="padding-top: 0px; padding-bottom: 100px">
        <div class="container">
          <div>
            <h2 class="title"><strong>Members</strong></h2>
          </div>
          <b-card no-body class="mb-1">
            <b-card-header header-tag="header" class="p-1" role="tab">
              <b-button block v-b-toggle.accordion-1 variant="info"
                >Thesis Advisor</b-button
              >
            </b-card-header>
            <b-collapse
              id="accordion-1"
              visible
              accordion="my-accordion"
              role="tabpanel"
            >
              <b-card-body>
                <div class="col-md-12 text-center">
                  <b-img
                    thumbnail
                    style="max-width: 20%"
                    img-left
                    fluid
                    src="https://firebasestorage.googleapis.com/v0/b/sallylab-official.appspot.com/o/%E8%80%81%E5%B8%AB%E7%85%A7%E7%89%87.jpeg?alt=media&token=4296f010-3177-496f-b3f0-933081dc9ce2"
                    alt="Image 1"
                  ></b-img>
                </div>
                <div class="col-md-12 text-center">
                  <b-card-text
                    >林家瑜博士<br />Chia-Yu Lin, Ph.D.<br />Email :
                    <a
                      rel="nofollow noopener"
                      href="mailto: sallylin0121@saturn.yzu.edu.tw"
                      >sallylin0121@saturn.yzu.edu.tw</a
                    ></b-card-text
                  >
                </div>
              </b-card-body>
            </b-collapse>
          </b-card>

          <b-card no-body class="mb-1">
            <b-card-header header-tag="header" class="p-1" role="tab">
              <b-button block v-b-toggle.accordion-2 variant="info"
                >Graduate Students</b-button
              >
            </b-card-header>
            <b-collapse
              id="accordion-2"
              accordion="my-accordion"
              role="tabpanel"
            >
              <b-card-body body-class="text-center">
                <b-card-text v-for="line in graduate" :key="line">
                  <b-icon icon="dot"></b-icon>
                  {{ line }}
                </b-card-text>
              </b-card-body>
            </b-collapse>
          </b-card>

          <b-card no-body class="mb-1">
            <b-card-header header-tag="header" class="p-1" role="tab">
              <b-button block v-b-toggle.accordion-3 variant="info"
                >Undergraduate Students</b-button
              >
            </b-card-header>
            <b-collapse
              id="accordion-3"
              accordion="my-accordion"
              role="tabpanel"
            >
              <b-card-body body-class="text-center">
                <b-card-text v-for="line in undergraduate" :key="line">
                  <b-icon icon="dot"></b-icon>
                  {{ line }}
                </b-card-text>
              </b-card-body>
            </b-collapse>
          </b-card>
        </div>
      </section>

      <section id="contact" class="tm-contact">
        <div class="container">
          <b-card>
            <b-card-title> </b-card-title>
            <b-card-title> Lab Operation </b-card-title>

            <b-card-body>
              <b-card-text> 1. Group meeting once a week. </b-card-text>
              <b-card-text> 2. Individual meeting once a week. </b-card-text>
            </b-card-body>
          </b-card>
          <div style="margin-top: 40px">
            <p>
              Made By
              <a rel="nofollow noopener" href="mailto: steven123890@gmail.com"
                >Sheng-Che Lin</a
              >
            </p>
            <b-button @click="edit = !edit" variant="outline-light">
              Edit
            </b-button>
          </div>
        </div>
      </section>
    </div>

    <b-modal v-model="edit" title="Lab Website Editor" hide-footer>
      <div role="group">
        <label>Password:</label>
        <b-form-input id="input-live" v-model="password"></b-form-input>
      </div>

      <div class="col-md-12 text-center">
        <b-button
          variant="info"
          style="margin-top: 10px"
          @click="enterPassword"
        >
          Login
        </b-button>
      </div>
    </b-modal>
  </body>
</template>

<script>
import TheDashboard from "./components/TheDashboard.vue";

import Firebase from "firebase";
let config = {
  apiKey: "AIzaSyAK9MNzqi3KEZmrTebQtD8-nuZ0D6hhXxU",
  authDomain: "sallylab-official.firebaseapp.com",
  databaseURL: "https://sallylab-official-default-rtdb.firebaseio.com",
  projectId: "sallylab-official",
  storageBucket: "sallylab-official.appspot.com",
  messagingSenderId: "138329708436",
  appId: "1:138329708436:web:ae5cc14920e0d3ccf8a181",
};

let app = Firebase.initializeApp(config);
let db = app.database();
export default {
  components: { TheDashboard },
  provide() {
    return {
      app: app,
      db: app.database(),
    };
  },
  data() {
    return {
      login: false,
      password: null,

      homepageImg: null,
      newsText: [],
      newsTitle: [],
      imgSorces: [],
      edit: false,
      currentPage: 1,
      rows: null,
      perPage: 3,
      aboutUs: "",
      graduate: null,
      undergraduate: null,
    };
  },
  methods: {
    enterPassword() {
      if (this.password == "sallylin0121") {
        this.login = true;
        this.edit = false;
      }
    },
    editDone() {
      document.scrollingElement.scrollTop = 0;
      this.imgSorces = [];
      this.newsTitle = [];
      this.newsText = [];
      this.rows = 0;
      db.ref("/news/")
        .once("value")
        .then((result) => {
          for (const name in result.val()) {
            this.imgSorces.push(result.val()[name].url);
            this.newsTitle.push(result.val()[name].title);
            this.newsText.push(result.val()[name].context);
            this.rows = this.imgSorces.length;
          }
        });
      db.ref("/about_us/main")
        .once("value")
        .then((result) => {
          for (const name in result.val()) {
            this.aboutUs = result.val()[name];
          }
        });
      db.ref("/members/graduate")
        .once("value")
        .then((result) => {
          for (const name in result.val()) {
            this.graduate = result.val()[name];
          }
          this.graduate = this.graduate.split("\n");
        });
      db.ref("/members/undergraduate")
        .once("value")
        .then((result) => {
          for (const name in result.val()) {
            this.undergraduate = result.val()[name];
          }
          this.undergraduate = this.undergraduate.split("\n");
        });
      db.ref("/homepage/img")
        .once("value")
        .then((result) => {
          for (const name in result.val()) {
            this.homepageImg = result.val()[name];
            console.log(this.homepageImg);
          }
        });
      this.edit = false;
      this.login = false;
      this.password = null;
    },
  },
  mounted: function () {
    db.ref("/about_us/main")
      .once("value")
      .then((result) => {
        for (const name in result.val()) {
          this.aboutUs = result.val()[name];
        }
      });
    db.ref("/members/graduate")
      .once("value")
      .then((result) => {
        for (const name in result.val()) {
          this.graduate = result.val()[name];
        }
        this.graduate = this.graduate.split("\n");
        // this.graduate.pop();
      });
    db.ref("/members/undergraduate")
      .once("value")
      .then((result) => {
        for (const name in result.val()) {
          this.undergraduate = result.val()[name];
        }
        this.undergraduate = this.undergraduate.split("\n");
      });
    db.ref("/news/")
      .once("value")
      .then((result) => {
        for (const name in result.val()) {
          this.imgSorces.push(result.val()[name].url);
          this.newsTitle.push(result.val()[name].title);
          this.newsText.push(result.val()[name].context);
          this.rows = this.imgSorces.length;
        }
      });
    db.ref("/homepage/img")
      .once("value")
      .then((result) => {
        for (const name in result.val()) {
          this.homepageImg = result.val()[name];
        }
      });
  },
};
</script>
<style scoped>
.title_name {
  /* height: 30vh; */
  position: absolute;
  top: 12%;
  left: 50%;
  background-color: rgb(0, 0, 0);
  background-color: rgba(0, 0, 0, 0.4);
  color: white;
  font-weight: bold;
  font-weight: bold;
  border: 3px solid #f1f1f1;
  transform: translate(-50%, -50%);
  z-index: 2;
  /* width: 50%; */
  padding-top: 5vh;
  padding-bottom: 3vh;
  padding-left: 6%;
  padding-right: 6%;
  text-align: center;
}

.nobull {
  list-style-type: none;
}

body {
  background: #ffffff;
  font-family: "Raleway", sans-serif;
  font-size: 16px;
  color: #606060;
  position: relative;
}
html,
body {
  width: 100%;
  overflow-x: hidden;
}

.templatemo-home {
  background-size: cover;
  /* filter: blur(2px);
  -webkit-filter: blur(2px); */
  background-attachment: fixed;
  background-position: center center;
  color: #5f5f5f;
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-align: center;
  -webkit-align-items: center;
  -ms-flex-align: center;
  align-items: center;
  text-align: center;
  height: 100vh;
}
/* h1,
h2,
h3 {
  font-weight: 300;
} */

p {
  line-height: 32px;
}
hr {
  border-color: #f2f2f2;
  width: 100px;
  margin-bottom: 40px;
}
.title {
  color: #303030;
  font-size: 50px;
  font-weight: bold;
  padding-bottom: 40px;
}

/* START WORK */
.tm-padding-top-bottom-100 {
  padding-top: 100px;
  padding-bottom: 100px;
}
.tm-work-h3 {
  color: #eb5424;
  font-size: 20px;
  font-weight: bold;
  letter-spacing: 1px;
  padding-bottom: 10px;
}
.work-wrapper {
  border: 2px solid #666;
  border-radius: 2px;
  text-align: center;
  padding: 80px 40px 80px 40px;
  -webkit-transition: all 0.1s ease-in;
  transition: all 0.1s ease-in;
}
.work-wrapper:hover {
  border-color: #eb5424;
}
.work-wrapper .fa {
  color: #888888;
  font-size: 60px;
  padding-bottom: 40px;
}
/* END WORK */

.tm-contact {
  text-align: center;
  padding-top: 0px;
  padding-bottom: 40px;
}
</style>