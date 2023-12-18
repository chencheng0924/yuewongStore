<script setup>
import { ref, onMounted, reactive, computed } from 'vue'
import 'vue3-carousel/dist/carousel.css'
import { Carousel, Slide, Pagination, Navigation } from 'vue3-carousel'
import { getAssetsFile } from '@/utils/commonUse'
import gridCarousel from '@/components/gridCarousel.vue'
components: {
  Carousel,
  Slide,
  Pagination,
  Navigation
}
const headerList = reactive([
  { title: 'ABOUT' },
  { title: 'GALLERY' },
  { title: 'MENU' },
  { title: 'CONTACT' }
])
const footerList1 = reactive([
  { title: 'Contact Us', content: '(646) 609-2331' },
  { title: 'Address', content: '60 Bayard St, New York,<hr> NY 10013' },
])
const footerList2 = reactive([
  { title: 'Dine-in', content: ['Monday-Thursday   9AM - 9PM', 'Friday-Sunday         9AM - 10PM'] },
  { title: 'Takeout', content: ['Monday-Thursday    9AM - 9PM', 'Friday-Sunday          9AM - 10PM'] },
])
const iconList = reactive([
  { img: '/img/icon/ig.svg' },
  { img: '/img/icon/fb.svg' },
  { img: '/img/icon/google.svg' },
  { img: '/img/icon/yelp.svg' },
])
// Instagram✅https://www.instagram.com/newyuewongrestaurant/

// Facebook✅https://www.facebook.com/profile.php?id=61553334060030

// Google✅https://g.page/r/Cd5cXREYwJlEEB0/review

// Yelp✅https://www.yelp.com/biz/new-yuewong-restaurant-new-york

