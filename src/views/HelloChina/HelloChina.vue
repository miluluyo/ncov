<template>
  <div class="">
    <div id="myChart" style="height: 350px"></div>
  </div>
</template>
<script type="text/javascript">
import "../../assets/china2";
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
      allList: [],
      datalist: [],
      province: ['湖北', '广东', '浙江', '湖南', '河南', '安徽', '重庆', '山东', '江西', '四川', '江苏', '北京', '福建', '上海', '广西', '河北', '陕西', '云南', '海南', '黑龙江', '辽宁', '山西', '天津', '甘肃', '内蒙古', '新疆', '宁夏', '吉林', '贵州', '青海', '西藏', '澳门', '香港', '台湾']
    }
  },
  methods: {
    getList() {
      this.axios
        .get("https://lab.isaaclin.cn/nCoV/api/area?latest=1")
        .then(response => {
          this.allList = response.data.results;
          //console.log(this.allList);
          let provinceAll = this.province
          for (var i = 0; i < provinceAll.length; i++) {
            //console.log(this.allList[i].provinceShortName)
            let b = this.allList;
            let r = b.filter(function(a) {
              return a.provinceShortName == provinceAll[i];
            });
            //console.log(r[0].provinceShortName,r[0].confirmedCount)
            var obj = {};
            obj.name = r[0].provinceShortName;
            obj.value = r[0].confirmedCount;
            this.datalist.push(obj);
            console.log('{ name: "'+r[0].provinceShortName+'", value: '+r[0].confirmedCount+' },');
          }
          //console.log(this.datalist)
          this.drawLine();
          window.onresize = () => {
            this.myChart.resize();
          };
        })
        .catch(response => {
          console.log(response);
        });
    },
    drawLine(){// 基于准备好的dom，初始化echarts实例
      let myChart = this.$echarts.init(document.getElementById('myChart'))
      // 绘制图表
      myChart.setOption({
        title: {
          //text: 'USA Population Estimates (2012)',
          //subtext: 'Data from www.census.gov',
          //sublink: 'http://www.census.gov/popest/data/datasets.html',
          //left: 'right'
        },
        tooltip: {
          trigger: "item",
          showDelay: 0,
          transitionDuration: 0.2,
          formatter: function(params) {
            var value = (params.value + "").split(".");
            value = value[0].replace(/(\d{1,3})(?=(?:\d{3})+(?!\d))/g, '$1,');
            return params.seriesName + "<br/>" + params.name + ": " + value;
          }
        },
        visualMap: {
          min: 0,
          max: 10000,
          left: 13,
          bottom: 0,
          showLabel: !0,
          itemWidth: 10,
          itemHeight: 20,
          textGap: 5,
          itemGap: 0,
          itemSymbol: "none",
          pieces: [
            {
              gt: 10000,
              label: "10000人及以上",
              color: "#7f1100",
              symbol: "rect"

            }, {
              gte: 1000,
              lte: 9999,
              label: "1000 - 9999 人",
              color: "#ff5428",
              symbol: "rect"
            }, {
              gte: 100,
              lt: 999,
              label: "100 - 999 人",
              color: "#ff8c71",
              symbol: "rect"
            }, {
              gte: 10,
              lt: 99,
              label: "10 - 99 人",
              color: "#FFB2A2",
              symbol: "rect"
            }, {
              gt: 0,
              lt: 9,
              label: "1 - 9 人",
              color: "#ffd768",
              symbol: "rect"
            }],
          show: !0
        },
        toolbox: {
          show: true,
          //orient: 'vertical',
          left: 'left',
          top: 'top',
          feature: {
            // dataView: {readOnly: false},
            // restore: {},
            // saveAsImage: {}
          }
        },
        geo: {
          map: "china",
          roam: !1,
          scaleLimit: {
            min: 1,
            max: 2
          },
          zoom: 1.23,
          top: 40,
          label: {
            normal: {
              show: !0,
              fontSize: 8,
              color: "#4B4B4B"
            }
          },
          itemStyle: {
            normal: {
              //shadowBlur: 50,
              //shadowColor: 'rgba(0, 0, 0, 0.2)',
              borderColor: "rgba(0, 0, 0, 0.2)"
            },
            emphasis: {
              areaColor: "#f2d5ad",
              shadowOffsetX: 0,
              shadowOffsetY: 0,
              borderWidth: 0
            }
          }
        },
        series: [
          {
            name: "确诊病例",
            type: 'map',
            mapType: 'china',
            geoIndex: 0,
            itemStyle: {
              normal: { label: { show: true } },
              emphasis: { label: { show: true } }
            }, 
            label: {
              show: true,
              normal:{
                fontSize: 8,
                color: "#4B4B4B"
              }
            },
            data: this.datalist
          }
        ]
      });
      window.addEventListener("resize", () => {
        myChart.resize();
      });
    }
  },
  mounted() {
    this.getList();
    //console.log(this.formatDate);
    
  }
};
</script>

<style lang="scss" scoped>

</style>
