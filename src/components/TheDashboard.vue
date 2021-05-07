<template>
  <div>
    <b-navbar
      variant="faded"
      type="light"
    >
      <b-navbar-brand
        tag="h1"
        class="mb-0"
      >
        <b-icon
          icon="pencil-fill"
          variant="secondary"
        ></b-icon>
        Lab Website Editor
      </b-navbar-brand>
    </b-navbar>
    <b-card>
      <!-- about us -->
      <!-- <b-alert variant="danger" show>關閉/重新載入前請先按Cancel回到展示頁面</b-alert> -->
      <div class="container">
        <b-form-group>
          <h5>Homepage Image</h5>
          <b-form-file
            v-model="newHomepage"
            :state="homepageStatus"
            accept="image/*"
            placeholder="If you want to change the backgroud image."
          ></b-form-file>
        </b-form-group>
      </div>

      <div class="container">
        <b-form-group>
          <h5>About Us</h5>
          <b-form-textarea
            id="textarea"
            v-model="aboutUs"
            placeholder="Enter something..."
            rows="5"
          ></b-form-textarea>
        </b-form-group>
      </div>

      <div class="container">
        <b-form-group>
          <h5>News</h5>
          <b-card-group deck>
            <b-card>
              <div v-if=" imgSorces.length >  (currentPage-1)* 3">
                <div class="col-md-12 text-center">
                  <b-card-img
                    style="height: 27vh; width: 100%;"
                    :src="imgSorces[(currentPage-1)* 3]"
                    bottom
                  ></b-card-img>
                </div>

                <b-form-input
                  size="lg"
                  style="margin-top:20px;"
                  v-model="newsTitle[(currentPage-1)* 3]"
                ></b-form-input>

                <b-form-textarea
                  style="margin-top:30px;"
                  v-model="newsText[(currentPage-1)* 3]"
                  placeholder="edit it"
                  rows="3"
                  max-rows="6"
                  size="sm"
                ></b-form-textarea>

                <div class="col-md-12 text-center">
                  <b-button
                    style="margin-top:10px;"
                    variant="danger"
                    @click="deleteNews((currentPage-1)* 3)"
                  > Delete </b-button>
                </div>
              </div>
            </b-card>

            <b-card>
              <div v-if=" imgSorces.length >  (currentPage-1)* 3 + 1">
                <div class="col-md-12 text-center">
                  <b-card-img
                    style="height: 27vh;  width: 100%;"
                    :src="imgSorces[(currentPage-1)* 3 + 1]"
                    bottom
                  ></b-card-img>
                </div>
                <b-form-input
                  size="lg"
                  style="margin-top:20px;"
                  v-model="newsTitle[(currentPage-1)* 3 + 1]"
                ></b-form-input>

                <b-form-textarea
                  style="margin-top:30px;"
                  v-model="newsText[(currentPage-1)* 3 + 1]"
                  placeholder="edit it"
                  rows="3"
                  max-rows="6"
                  size="sm"
                ></b-form-textarea>
                <div class="col-md-12 text-center">
                  <b-button
                    style="margin-top:10px;"
                    variant="danger"
                    @click="deleteNews((currentPage-1)* 3 + 1)"
                  > Delete </b-button>
                </div>
              </div>

            </b-card>

            <b-card>
              <div v-if=" imgSorces.length >  (currentPage-1)* 3 + 2">
                <div class="col-md-12 text-center">
                  <b-card-img
                    style="height: 27vh; width: 100%;"
                    :src="imgSorces[(currentPage-1)* 3 + 2]"
                    bottom
                  ></b-card-img>
                </div>

                <b-form-input
                  style="margin-top:20px;"
                  size="lg"
                  v-model="newsTitle[(currentPage-1)* 3 + 2]"
                ></b-form-input>

                <b-form-textarea
                  style="margin-top:30px;"
                  v-model="newsText[(currentPage-1)* 3 + 2]"
                  placeholder="edit it"
                  rows="3"
                  max-rows="6"
                  size="sm"
                ></b-form-textarea>

                <div class="col-md-12 text-center">
                  <b-button
                    style="margin-top:10px;"
                    variant="danger"
                    @click="deleteNews((currentPage-1)* 3 + 2)"
                  > Delete </b-button>
                </div>
              </div>
            </b-card>
          </b-card-group>
          <div class="col-md-12 text-center">
            <b-button
              @click="onCreate"
              variant="info"
              style="margin-top:30px;"
            >Create</b-button>
          </div>
          <b-pagination
            v-model="currentPage"
            :total-rows="rows"
            :per-page="perPage"
            align="center"
            style="margin-top:30px;"
          ></b-pagination>
        </b-form-group>
      </div>
      <!-- modal -->
      <b-modal
        v-model="create"
        title="Create News"
        hide-footer
      >
        <div>
          <b-form-file
            v-model="createNewsImg"
            :state="newsImgStatus"
            :placeholder="newsImgPlacehold"
            accept="image/*"
          ></b-form-file>
          <b-form-input
            style="margin-top:30px;"
            v-model="createNewsTitle"
          ></b-form-input>
          <b-form-textarea
            style="margin-top:20px;"
            v-model="createNewsText"
            placeholder="edit it"
            rows="3"
            max-rows="6"
          ></b-form-textarea>
          <div class="col-md-12 text-center">
            <b-button
              v-if="!modalSubmitted"
              variant="info"
              style="margin-top:10px;"
              @click="submitNews"
            > Submit </b-button>
            <b-button
              v-else
              variant="info"
              style="margin-top:10px;"
              disabled
            >
              <b-spinner small></b-spinner>
            </b-button>
          </div>

        </div>
      </b-modal>
      <div class="container">
        <b-form-group>
          <h5>Members</h5>
          <b-row>
            <b-col sm="3">
              <label>Graduate Students:</label>
            </b-col>
            <b-col sm="8">
              <b-form-textarea
                v-model="graduate"
                placeholder="Enter something..."
                rows="10"
              ></b-form-textarea>
            </b-col>
          </b-row>
          <b-row>
          </b-row>
          <b-row class="mt-2">
            <b-col sm="3">
              <label>Undergraduate Students:</label>
            </b-col>
            <b-col sm="8">
              <b-form-textarea
                v-model="undergraduate"
                placeholder="Enter something..."
                rows="10"
              ></b-form-textarea>
            </b-col>
          </b-row>
        </b-form-group>
      </div>
      <div class="col-md-12 text-center">
        <b-button
          class="mr-1"
          @click="cancel"
        >Cancel</b-button>
        <b-button
          v-if="!submitted"
          class="mr-1"
          variant="primary"
          @click="onSubmit"
        >
          Submit
        </b-button>
        <b-button
          v-else
          variant="primary"
          disabled
        >
          <b-spinner small></b-spinner>
        </b-button>

      </div>
    </b-card>
  </div>