const goOutWeb = (index) => {
  switch (index) {
    case 0:
      window.open('https://www.instagram.com/newyuewongrestaurant/', '_blank');
      break;
    case 1:
      window.open('https://www.facebook.com/profile.php?id=61553334060030', '_blank');
      break;
    case 2:
      window.open('https://g.page/r/Cd5cXREYwJlEEB0/review', '_blank');
      break;
    case 3:
      window.open('https://www.yelp.com/biz/new-yuewong-restaurant-new-york', '_blank');
      break;  
    default:
      break;
  }
}
const email = ref('')
const showBigPhoto = ref(false)
const p = ref('')
const nowIndex = ref(0)
const nowPic = computed(() => {
  return getAssetsFile(`m${nowIndex.value}.png`)
})
const show = (type, idx) => {
  showBigPhoto.value = true
  nowIndex.value = idx
  p.value = type + idx.toString()
}
const breakpoints = {
  // 700px and up
  700: {
    itemsToShow: 3.5,
    snapAlign: 'center',
  },
  // 1024 and up
  1024: {
    itemsToShow: 5,
    snapAlign: 'start',
  },
}
const picList = reactive([
  { imgName: 'c1', w: 197, h: 198 },
  { imgName: 'c2', w: 197, h: 198 },
  { imgName: 'c3', w: 400, h: 400 },
  { imgName: 'c4', w: 299, h: 299 },
  { imgName: 'c5', w: 299, h: 299 },
  { imgName: 'c6', w: 603, h: 603 },
  { imgName: 'c7', w: 452, h: 603 }
])
// const picList = reactive(['c1', 'c2', 'c3', 'c4', 'c5', 'c6'])
const gridArea = `
  "c1 c1 c1 c2 c2 c2 c4 c4 c4 c4 c6 c6 c6 c6 c6 c7 c7 c7 c7"
  "c1 c1 c1 c2 c2 c2 c4 c4 c4 c4 c6 c6 c6 c6 c6 c7 c7 c7 c7"
  "c1 c1 c1 c2 c2 c2 c4 c4 c4 c4 c6 c6 c6 c6 c6 c7 c7 c7 c7"
  "c3 c3 c3 c3 c3 c3 c4 c4 c4 c4 c6 c6 c6 c6 c6 c7 c7 c7 c7"
  "c3 c3 c3 c3 c3 c3 c5 c5 c5 c5 c6 c6 c6 c6 c6 c7 c7 c7 c7"
  "c3 c3 c3 c3 c3 c3 c5 c5 c5 c5 c6 c6 c6 c6 c6 c7 c7 c7 c7"
  "c3 c3 c3 c3 c3 c3 c5 c5 c5 c5 c6 c6 c6 c6 c6 c7 c7 c7 c7"
  "c3 c3 c3 c3 c3 c3 c5 c5 c5 c5 c6 c6 c6 c6 c6 c7 c7 c7 c7"

`
const openPic = (idx) => {
  console.log(idx)
}
const changePicIndex = (type) => {
  type == 'back' ? nowIndex.value -= 1 : nowIndex.value += 1
}
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Edu+TAS+Beginner:wght@600&family=Hind:wght@700&family=Nunito+Sans:opsz,wght@6..12,700&family=Rubik+Bubbles&display=swap');
</style>
<template>
  <div class="w-screen bg-[#FFD230] flex flex-col pt-[100px] items-center justify-end">
    <div class="flex flex-col items-center titleC">
      <div class="font-bold text-[64px] flex flex-col items-center titleCText">
        <span data-aos="zoom-in">NEW YUE WONG RESTAURANT</span>
        <span>裕旺大饭店</span>
      </div>
      <div class="flex gap-[46px] mt-[30px] mb-[30px] titleCOption">
        <div v-for="(item, idx) in headerList" :key="idx" class="py-[15px] px-[23px] bg-white rounded-[50px] font-bold cursor-pointer">
          {{ item.title }}
        </div>
      </div>
      <img src="@/assets/img/img1.png" alt="img" class="">
    </div>
  </div>
  <div class="flex w-screen justify-center pt-[154px] pb-[111px] about">
    <div class="flex w-[70%] gap-[80px] justify-center aboutC">
      <img src="@/assets/img/img2.png" alt="img" data-aos="fade-up">
      <div class="w-[40%] aboutCArea">
        <div class="font-bold text-[32px] mb-[30px] gap-3 flex aboutCTitle" data-aos="fade-down-left">
          <span>ABOUT</span>
          <span class="text-[#FFD230]">NYW</span>
        </div>
        <div class="text-[20px] leading-loose aboutCText">
          Welcome to New Yue Wong in NYC's Chinatown since 2011! Try our famous Peking Duck—crispy, succulent, and full of authentic flavor. Our spot blends tradition with innovation for a memorable dining experience that captures the spirit of Chinatown in every delicious bite!
        </div>
      </div>
    </div>
  </div>
  <!-- Menu-->
  <div class="w-screen bg-[#FFD230] py-10 menuBanner flex flex-col items-center h-[600px]">
    MENU
    <div class="max-w-[1200px]">
      <Carousel :snapAlign="'center'" :breakpoints="breakpoints">
        <Slide v-for="slide in 11" :key="slide" @click="show('m', slide)">
          <div class="carousel__item">
            <!-- <img :src="getAssetsFile(`m${slide}.png`)" class="w-[200px]"> -->
            <img :src="getAssetsFile(`m${slide}.png`)">
          </div>
        </Slide>
        <template #addons>
          <Navigation />
        </template>
      </Carousel>
    </div>
  </div>
  <!-- Food -->
  <div class="flex w-screen justify-center pt-[154px] pb-[111px]">
    <div class="w-[1200px] flex items-center gap-4">
      <div class="exploreTitle whitespace-nowrap">
        Explore<br/>Our Food
      </div>
      <gridCarousel :picList="picList" :gridArea="gridArea" :ifOverflowScroll="true" @openPic="openPic"/>
    </div>
    <!-- <div class="exploreCShow">
      <img src="../assets/img/text3.png" alt="">
      <div class="exploreCImgList">
        <div class="list1">
          <img v-for="item in 3" :key="item" :src="getAssetsFile(`menu/left${item}.jpg`)" alt="">
        </div>
        <div class="list2">
          <img v-for="item in 3" :key="item" :src="getAssetsFile(`menu/right${item}.jpg`)" alt="">
        </div>
      </div>
    </div> -->
  </div>
  <div class="bg-[#FFD230] w-screen h-[320px] justify-center items-center flex flex-col mail">
    <span class="emailTitle">Stay savory!</span>
    <span class="emailTitle content">Join our email list and get access to specials deals exclusive to our subscribers.</span>
    <div class="flex input px-[10px] py-[10px] bg-white rounded-2xl mt-[20px]">
      <el-input
        v-model="email"
        placeholder="enter your email address"
      />
      <div class="sendBtn bg-slate-600 text-white px-3 py-2 flex items-center justify-center rounded-xl cursor-pointer">
        <span>Subscribe</span>
      </div>
    </div>
  </div>
  <div class="flex w-screen justify-center pt-[154px] pb-[111px] igFollow">
    <div class="flex w-[70%] gap-[80px] justify-center items-center flex-col">
      <div class="flex font-bold text-[36px]">
        <span>Follow</span>
        <span class="text-[#FFD230]">@newyuewongrestaurant</span>
      </div>
      <div class="flex gap-[40px]">
        <img src="@/assets/img/imgb1.png">
        <img src="@/assets/img/imgb2.png">
        <img src="@/assets/img/imgb3.png">
        <img src="@/assets/img/imgb4.png">
      </div>
    </div>
  </div>
  <div class="w-screen flex footer">
    <img class="footerImg" src="@/assets/img/footer.png" alt="">
    <div class="bg-[#FFD230] w-full px-[74px] py-[98px] footerContent">
      <div class="content">
        <div class="area">
          <div v-for="(item, index) in footerList1" :key="index" class="areaItem">
            <div class="title">{{ item.title }}</div>
            <div class="text" v-html="item.content" />
          </div>
        </div>
        <div class="area2">
          <div class="area2Title">Opening Hours</div>
          <div v-for="(item, index) in footerList2" :key="index"  class="area2Item">
            <div class="title">{{ item.title }}</div>
            <div class="area2ContentItem">
              <div v-for="(item2, index2) in item.content" :key="index2" class="contentItem">
                <div class="text">{{ item2 }}</div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="link">
        <div class="linkList cursor-pointer">
          <img @click="goOutWeb(index)" v-for="(item, index) in iconList" :key="index" :src="item.img" alt="">
        </div>
        <div class="remind">© 2023 NEW YUE WONG RESTAURANT. ALL RIGHTS RESERVED.</div>
      </div>
    </div>
  </div>
  <div class="footerC">
    <img class="footerImg" src="@/assets/img/footer.png" alt="">
    <div class="linkList cursor-pointer">
      <img @click="goOutWeb(index)" v-for="(item, index) in iconList" :key="index" :src="item.img" alt="">
    </div>
    <div class="area">
      <div v-for="(item, index) in footerList1" :key="index" class="areaItem">
        <div class="title">{{ item.title }}</div>
        <div class="text" v-html="item.content" />
      </div>
    </div>
    <div class="area2">
      <div class="area2Title">Opening Hours</div>
      <div v-for="(item, index) in footerList2" :key="index"  class="area2Item">
        <div class="title">{{ item.title }}</div>
        <div class="area2ContentItem">
          <div v-for="(item2, index2) in item.content" :key="index2" class="contentItem">
            <div class="text">{{ item2 }}</div>
          </div>
        </div>
      </div>
    </div>
    <div class="remind">© 2023 NEW YUE WONG RESTAURANT. ALL RIGHTS RESERVED.</div>
  </div>
  <div class="fixed top-0 left-0 w-screen h-screen flex items-center justify-center pic" v-if="showBigPhoto">
    <div class="absolute right-10 top-5 text-xl font-semibold z-20 text-white cursor-pointer" @click="showBigPhoto = false">CLOSE</div>
    <img src="@/assets/img/ca.png" class="rotate-180 w-[50px] absolute top-[50%] left-[20%] translate-y-[-50%]" v-if="nowIndex > 1" @click="changePicIndex('back')">
    <img :src="nowPic" class="w-[70vw] h-[80vh] object-contain">
    <img src="@/assets/img/ca.png" class="w-[50px] absolute top-[50%] right-[20%] translate-y-[-50%]" v-if="nowIndex < 11" @click="changePicIndex('go')">
  </div>
