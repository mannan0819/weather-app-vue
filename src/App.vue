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
      <!-- <HelloWorld/> -->
    </v-main>
  </v-app>
</template>