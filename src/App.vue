<script>
import Search from "./components/Search.vue";
import Current from "./components/Current.vue";
export default {
  name: "App",

  components: {
    Search,
    Current
  },

  data(){
    return {
      location:""
    }
  },
  methods:{
    locationSet(loc){
      console.log(loc)
      this.location = loc
    }
  }
};
</script>


<template>
  <v-app>
    <v-main>
      <Search @loc-set="locationSet"/>
      <Current :location="location" />
      <!-- <HelloWold/> -->
    </v-main>
  </v-app>
</template>

<style scoped>
.v-main {
  font-family: Roboto, Menlo, Monaco, Consolas, "Courier New",
    monospace;
    
   
}
</style>