<template>
  <div>
    <div :class="oo">1</div>
    <vue-cal
      style="height：250px"
      class="vuecal__title-bar"
      locale="zh-cn"
    ></vue-cal>
    <br />
    <vue-cal
      hide-view-selector
      :time="false"
      active-view="month"
      class="vuecal--green-theme vuecal--rounded-theme cla-one"
      xsmall
      locale="zh-cn"
    >
      <i aria-hidden="true" class="v-icon material-icons">arrow_back</i>
      <i aria-hidden="true" class="v-icon material-icons">arrow_forward</i>
    </vue-cal>

    <vue-cal
      class="vuecal--rounded-theme vuecal--green-theme"
      xsmall
      hide-view-selector
      :time="false"
      active-view="month"
      :disable-views="['week']"
      style="width: 270px; height: 300px"
    >
    </vue-cal>

    <vue-cal
      :time="false"
      active-view="month"
      :disable-views="['years', 'year', 'week']"
    />
    <vue-cal :time="false" small active-view="year" locale="zh-cn" />

    <vue-cal :time-from="7 * 60" :time-to="20 * 60" :time-step="60" />

    <vue-cal
      :time-from="8 * 60"
      :time-to="24 * 60"
      :special-hours="specialHours" 
      
    />
<br>
    <!-- <vue-cal xsmall active-view="day" :disable-views="['years', 'year', 'month']" class="vuecal--green-theme vuecal__now-line" /> -->
<br>
  <vue-cal selected-date="2018-11-19"
         :time="false"
         :disable-views="['years', 'year', 'month']"
         hide-weekends
         :events="events">
</vue-cal>
  </div>
</template>

<script>
import "vue-cal/dist/vuecal.css";
import "vue-cal/dist/i18n/zh-cn.js";
import VueCal from "vue-cal";

const dailyHours = { from: 9 * 60, to: 18 * 60, class: 'business-hours' }


export default {
  
  data() {
    return {
      oo:{
        aa:true
      },
      specialHours: {
        1: { from: 9 * 60, to: 18 * 60, class: "business-hours" },
        2: dailyHours,
        3: [
          { from: 9 * 60, to: 12 * 60, class: "business-hours" },
          { from: 14 * 60, to: 18 * 60, class: "business-hours" },
        ],
        4: dailyHours,      
        5: dailyHours,       
      },
       events: [
    {
      start: '2018-11-21',
      end: '2018-11-21',
      title: 'Need to go shopping',
      content: '<i class="v-icon material-icons">shopping_cart</i>',
      class: 'leisure'
    },
    {
      start: '2018-11-21',
      end: '2018-11-21',
      title: 'Golf with John',
      content: '<i class="v-icon material-icons">golf_course</i>',
      class: 'sport'
    },
    {
      start: '2018-11-22',
      end: '2018-11-22',
      title: 'Dad\'s birthday!',
      content: '<i class="v-icon material-icons">cake</i>',
      class: 'sport'
    }
  ]
    };
  },
  components: { VueCal }
};
</script>

<style>
.cla-one {
  background-color: paleturquoise;
}
.vuecal__title-bar {
  background-color: #e4f5ef;
}
.business-hours {
  background-color: rgba(255, 255, 0, 0.2);
  border: solid rgba(255, 210, 0, 0.6);
  border-width: 2px 0;
}
.aa{
  background-color: palevioletred;
  color:red;
}
/* .vuecal__now-line{
  color: #06c;
} */
.vuecal__event.leisure {background-color: rgba(253, 156, 66, 0.9);border: 1px solid rgb(233, 136, 46);color: #fff;}
.vuecal__event.sport {background-color: rgba(255, 102, 102, 0.9);border: 1px solid rgb(235, 82, 82);color: #fff;}
</style>