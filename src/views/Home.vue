<template>
  <div class="home">
    <!-- <Demo /> -->
    <HelloTitle />
    <HelloContent :formatDate="newsList" />
    <HelloChina :formatDate="newsList"/>
  </div>
</template>

<script>
import HelloTitle from "./HelloTitle/HelloTitle";
import HelloContent from "./HelloContent/HelloContent";
import HelloChina from "./HelloChina/HelloChina";
// import Demo from "./Demo/Demo";
export default {
  name: "home",
  components: {
    HelloTitle: HelloTitle,
    HelloContent: HelloContent,
    HelloChina: HelloChina,
    // Demo: Demo
  },
  data() {
    return {
      newsList: {}
    };
  },
  methods: {
    ceshi: function() {
      this.axios
        .get("https://lab.isaaclin.cn/nCoV/api/overall")
        .then(response => {
          //console.log(response);
          this.newsList = response.data.results[0];
        })
        .catch(response => {
          console.log(response);
        });
    }
  },
  mounted() {
    this.ceshi();
  }
};
</script>
