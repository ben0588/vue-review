<template>
  <div class="container recommend-container mt-60">
    <div
      :class="[
        'row',
        { 'flex-row-reverse': index % 2 !== 0 },
        { 'flex-column-reverse': flexRowReverse }
      ]"
      v-for="(item, index) in list"
      :key="item.title"
    >
      <div :class="['col-12', 'col-lg-6', 'px-0']">
        <div :class="['d-flex', 'justify-content-center', 'align-items-center', 'h-100']">
          <div
            :class="[
              'd-flex',
              'flex-column',
              'justify-content-center',
              'align-items-start',
              'h-100',
              { 'p-3': windowWidth >= 375 },
              { 'p-5': windowWidth < 375 }
            ]"
          >
            <h3 class="fs-2 fw-bolder">{{ item.title }}</h3>
            <p class="text-wrap fs-5">{{ item.text }}</p>

            <ul v-if="item.isLast">
              <li
                v-for="(list, index) in item.textList"
                :key="list.title"
                :class="[
                  'list-unstyled',
                  'p-0',
                  {
                    'py-4': windowWidth >= 375
                  }
                ]"
              >
                <div class="fs-4 fw-bolder">{{ index + 1 }}.</div>
                <h4 class="fs-4 fw-bolder">{{ list.title }}</h4>
                <span>{{ list.text }}</span>
              </li>
              <button
                type="button"
                v-if="item.isLast"
                class="recommend-btn btn-primary-hover-dark fs-5 fw-bolder mt-5"
              >
                Plan a free online training
              </button>
            </ul>

            <router-link to="/" v-else>查看更多</router-link>
          </div>
        </div>
      </div>
      <div :class="['col-12', 'col-lg-6', 'px-0', { 'px-2': windowWidth <= 375 }]">
        <img
          :src="item.img"
          :alt="item.title"
          :class="['recommend-img', { 'height-1080 ': item.isLast }]"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      windowWidth: 0,
      list: [
        {
          img: 'https://images.unsplash.com/photo-1563170351-be82bc888aa4?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxjb2xsZWN0aW9uLXBhZ2V8MTd8MTE1ODAyMTR8fGVufDB8fHx8fA%3D%3D',
          title: 'Gabrielle CHANEL',
          text: '全新嗅覺體驗，花香四溢、明亮馥郁。結合茉莉、依蘭依蘭、橙花和最迷人的格拉斯晚香玉之花香，呈現出夢幻花香氣息。 極具女性特質的香奈兒嘉柏麗香水，專為光芒四射的她而生。'
        },
        {
          img: 'https://images.unsplash.com/photo-1594913785162-e678a0c23ee9?q=80&w=1587&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
          title: 'Five O’clock Au Gingembre',
          text: '生薑與溫醇的肉桂香、紅糖的香甜摻和成一氣，溫暖微辛的氣息反倒形成一股輕煙氤氳開來，還帶點微微煙醺感漫溢在整個鼻息之間，細聞之下,又還有溫溫淡淡的木香，溫和而暖心。'
        },
        {
          img: 'https://images.unsplash.com/photo-1585120040315-2241b774ad0f?q=80&w=1470&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
          title: 'CHANEL N°5',
          text: 'N°5，女性魅力的極致精髓。散發柔美澄透的乙醛花束香氣。經典傳奇香氛，蘊藏於極簡設計的獨特瓶身。'
        },
        {
          img: 'https://images.unsplash.com/photo-1542038382126-77ae2819338d?q=80&w=1587&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
          textList: [
            {
              title: 'Levels of Preventive Maintenance Compliance',
              text: 'The core idea of preventative maintenance is the performance of proactive actions against unscheduled downtime in order to identify potential defects before they evolve into something more severe.'
            },
            {
              title: 'Percentage of Planned Maintenance',
              text: 'The planned maintenance percentage is the total planned maintenance time in your CMMS software over a date range over the total number of hours of a service performed by the technicians.'
            },
            {
              title: 'Critical percentage of planned maintenance',
              text: 'Calculating the critical percentage of planned maintenance will help you prioritize the most important operations that should be performed immediately.'
            }
          ],
          isLast: true
        }
      ]
    };
  },
  computed: {
    flexRowReverse() {
      return this.windowWidth <= 375 ? true : false;
    }
  },
  mounted() {
    this.windowWidth = window.innerWidth;
    window.addEventListener('resize', () => {
      this.windowWidth = window.innerWidth;
    });
  }
};
</script>

<style lang="scss">
.recommend-container {
  overflow-x: hidden;
  width: 1110px;
  @media (max-width: 375px) {
    width: 100%;
    /* padding: 0 !important; */
  }
}

.recommend-img {
  width: 100%;
  max-width: 555px;
  height: auto;
  height: 555px;
  object-fit: cover;
  object-position: left;

  @media (max-width: 375px) {
    /* padding-left: 5px; */
    /* padding-right: 5px; */
    width: 100%;
    height: 350px;
  }
}

.height-1080 {
  height: 1080px;
}

.recommend-btn {
  /* width: 350px; */
  height: 60px;
  background: #ffffff 0% 0% no-repeat padding-box;
  border: 2px solid #000000;
  border-radius: 30px;
  opacity: 1;
  width: 100%;

  &:hover {
    color: #473b22 !important;
    background: #0000004d;
  }

  @media (max-width: 375px) {
    width: 275px;
  }
}
</style>
