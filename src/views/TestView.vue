<template>
  <div class="about">
    <div class="navbar">
      <div class="title" id="titletext">
        您好，欢迎来到山东第一医科大学第三附属医院！
      </div>
      <div class="buttons">
        <div class="edge"></div>
        <div class="buttonl"><a href="#">就诊服务</a></div>
        <div class="button"><a href="#">医院动态</a></div>
        <div class="button"><a href="#">登录|注册</a></div>
        <div class="edge"></div>
      </div>
    </div>

    <div class="searchbar">
      <div id="logo">
        <img src="../assets/logo.png" id="logoimg" />
        <div id="logotext">
          <p class="cnlogotext">山东第一医科大学第三附属医院</p>

          <p class="cnlogotext" style="font-size: 19px">
            山东省医学科学院附属医院
          </p>
        </div>
      </div>
      <SearchBar :callback="onCallBack"> </SearchBar>
      <!--  -->
    </div>

    <div class="border"></div>

    <div class="navbar2">
      <div class="buttonlist">
        <div class="button2" align="center"><a href="#">首页</a></div>
        <div class="button2" align="center"><a href="#">医院概况</a></div>
        <div class="button2" align="center"><a href="#">医院动态</a></div>
        <div class="button2" align="center"><a href="#">党建文化</a></div>
        <div class="button2" align="center"><a href="#">就诊指南</a></div>
        <div class="button2" align="center"><a href="#">科室导航</a></div>
        <div class="button2" align="center"><a href="#">医疗团队</a></div>
        <div class="button2" align="center"><a href="#">健康科普</a></div>
        <div class="button2" align="center"><a href="#">院务公开</a></div>
      </div>
    </div>

    <div class="currentposition">
      <div id="currentpositiontext">您所在的位置： 首页>>医疗团队</div>
    </div>

    <swiper
      :options="swiperOption"
      @swiper="onSwiper"
      @slideChange="onSlideChange"
    >
      <swiper-slide><img src="../assets/20210330164308.jpg" /></swiper-slide>
      <swiper-slide><img src="../assets/20210901174739.jpg" /></swiper-slide>
      <swiper-slide><img src="../assets/20230505113055.jpg" /></swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
      <div class="swiper-button-prev" slot="button-prev"></div>
      <div class="swiper-button-next" slot="button-next"></div>
    </swiper>

    <div id="app">
      <div class="cardcontainer" style="height: 20px"></div>
      <div class="tabbar">
        <template v-for="(item, index) in tabNames">
          <div class="deactivated" align="center">
            <a @click="tabClik(index)">{{ item }}</a>
            <div class="selected visible" v-if="clickIndex === index"></div>
            <div class="selected" v-if="clickIndex != index"></div>
          </div>
        </template>

        <!-- <div class="deactivated" align=center><a @click="changeDepartment('1')">内科医生</a>
                <div class="selected" :class="{visible: physicianvisible}"></div>
            </div>
            <div class="deactivated" align=center><a @click="changeDepartment('2')">外科医生</a>
                <div class="selected" :class="{visible: surgeonvisible}"></div>
            </div>
            <div class="deactivated" align=center><a @click="changeDepartment('3')">妇科医生</a>
                <div class="selected" :class="{visible: gynecologistvisible}"></div>
            </div>
            <div class="deactivated" align=center><a @click="changeDepartment('4')">儿科医生</a>
                <div class="selected" :class="{visible: pediatricianvisible}"></div>
            </div> -->
      </div>

      <div class="cardcontainer">
        <div class="border"></div>
        <div class="cardcontainer" style="height: 20px"></div>

        <div v-for="(item, index) in tabNames">
          <div class="card-container" v-if="clickIndex === index">
            <div class="card" v-for="doctor in doctors[index]">
              <Card :doctor="doctor"> </Card>
            </div>
          </div>
        </div>
        <!-- Add as many cards as necessary -->
      </div>
    </div>
  </div>
</template>

<style>
</style>

 

<script>
import { defineComponent } from "@vue/composition-api";
import Img1 from "../assets/Image-1.png";
import Img2 from "../assets/Image-2.png";
import "../assets/medteamstyle.css";
import Card from "./CardView.vue";
import SearchBar from "./SearchBar.vue";

