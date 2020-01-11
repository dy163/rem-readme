<template>
  <div class="chart">
      <van-row>
        <van-col span="6" @click="handleBranch" id="branch">分时</van-col>
        <van-col span="6" @click="handleDaily" id="daily">日k</van-col>
        <van-col span="6" @click="handleWeek" id="week">周k</van-col>
        <van-col span="6" @click="handleMonth" id="month">月k</van-col>
      </van-row>
      <Branch v-if="branch"/>
      <Daily v-if="daily"/>
      <Week v-if="week"/>
      <Month v-if="month"/>
  </div>
</template>

<script>
import Branch from "./branch"
import Daily from "./daily"
import Week from "./week"
import Month from "./month"

export default {
  name: "Chart",
  components: {
    Branch,
    Daily,
    Week,
    Month
  },
  props: {},
  data() {
    return {
      branch: true,
      daily:false,
      week:false,
      month:false,
    };
  },
  methods: {
    /** 
     * 分
     */
    handleBranch () {
      this.branch = true
      this.daily = false
      this.week = false
      this.month = false
      document.getElementById('branch').style.color = '#2F98FF'
      document.getElementById('daily').style.color = '#7f819b'
      document.getElementById('week').style.color = '#7f819b'
      document.getElementById('month').style.color = '#7f819b'
    },
    /**
     * 日
     */
    handleDaily () {
      this.branch = false
      this.daily = true
      this.week = false
      this.month = false
      document.getElementById('daily').style.color = '#2F98FF'
      document.getElementById('branch').style.color = '#7f819b'
      document.getElementById('week').style.color = '#7f819b'
      document.getElementById('month').style.color = '#7f819b'
    },
    /**
     * 周
     */
    handleWeek () {
      this.daily = false
      this.branch = false
      this.week = true
      this.month = false
      document.getElementById('daily').style.color = '#7f819b'
      document.getElementById('branch').style.color = '#7f819b'
      document.getElementById('week').style.color = '#2F98FF'
      document.getElementById('month').style.color = '#7f819b'
    },
    /**
     * 月
     */
    handleMonth () {
      this.daily = false
      this.branch = false
      this.week = false
      this.month = true
      document.getElementById('daily').style.color = '#7f819b'
      document.getElementById('branch').style.color = '#7f819b'
      document.getElementById('week').style.color = '#7f819b'
      document.getElementById('month').style.color = '#2F98FF'
    }

  },
};
</script>
<style lang='less' scoped>
  .van-row {
    height: 43px;
    line-height: 43px;
    font-size: 14px;
    color:#7f819b;;
    text-align: center;
    #branch {
      color: #2F98FF;
    }
  }

</style>