</template>
<style lang="scss" scoped>
:deep(.el-input) {
  width: 400px;
  .el-input__wrapper {
    border-radius: 0px;
    box-shadow: none;
    background-color: white;
    border: none;
  }
}
.send {
  display: flex;
  align-items: center;
  justify-content: center;
  border-top: 2px solid black;
  border-right: 2px solid black;
  border-bottom: 2px solid black;
  padding: 10px;
}
.footerImg{
  width: 40%;
  object-fit: cover;
}
.footerContent{
  display: flex;
  flex-direction: column;

  .content{
    display: flex;
    justify-content: space-evenly;
    .area{
      display: flex;
      flex-direction: column;
      gap: 20px;
      width: 40%;
      .areaItem{
        display: flex;
        flex-direction: column;
        gap: 5px;
        .title{
          font-size: 20px;
          font-weight: bold
        }
      }
    }
    .area2{
      display: flex;
      flex-direction: column;
      gap: 20px;
      width: 60%;
      .area2Title{
        font-size: 20px;
        font-weight: bold
      }
      .area2Item{
        display: flex;
        align-items: center;
        .area2ContentItem{
          display: flex;
          flex-direction: column;
          justify-content: space-between;
          .contentItem{
            display: flex;
            
          }
        }
        .title{
          font-size: 18px;
          font-weight: 600;
          width: 100px;
        }
        .text{
          font-size: 14px;
        }
      }
    }
  }
  .link{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 30px;
    .linkList{
      display: flex;
      gap: 10px;
    }
    .remind{
      font-size: 14px;
    }
  }
}
:deep(.carousel__prev) {
  left: -45px;
}
:deep(.carousel__next) {
  right: -45px;
}
.pic {
  background-color: rgba(0,0,0,0.7);
}
.exploreCShow, .menuCShow, .footerC{
  display: none;
}

