<template>
  <section
    id="services"
    :class="$vuetify.rtl ? 'ar-service-one' : 'en-service-one'"
    class=" service-one py-10 "
  >
    <!-- <v-img
      style="position: absolute;
    margin-top: -71px;
        opacity: 0.5;
    right: 0px;"
      max-height="400px"
      max-width="100px"
      src="aii.png"
      eager
    >
    </v-img> -->
    <v-img
      style=" margin-top:-300px; opacity: 0.3; position: absolute;  right:0px"
      src="left-01.png"
      width="100px"
      eager
    ></v-img>
    <v-img
      style=" margin-top:400px; opacity: 0.3; position: absolute;  left:0px"
      src="right-01.png"
      width="100px"
      eager
    ></v-img>
    <div class="container">
      <div class="block-title mx-8 ">
        <h3
          v-animate-onscroll="{ down: 'animated pulse' }"
          class="text-h4 mb-5 font-weight-black"
        >
          {{ arabicinfo.service.title }}
        </h3>
        <h1 class="text-subtitle-1">
          {{ arabicinfo.service.description }}
        </h1>
      </div>
      <!-- /.block-title -->
      <div
        v-animate-onscroll="{ down: 'animated fadeInUp' }"
        class="row"
        style="justify-content: center;"
      >
        <div
          class="col-md-6 col-sm-10 col-lg-3"
          v-for="item in arabicinfo.service.mores"
          :key="item.name"
        >
          <div class="service-one__box ">
            <div class="service-one__icon red">
              <div
                :class="
                  $vuetify.theme.dark
                    ? 'service-one__icon-inner service-one__dark '
                    : 'service-one__icon-inner'
                "
              >
                <v-icon size="50px">
                  {{ item.icon }}
                </v-icon>
              </div>
              <!-- /.service-one__icon-inner -->
            </div>
            <!-- /.service-one__icon -->
            <h3>
              {{ item.name }}
            </h3>
            <p class="text-justify">
              {{ item.details }}
            </p>
          </div>
          <!-- /.service-one__box -->
        </div>

        <!-- /.col-md-6 col-lg-3 -->
      </div>
      <!-- /.row -->
    </div>
    <!-- /.container -->
  </section>
</template>

<script>
import { mapState } from "vuex";

export default {
  computed: {
    ...mapState(["arabic", "english"]),
    arabicinfo() {
      if (this.$vuetify.rtl) {
        return this.arabic;
      } else {
        return this.english;
      }
    }
  }
};
</script>

<style scoped>
/*--------------------------------------------------------------
# Services
--------------------------------------------------------------*/
.service-one {
  position: relative;
}

/* .service-one .container {
  position: relative;
} */

.service-one__shape-1 {
  bottom: 65%;
  left: 95%;
  -webkit-animation-name: shapeMover;
  animation-name: shapeMover;
  -webkit-animation-duration: 9s;
  animation-duration: 9s;
  -webkit-animation-timing-function: linear;
  animation-timing-function: linear;
  -webkit-animation-iteration-count: infinite;
  animation-iteration-count: infinite;
}

.service-one .block-title {
  margin-bottom: 60px;
  text-align: center;
}

.service-one .block-title p {
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  justify-content: center;
}

.ar-service-one [class*="col-"]:not(:last-of-type) {
  position: relative;
}

.ar-service-one [class*="col-"]:not(:last-of-type)::before {
  content: "";
  width: 1px;
  height: 230px;
  background-color: #e4e4e4;
  position: absolute;
  top: 50%;
  left: 0;
  -webkit-transform: translateY(-50%);
  transform: translateY(-50%);
}
.en-service-one [class*="col-"]:not(:first-of-type) {
  position: relative;
}
.en-service-one [class*="col-"]:not(:first-of-type)::before {
  content: "";
  width: 1px;
  height: 230px;
  background-color: #e4e4e4;
  position: absolute;
  top: 50%;
  left: 0;
  -webkit-transform: translateY(-50%);
  transform: translateY(-50%);
}

@media (max-width: 768px) {
  .service-one [class*="col-"]::before {
    display: none;
  }
}
@media (max-width: 1024px) {
  .en-service-one [class*="col-"]:nth-of-type(1)::before {
    display: none;
  }
  .en-service-one [class*="col-"]:nth-of-type(3)::before {
    display: none;
  }
  .ar-service-one [class*="col-"]:nth-of-type(2)::before {
    display: none;
  }
  .ar-service-one [class*="col-"]:nth-of-type(4)::before {
    display: none;
  }
}

.service-one__box {
  text-align: center;
  position: relative;
  margin-bottom: 20px;
}

.service-one__box h3 {
  color: var(--thm-black);
  font-size: 20px;
  font-weight: bold;
  line-height: 1;
  margin-top: 30px;
  margin-bottom: 0;
  letter-spacing: -0.04em;
}

.service-one__box h3 a {
  color: inherit;
}

.service-one__box p {
  margin: 0;
  font-size: 18px;
  line-height: 34px;
  color: #7e7e7e;
  margin-left: auto;
  margin-right: auto;
  margin-top: 15px;
}

.service-one__box:hover .service-one__icon::before,
.service-one__box:hover .service-one__icon::after {
  -webkit-transform: rotate(-35deg);
  transform: rotate(-35deg);
  opacity: 1;
}

.service-one__box:hover .service-one__icon-inner::before {
  -webkit-transform: translate(0%, 0%);
  transform: translate(0%, 0%);
}

.service-one__icon {
  position: relative;
  width: 120px;
  height: 130px;
  margin-left: auto;
  margin-right: auto;
  border-top-left-radius: 60px;
  border-top-right-radius: 60px;
  position: relative;
}

.service-one__icon::before,
.service-one__icon::after {
  content: "";
  width: 9px;
  height: 141px;
  background-color: inherit;
  border-radius: 4.5px;
  position: absolute;
  top: -15px;
  left: 30px;
  z-index: 1;
  -webkit-transform: rotate(70deg);
  transform: rotate(70deg);
  opacity: 0;
  -webkit-transition: opacity 500ms ease, -webkit-transform 500ms ease;
  transition: opacity 500ms ease, -webkit-transform 500ms ease;
  transition: opacity 500ms ease, transform 500ms ease;
  transition: opacity 500ms ease, transform 500ms ease,
    -webkit-transform 500ms ease;
}

.service-one__icon::after {
  left: 40px;
  top: -30px;
}

.service-one__icon-inner {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 10;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  justify-content: center;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  overflow: hidden;
}

.service-one__icon-inner::before {
  content: "";
  top: 0;
  left: 0;
  width: 107px;
  height: 107px;
  background-color: #fff;
  position: absolute;
  opacity: 0.2;
  -webkit-transform: translate(-30%, -30%);
  transform: translate(-30%, -30%);
  border-radius: 50%;
  -webkit-transition: -webkit-transform 500ms ease;
  transition: -webkit-transform 500ms ease;
  transition: transform 500ms ease;
  transition: transform 500ms ease, -webkit-transform 500ms ease;
}
.service-one__dark::before {
  background-color: #000 !important;
}

.service-one__icon-inner::after {
  content: "";
  width: 100%;
  height: 4px;
  background-color: #fff;
  opacity: 0.2;
  position: absolute;
  left: 0;
  bottom: 0;
}

.service-one__icon-inner i {
  color: #fff;
  font-size: 64px;
}
.background-base {
  background-color: red;
}
</style>
