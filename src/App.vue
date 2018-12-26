<template>
  <div id="app" :style="{backgroundImage:'url(' + backgroundImage + ')'}">
    <div class="weather" id="weather">
      <!-- nav -->
      <div class="weather_content_wrapper">
        <div class="weather_nav">
          <div class="weather_nav_icon"><i class="iconfont icon-fenxiang"></i></div>
          农业气象
        </div>

        <!-- 描述 -->
        <div class="weather_describe">
          <div class="degree">
            <div class="degree_number">14</div>
            <div class="degree_number_right">
              <div class="degree_icon">o</div>
              <div class="degree_yun">多云</div>
            </div>
          </div>
          <div class="describe">
            <div class="describe_quality">空气质量：优</div>
            <div class="describe_list">
              <div class="describe_item">晴</div>
              <div class="describe_item">22 ~ 26℃</div>
              <div class="describe_item">南风微风</div>
            </div>
          </div>
        </div>

        <div class="weather_comprehensive">
          <!-- 地址 -->
          <div class="weather_address pt">
            <i class="iconfont icon-addressfill"></i> 北京市&nbsp;&nbsp;阜安西路
          </div>
          <!-- 日期 -->
          <div class="weather_time pt">
            <i class="iconfont icon-riqi"></i> 3月22日&nbsp;&nbsp;周四&nbsp;&nbsp;二月初六
          </div>
          <!-- 预警 -->
          <div class="weather_warning pt">
            <i class="iconfont icon-yujing"></i> 预警：大风蓝色预警
            <div class="subscribe">一键订阅</div>
          </div>
        </div>
      </div>
<!-- /气象正常，暂无预警; -->
        <div class="weather_weilai">未来七天<i class="iconfont icon-xiayiyeqianjinchakangengduo"></i></div>
      <div class="weather_swiper">
        <swiper :options="swiperOption" ref="mySwiper">
          <swiper-slide v-for="(item, index) in weatherList" :key="index">
            <div class="swiper_content_wrapper">
              <div class="xinqi">{{item.week}}</div>
              <div class="riqi base">{{item.mouth}}</div>
              <div class="photo base"><img :src="item.img" alt=""></div>
              <div class="wendu base">{{item.wendu}}</div>
              <div class="qing base">{{item.qing}}</div>
              <div class="feng base">{{item.feng}}</div>
              <div class="wuran base">{{item.wuran}}</div>
            </div>
          </swiper-slide>
        </swiper>
      </div>
    </div>
  </div>
</template>

<script>
  import {
    swiper,
    swiperSlide
  } from 'vue-awesome-swiper'
  import 'swiper/dist/css/swiper.min.css'
  export default {
    name: 'App',

    created() {
      this.id = this.getUrlParam('id')
    },
    mounted() {
      document.getElementById('app').style.height = document.documentElement.clientHeight + 'px'
    },
    computed: {
      swiper() {
        return this.$refs.mySwiper.swiper
      }
    },
    methods: {
      getUrlParam(params) {
        var reg = new RegExp("(^|&)" + params + "=([^&]*)(&|$)");
        var r = window.location.search.substr(1).match(reg);
        if (r !== null) {
          return unescape(r[2])
        }
        return null;
      }
    },
     data() {
      return {
        backgroundImage: require('./assets/images/weatherss.png'),
        weatherList: [{
          week: '周日',
          mouth: '03月17日',
          img: 'https://ss1.bdstatic.com/5eN1bjq8AAUYm2zgoY3K/r/www/aladdin/img/new_weath/icon/5.png',
          wendu: '22 ~ 26℃',
          qing: '晴',
          feng: '微风',
          wuran: '124 轻度污染'
        },
        {
          week: '周一',
          mouth: '03月18日',
          img: 'https://ss1.bdstatic.com/5eN1bjq8AAUYm2zgoY3K/r/www/aladdin/img/new_weath/icon/5.png',
          wendu: '22 ~ 26℃',
          qing: '晴',
          feng: '微风',
          wuran: '124 轻度污染'
        },
        {
          week: '周二',
          mouth: '03月19日',
          img: 'https://ss1.bdstatic.com/5eN1bjq8AAUYm2zgoY3K/r/www/aladdin/img/new_weath/icon/5.png',
          wendu: '22 ~ 26℃',
          qing: '晴',
          feng: '微风',
          wuran: '124 轻度污染'
        },
        {
          week: '周三',
          mouth: '03月20日',
          img: 'https://ss1.bdstatic.com/5eN1bjq8AAUYm2zgoY3K/r/www/aladdin/img/new_weath/icon/5.png',
          wendu: '22 ~ 26℃',
          qing: '晴',
          feng: '微风',
          wuran: '124 轻度污染'
        },
        {
          week: '周四',
          mouth: '03月21日',
          img: 'https://ss1.bdstatic.com/5eN1bjq8AAUYm2zgoY3K/r/www/aladdin/img/new_weath/icon/5.png',
          wendu: '22 ~ 26℃',
          qing: '晴',
          feng: '微风',
          wuran: '124 轻度污染'
        },
        {
          week: '周五',
          mouth: '03月22日',
          img: 'https://ss1.bdstatic.com/5eN1bjq8AAUYm2zgoY3K/r/www/aladdin/img/new_weath/icon/5.png',
          wendu: '22 ~ 26℃',
          qing: '晴',
          feng: '微风',
          wuran: '124 轻度污染'
        },
        {
          week: '周六',
          mouth: '03月23日',
          img: 'https://ss1.bdstatic.com/5eN1bjq8AAUYm2zgoY3K/r/www/aladdin/img/new_weath/icon/5.png',
          wendu: '22 ~ 26℃',
          qing: '晴',
          feng: '微风',
          wuran: '124 轻度污染'
        }
        ],
        swiperOption: {
          notNextTick: true,
          breakpoints: {
            1024: {
              slidesPerView: 5,
              spaceBetween: 10,
            },
            768: {
              slidesPerView: 3,
              spaceBetween: 10,
            },
            640: {
              slidesPerView: 3,
              spaceBetween: 10,
            },
            320: {
              slidesPerView: 2,
              spaceBetween: 10,
            }
          }
        }
      }
    },
    components: {
      swiper,
      swiperSlide
    }
  }