export default defineComponent({
  components: {
    Card,
    SearchBar,
  },
  props: {
    aaa: {
      type: String,
      default: "请输入",
    },
  },
  data() {
    return {
      swiperOption: {
        slidesPerView: 1,
        // 设置分页器
        pagination: {
          el: ".swiper-pagination",
          // 设置点击可切换
          clickable: true,
        },
        // 设置前进后退按钮
        navigation: {
          nextEl: ".swiper-button-next",
          prevEl: ".swiper-button-prev",
        },
        // 设置自动轮播
        autoplay: {
          delay: 5000, // 5秒切换一次
        },
        // 设置轮播可循环
        loop: true,
      },

      text: "test",

      visible: false,
      activeName: "second",

      tabNames: ["内科医生", "外科医生", "妇科医生", "儿科医生"],
      clickIndex: 1,

      doctors: [
        [
          {
            name: "王丿",
            imgsrc: Img1,
            ocptntitle: "主任",
            specialties: "熟练掌握呼吸及心脑血管系统等老...",
            introduction: "王丿，毕业于山东大学医学院...",
          },
          {
            name: "王刂",
            imgsrc: Img1,
            ocptntitle: "副主任",
            specialties: "精通掌握呼吸及心脑血管系统等老...",
            introduction: "王刂，毕业于山西大学医学院...",
          },
          {
            name: "王川",
            imgsrc: Img1,
            ocptntitle: "副主任",
            specialties: "完整掌握呼吸及心脑血管系统等老...",
            introduction: "王川，毕业于广东大学医学院...",
          },
          {
            name: "王灬",
            imgsrc: Img1,
            ocptntitle: "副主任",
            specialties: "贯通掌握呼吸及心脑血管系统等老...",
            introduction: "王灬，毕业于广西大学医学院...",
          },
          {
            name: "张钟文",
            imgsrc: Img2,
            ocptntitle: "院长、科主任",
            specialties: "在糖尿病及其慢性并发症、甲状...",
            introduction: "医学学士、副主任医师，青年中医...",
          },
          {
            name: "张钟武",
            imgsrc: Img2,
            ocptntitle: "副院长",
            specialties: "在糖尿病及其慢性并发症、甲状...",
            introduction: "医学硕士、副主任医师，青年中医...",
          },
          {
            name: "张钟理",
            imgsrc: Img2,
            ocptntitle: "主任",
            specialties: "在糖尿病及其慢性并发症、甲状...",
            introduction: "医学博士、主任医师，青年中医...",
          },
          {
            name: "张钟工",
            imgsrc: Img2,
            ocptntitle: "副主任",
            specialties: "在糖尿病及其慢性并发症、甲状...",
            introduction: "医学院士、副主任医师，青年中医...",
          },
        ],
        [
          {
            name: "王川",
            imgsrc: Img1,
            ocptntitle: "主任",
            specialties: "熟练掌握呼吸及心脑血管系统等老...",
            introduction: "王川，毕业于山东大学医学院...",
          },
          {
            name: "张川",
            imgsrc: Img1,
            ocptntitle: "副主任",
            specialties: "精通掌握呼吸及心脑血管系统等老...",
            introduction: "张川，毕业于山西大学医学院...",
          },
          {
            name: "李川",
            imgsrc: Img1,
            ocptntitle: "副主任",
            specialties: "完整掌握呼吸及心脑血管系统等老...",
            introduction: "李川，毕业于广东大学医学院...",
          },
          {
            name: "赵川",
            imgsrc: Img1,
            ocptntitle: "副主任",
            specialties: "贯通掌握呼吸及心脑血管系统等老...",
            introduction: "赵川，毕业于广西大学医学院...",
          },
          {
            name: "张钟文",
            imgsrc: Img2,
            ocptntitle: "院长、科主任",
            specialties: "在糖尿病及其慢性并发症、甲状...",
            introduction: "医学学士、副主任医师，青年中医...",
          },
          {
            name: "张时文",
            imgsrc: Img2,
            ocptntitle: "副院长",
            specialties: "在糖尿病及其慢性并发症、甲状...",
            introduction: "医学硕士、副主任医师，青年中医...",
          },
          {
            name: "张分文",
            imgsrc: Img2,
            ocptntitle: "主任",
            specialties: "在糖尿病及其慢性并发症、甲状...",
            introduction: "医学博士、主任医师，青年中医...",
          },
          {
            name: "张秒文",
            imgsrc: Img2,
            ocptntitle: "副主任",
            specialties: "在糖尿病及其慢性并发症、甲状...",
            introduction: "医学院士、副主任医师，青年中医...",
          },
        ],
        [
          {
            name: "王妇女之友",
            imgsrc: Img1,
            ocptntitle: "主任",
            specialties: "熟练掌握呼吸及心脑血管系统等老...",
            introduction: "王川，毕业于山东大学医学院...",
          },
          {
            name: "张妇女之友",
            imgsrc: Img1,
            ocptntitle: "副主任",
            specialties: "精通掌握呼吸及心脑血管系统等老...",
            introduction: "张川，毕业于山西大学医学院...",
          },
          {
            name: "李妇女之友",
            imgsrc: Img1,
            ocptntitle: "副主任",
            specialties: "完整掌握呼吸及心脑血管系统等老...",
            introduction: "李川，毕业于广东大学医学院...",
          },
          {
            name: "赵妇女之友",
            imgsrc: Img1,
            ocptntitle: "副主任",
            specialties: "贯通掌握呼吸及心脑血管系统等老...",
            introduction: "赵川，毕业于广西大学医学院...",
          },
          {
            name: "张钟文",
            imgsrc: Img2,
            ocptntitle: "院长、科主任",
            specialties: "在糖尿病及其慢性并发症、甲状...",
            introduction: "医学学士、副主任医师，青年中医...",
          },
          {
            name: "张时文",
            imgsrc: Img2,
            ocptntitle: "副院长",
            specialties: "在糖尿病及其慢性并发症、甲状...",
            introduction: "医学硕士、副主任医师，青年中医...",
          },
          {
            name: "张分文",
            imgsrc: Img2,
            ocptntitle: "主任",
            specialties: "在糖尿病及其慢性并发症、甲状...",
            introduction: "医学博士、主任医师，青年中医...",
          },
          {
            name: "张秒文",
            imgsrc: Img2,
            ocptntitle: "副主任",
            specialties: "在糖尿病及其慢性并发症、甲状...",
            introduction: "医学院士、副主任医师，青年中医...",
          },
        ],
        [
          {
            name: "王爱幼",
            imgsrc: Img1,
            ocptntitle: "主任",
            specialties: "熟练掌握呼吸及心脑血管系统等老...",
            introduction: "王丿，毕业于山东大学医学院...",
          },
          {
            name: "张爱幼",
            imgsrc: Img1,
            ocptntitle: "副主任",
            specialties: "精通掌握呼吸及心脑血管系统等老...",
            introduction: "王刂，毕业于山西大学医学院...",
          },
          {
            name: "李爱幼",
            imgsrc: Img1,
            ocptntitle: "副主任",
            specialties: "完整掌握呼吸及心脑血管系统等老...",
            introduction: "王川，毕业于广东大学医学院...",
          },
          {
            name: "赵爱幼",
            imgsrc: Img1,
            ocptntitle: "副主任",
            specialties: "贯通掌握呼吸及心脑血管系统等老...",
            introduction: "王灬，毕业于广西大学医学院...",
          },
          {
            name: "张钟文",
            imgsrc: Img2,
            ocptntitle: "院长、科主任",
            specialties: "在糖尿病及其慢性并发症、甲状...",
            introduction: "医学学士、副主任医师，青年中医...",
          },
          {
            name: "张钟武",
            imgsrc: Img2,
            ocptntitle: "副院长",
            specialties: "在糖尿病及其慢性并发症、甲状...",
            introduction: "医学硕士、副主任医师，青年中医...",
          },
          {
            name: "张钟理",
            imgsrc: Img2,
            ocptntitle: "主任",
            specialties: "在糖尿病及其慢性并发症、甲状...",
            introduction: "医学博士、主任医师，青年中医...",
          },
          {
            name: "张钟工",
            imgsrc: Img2,
            ocptntitle: "副主任",
            specialties: "在糖尿病及其慢性并发症、甲状...",
            introduction: "医学院士、副主任医师，青年中医...",
          },
        ],
      ],
    };
  },
  methods: {
    handleClick(tab, event) {
      console.log(tab, event);
    },
    getImageUrl(imgsrc) {
      return imgsrc;
    },
    tabClik(index) {
      this.clickIndex = index;
      console.log(this.clickIndex);
    },

    onCallBack(Str){
      alert("找不到\""+Str+"\"相关的内容")
    },

    onSwiper() {},
    onSlideChange() {},
  },

  setup() {},

  mounted() {},
});
</script>

