<template>
  <div class="">
    <div class="DataDetail">
      截至 {{ formatDate.updateTime | changeDate }} 全国数据统计
    </div>
    <div class="nCovDataList">
      <el-row>
        <el-col :span="6">
          <div class="nCovDataBox">
            <div class="nCovDataBoxNum">
              {{ formatDate.confirmedCount }}
            </div>
            <div class="nCovDataBoxText">
              全国确诊
            </div>
          </div>
        </el-col>
        <el-col :span="6">
          <div class="nCovDataBox">
            <div class="nCovDataBoxNum">
              {{ formatDate.suspectedCount }}
            </div>
            <div class="nCovDataBoxText">
              疑似感染
            </div>
          </div>
        </el-col>
        <el-col :span="6">
          <div class="nCovDataBox">
            <div class="nCovDataBoxNum">
              {{ formatDate.curedCount }}
            </div>
            <div class="nCovDataBoxText">
              死亡
            </div>
          </div>
        </el-col>
        <el-col :span="6">
          <div class="nCovDataBox">
            <div class="nCovDataBoxNum">
              {{ formatDate.deadCount }}
            </div>
            <div class="nCovDataBoxText">
              治愈
            </div>
          </div>
        </el-col>
    </el-row>
    </div>
    







  </div>
</template>

<script type="text/javascript">
export default {
  props: {
    formatDate: {
      type: Object,
      // eslint-disable-next-line vue/require-valid-default-prop
      default: {}
    }
  },
  data() {
    return {

    }
  },
  filters: {
    changeDate: function (value) {
      let date = new Date(value);
      let y = date.getFullYear();
      let MM = date.getMonth() + 1;
      MM = MM < 10 ? "0" + MM : MM;
      let d = date.getDate();
      d = d < 10 ? "0" + d : d;
      let h = date.getHours();
      h = h < 10 ? "0" + h : h;
      let m = date.getMinutes();
      m = m < 10 ? "0" + m : m;
      let s = date.getSeconds();
      s = s < 10 ? "0" + s : s;
      return y + "-" + MM + "-" + d + " " + h + ":" + m + ":" + s;
    }
  },
  methods: {
  },
  mounted() {
    console.log(this.formatDate);
  }
}
</script>

<style lang="scss" scoped>
.DataDetail {
  font-size: 0.75rem;
  margin-top: 1rem;
  padding: 0 1rem;
  color: #666
}
.nCovDataList {
  padding: 1rem;
  text-align: center;
  font-weight: bolder;
}
.nCovDataBox {
  border-right: 1px solid #ccc
}
.nCovDataList .el-col-6:nth-child(4) .nCovDataBox {
  border-right: none;
}
.nCovDataBoxNum {
  font-size: 1.25rem;
}
.nCovDataBoxText {
  font-size: 0.75rem;
}
.nCovDataList .el-col-6:nth-child(1) .nCovDataBoxNum {
  color:rgb(247, 76, 49)
}
.nCovDataList .el-col-6:nth-child(2) .nCovDataBoxNum {
  color:rgb(247, 130, 7)
}
.nCovDataList .el-col-6:nth-child(3) .nCovDataBoxNum {
  color:rgb(93, 112, 146)
}
.nCovDataList .el-col-6:nth-child(4) .nCovDataBoxNum {
  color:rgb(40, 183, 163)
}

</style>