</script>

<style>
  body {
    font-family: 'MicrosoftYaHei';
  }

  #app {
    background-size: cover;
    /* background-size: 100% 100%; */
    background-repeat: no-repeat;
  }

  .weather {
    padding: 0px 20px;
    position: relative;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .weather_content_wrapper {
    display: flex;
    flex-direction: column;
    width: 100%;
    height: 100%;
  }

  .weather_nav {
    width: 100%;
    height: 92px;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    position: relative;
    color: #fff;
    font-size: 36px;
  }

  .weather_nav .weather_nav_icon {
    position: absolute;
    left: 0;
    top: 0;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .weather_nav .weather_nav_icon>i {
    font-size: 42px;
    color: #fff;
  }

  .weather_describe {
    width: 100%;
    margin-top: 130px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .weather_describe .degree {
    display: flex;
    padding-left: 10px;
  }

  .degree .degree_number {
    font-size: 80px;
    color: #fff;
  }

  .degree .degree_number_right {
    padding-left: 20px;
    display: flex;
    flex-direction: column;
  }

  .degree_number_right .degree_icon,
  .degree_number_right .degree_yun {
    font-size: 35px;
    color: #fff;
  }

  .weather_describe .describe {
    flex: 1;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    padding-left: 80px;
  }

  .describe .describe_quality {
    color: #fff;
    font-size: 30px;
  }

  .describe .describe_list {
    display: flex;
    flex-direction: row;
  }

  .describe .describe_list .describe_item {
    padding-right: 20px;
    color: #fff;
    font-size: 30px;
  }

  .weather_comprehensive {
    width: 100%;
    margin-top: 20px;
    display: flex;
    flex-direction: column;
  }

  .weather_comprehensive .weather_address {
    padding-left: 10px;
    display: flex;
    align-items: center;
    font-size: 28px;
    color: #fff;
  }

  .weather_comprehensive .weather_address>i {
    font-size: 35px;
    color: #fff;
    padding-right: 10px;
  }

  .weather_comprehensive .weather_time {
    padding-left: 10px;
    display: flex;
    align-items: center;
    font-size: 28px;
    color: #fff;
  }

  .weather_comprehensive .weather_time>i {
    font-size: 35px;
    color: #fff;
    padding-right: 10px;
  }

  .weather_comprehensive .weather_warning {
    padding-left: 10px;
    display: flex;
    align-items: center;
    font-size: 28px;
    color: #fff;
  }

  .weather_comprehensive .weather_warning>i {
    font-size: 35px;
    color: #ffff01;
    padding-right: 10px;
  }
   .pt {
    padding: 7px 0px;
  }
  .subscribe {
    padding: 3px 15px;
    border-radius: 20px;
    background: #ffff01;
    color: #1ab2fe;
    font-size: 22px;
margin-left: 40px;
  }


  .weather_swiper {
    width: 100%;
    height: 500px;
    margin-bottom: 20px;
  }

.weather_weilai {
  padding: 20px 0px;
  color: #fff;
  font-size: 30px;
}
.weather_weilai>i {
  color: #fff;
  font-size: 30px;
}
  .swiper-container {
    width: 100%;
    /* padding: 0rem 30px; */
    height: 100%;
  }

  .swiper-slide {
    text-align: center;
    font-size: 18px;
    background: #fff;
    display: -webkit-box;
    display: -ms-flexbox;
    display: -webkit-flex;
    display: flex;
    -webkit-box-pack: center;
    -ms-flex-pack: center;
    -webkit-justify-content: center;
    justify-content: center;
    -webkit-box-align: center;
    -ms-flex-align: center;
    -webkit-align-items: center;
    align-items: center;
    flex-direction: column;
    background: #1ab2fe;
    justify-content: space-around;
    border-radius: 10px;
  }

  .swiper_content_wrapper {
    flex: 1;
    padding: 20px 10px;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
  }

  img {
    /* width: 50px; */
    /* height: 50px; */
    display: block;
  }

  .xinqi {
    font-size: 30px;
    color: #fff;
  }
.photo {
  display: flex;
  width: 100%;
  justify-content: center;
  align-items: center;
  padding: 40px 0px;
}
  .base {
    color: #fff;
    font-size: 26px;
    padding: 5px 0px;
  }

  .wuran {
    padding: 5px 18px;
    border-radius: 25px;
    font-size: 18px;
    background: #0094fa;
  }
</style>