@media screen and (max-width: 990px) {
  .titleC{
    .titleCText{
      margin-bottom: 30px;
      span{
        font-size: 20px;
      }
    }
    .titleCOption{
      display: none;
    }
    img{
      height: 70vh;
      object-fit: cover;
    }
  }
  .about{
    padding: 60px 0;
    .aboutC{
      flex-direction: column;
      .aboutCArea{
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        .aboutCTitle{
          font-size: 20px;
        }
        .aboutCText{
          font-size: 16px;
        }
      }
    }
  }
  .explore{
    background-color: #FFD230;
    padding: 50px;
    .exploreC{
      display: none;
    }
    .exploreCShow{
      display: flex;
      flex-direction: column;
      gap: 30px;
      .exploreCImgList{
        display: flex;
        gap: 5px;
        .list1, .list2{
          display: flex;
          flex-direction: column;
          gap: 20px;
          img{
            width: 145px;
            height: 168px;
            object-fit: cover;
          }
        }
        .list2{
          padding-top: 20px;
        }
      }
    }
  }
  .menu{
    background-color: #FFD230;
    padding: 50px;
    .menuC{
      display: none;
    }
    .menuCShow{
      display: flex;
      flex-direction: column;
      .title{
        transform: scale(.5);
      }
    }
  }
  .mail{
    background-color: #fff;
    flex-direction: column;
    padding: 0 50px;
    gap: 20px;
    .input{
      width: 90%;
    }
  }
  .igFollow, .footer{
    display: none;
  }
  .footerC{
    background-color: #FFD230;
    width: 100vw;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 30px 0;
    img{
      width: 90%;
      margin-bottom: 20px;
    }
    .linkList{
      display: flex;
      gap: 10px;
    }
    .area{
      text-align: center;
      .areaItem{
        margin-bottom: 25px;
        .title{
          font-weight: bold;
        }
      }
    }
    .area2{
      text-align: center;
      .area2Title{
        font-weight: bold;
      }
      .area2Item{
        margin-bottom: 25px;
      }
    }
    .remind{
      text-align: center;
      font-size: 9px;
    }
  }
}
.menuBanner {
  font-family: 'Rubik Bubbles';
  color: white;
  font-size: 60px;
}
.exploreTitle {
  font-family: 'Rubik Bubbles';
  color: #FFD230;
  font-size: 60px;
}
.emailTitle {
  font-family: 'Rubik Bubbles';
  color: black;
  font-size: 60px;
  &.content {
    font-family: 'Noto Sans';
    font-size: 20px;
  }
}
</style>