</template>

<script>
export default {
  inject: ["db", "app"],
  data() {
    return {
      modalSubmitted: false,
      submitted: false,
      newHomepage: null,

      create: false,
      createNewsTitle: null,
      createNewsImg: null,
      createNewsText: null,
      allCreateFile: [],

      newsText: [],
      newsTitle: [],
      imgSorces: [],
      newsFileName: [],
      beDeleted: [],

      rows: 0,
      perPage: 3,
      currentPage: 1,

      change: false,
      originIndex: null,
      targetIndex: null,
      options: [],

      aboutUs: "",
      graduate: "",
      undergraduate: "",
    };
  },
  computed: {
    homepageStatus() {
      if (this.newHomepage) {
        return true;
      } else {
        return null;
      }
    },
    newsImgStatus() {
      if (this.createNewsImg) {
        return true;
      } else {
        return null;
      }
    },
    newsImgPlacehold() {
      if (this.createNewsImg) {
        return this.createNewsImg.name;
      } else {
        return "No file chosen...";
      }
    },
  },
  mounted: function () {
    document.scrollingElement.scrollTop = 0;
    this.db
      .ref("/news/")
      .once("value")
      .then((result) => {
        for (const name in result.val()) {
          this.imgSorces.push(result.val()[name].url);
          this.newsText.push(result.val()[name].context);
          this.newsTitle.push(result.val()[name].title);
          this.newsFileName.push(result.val()[name].file_name);
          this.rows = this.imgSorces.length;
        }
      });
    this.db
      .ref("/about_us/main")
      .once("value")
      .then((result) => {
        for (const name in result.val()) {
          this.aboutUs = result.val()[name];
        }
      });
    this.db
      .ref("/members/graduate")
      .once("value")
      .then((result) => {
        for (const name in result.val()) {
          this.graduate = result.val()[name];
        }
      });
    this.db
      .ref("/members/undergraduate")
      .once("value")
      .then((result) => {
        for (const name in result.val()) {
          this.undergraduate = result.val()[name];
        }
      });
  },
  methods: {
    cancel() {
      for (let i = 0; i < this.allCreateFile.length; i++) {
        let storageRef = this.app.storage().ref(this.allCreateFile[i] + ".jpg");
        storageRef.delete();

        this.db.ref("/create/" + this.allCreateFile[i]).remove();
      }
      let previousCreate = [];
      this.db
        .ref("/create/")
        .once("value")
        // 先讀create
        .then((result) => {
          for (const name in result.val()) {
            console.log(result.val()[name].file_name);
            previousCreate.push(result.val()[name].file_name);
          }
        })
        // 根據create去比對最新news 刪掉多餘的
        .then(() => {
          this.db.ref("/create/").remove();
          for (let i = 0; i < previousCreate.length; i++) {
            if (this.newsFileName.includes(previousCreate[i]) === false) {
              let storageRef = this.app
                .storage()
                .ref(previousCreate[i] + ".jpg");
              console.log(previousCreate[i] + ".jpg");
              storageRef.delete();
            }
          }
          this.$emit("editDone");
        });
    },
    onCreate() {
      this.create = true;
    },
    submitNews() {
      // 每次create就做紀錄 submit的時候只要create的file 不在紀錄裡面就刪掉
      if (
        this.createNewsText !== null &&
        this.createNewsImg != null &&
        this.createNewsTitle != null
      ) {
        this.modalSubmitted = true;
        let aNow = new Date();
        let storageRef = this.app
          .storage()
          .ref(String(aNow.getTime()) + ".jpg");
        storageRef.put(this.createNewsImg).then((snapshot) => {
          snapshot.ref.getDownloadURL().then((url) => {
            this.imgSorces.unshift(url);
            this.newsTitle.unshift(this.createNewsTitle);
            this.newsText.unshift(this.createNewsText);
            this.newsFileName.unshift(String(aNow.getTime()));
            this.allCreateFile.push(String(aNow.getTime()));
            // 紀錄
            this.db
              .ref("/create/")
              .child(String(aNow.getTime()))
              .set({
                file_name: String(aNow.getTime()),
              });

            this.createNewsTitle = null;
            this.createNewsText = null;
            this.createNewsImg = null;
            this.rows += 1;
            this.create = false;
            this.modalSubmitted = false;
          });
        });
      }
    },

    onSubmit() {
      this.submitted = true;
      this.db.ref("/members/").child("graduate").set({
        context: this.graduate,
      });
      this.db.ref("/members/").child("undergraduate").set({
        context: this.undergraduate,
      });
      this.db.ref("/about_us/").child("main").set({
        context: this.aboutUs,
      });
      // 先更新news
      this.db.ref("/news/").remove();
      for (let i = 0; i < this.imgSorces.length; i++) {
        this.db.ref("/news/").child(String(i)).set({
          title: this.newsTitle[i],
          file_name: this.newsFileName[i],
          context: this.newsText[i],
          url: this.imgSorces[i],
        });
      }
      // 被刪除的資料在submit的時候真正刪掉
      for (let i = 0; i < this.beDeleted.length; i++) {
        let storageRef = this.app.storage().ref(this.beDeleted[i] + ".jpg");
        storageRef.delete();
      }

      // 避免重新整理跟用到一半被關閉 導致資料庫有一堆沒用到的資料
      let previousCreate = [];
      this.db
        .ref("/create/")
        .once("value")
        // 先讀create
        .then((result) => {
          for (const name in result.val()) {
            console.log(result.val()[name].file_name);
            previousCreate.push(result.val()[name].file_name);
          }
        })
        // 根據create去比對最新news 刪掉多餘的
        .then(() => {
          this.db.ref("/create/").remove();
          for (let i = 0; i < previousCreate.length; i++) {
            if (this.newsFileName.includes(previousCreate[i]) === false) {
              let storageRef = this.app
                .storage()
                .ref(previousCreate[i] + ".jpg");
              console.log(previousCreate[i] + ".jpg");
              storageRef.delete();
            }
          }
        });

      if (this.newHomepage) {
        let storageRef = this.app.storage().ref("homepage.jpg");
        storageRef.put(this.newHomepage).then((snapshot) => {
          snapshot.ref.getDownloadURL().then((url) => {
            this.db.ref("/homepage/").child("img").set({
              url: url,
            });
            this.$emit("editDone");
          });
        });
      } else {
        this.submitted = true;
        this.$emit("editDone");
      }
    },
    deleteNews(index) {
      this.newsTitle.splice(index, 1);
      this.newsText.splice(index, 1);
      this.imgSorces.splice(index, 1);
      this.beDeleted.push(this.newsFileName[index]);
      this.newsFileName.splice(index, 1);
      this.rows -= 1;
    },
  },
};
</script>