<template>
  <div class="head" id="main">
    <div class="nCovText">
      <div class="nCovLogo"><i class="el-icon-sunny"></i> 武汉加油！</div>
      <div class="nCovTitle">新型冠状病毒肺炎</div>
      <div class="nCovCon"><i class="el-icon-aim"></i>疫情实时追踪</div>
      <div class="nCovExplain">数据来源：国家及各地卫健委每日信息发布</div>
    </div>
  </div>
</template>

<script type="text/javascript">
export default {
  data() {
    return {

    }
  },
  components: {

  }
}
</script>

<style lang="scss" scoped>
#main {
  width: 100%;
  height: 180px;
  overflow: hidden;
}
.nCovText {
  color: #ffffff;
  padding: 2rem 1rem;
}
.nCovTitle {
  font-size: 1rem;
  padding: 0.25rem 1rem;
  background:rgba(225,225,225,0.5);
  display: inline-block;
  border-radius: 1rem;
  margin: 0.5rem 0;
}
.nCovCon {
  font-style: oblique;
  font-size: 1.5rem;
}
.nCovExplain {
  display: flex;
  justify-content: space-between;
  line-height: 1rem;
  height: 1rem;
  font-size: 0.75rem;
  color: #fff;
  position: absolute;
  left: 1rem;
  right: 1rem;
  bottom: 1rem;
}
#main {
  background-image: url(https://img1.dxycdn.com/2020/0125/819/3392881515137832451-21.png!w720);
  background-position: right;
  background-size: 55%;
  background-repeat: no-repeat;
  background-color: #0C0F17;
}
</style>
