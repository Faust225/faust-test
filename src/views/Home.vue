<template>
<!-- 
  good example to study basics
  https://medium.com/js-dojo/getting-your-head-around-vue-js-scoped-slots-281bf82a1e4e
  
  ES decorator
  https://www.youtube.com/watch?v=Pp_fPANxxio

  vueEx

  Axios
    https://medium.com/js-dojo/yet-another-pattern-for-api-calls-using-vuejs-vuex-b22ecdfb0ea2

    Good basic vue js and axios
    https://developer.school/how-to-use-vue-js-json-server-and-axios/

    Getting started
    https://medium.com/codingthesmartway-com-blog/getting-started-with-axios-166cb0035237

  middlewares???

  JSON server
  https://www.npmjs.com/package/json-server

  Mongo
  https://www.freecodecamp.org/news/learn-mongodb-a4ce205e7739/

  Cloud Mongo video getting started
  https://www.youtube.com/watch?v=Ed61W_jenDw

  Node
  https://www.youtube.com/watch?v=qQwcCS8K_K0
 -->
  <div class="home">
    <input v-model="name">
    <a href="javascript:" @click="addElement">ADD</a>
  </div>
</template>
<script>

// @ === /src
import data from "@/services/data.js";

export default {
  name: "home",
  data() {
    return {
      name: ""
    };
  },
  // makes method
    methods: {
    addElement() {
      if(this.name != "") {
        data.dataArray.push(this.name);
      }
    }
  }
};
</script>
