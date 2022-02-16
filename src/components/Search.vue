<template>
  <v-text-field
    label="Location"
    persistent-hint
    outlined
    class="ma-2"
    v-model="location"
    @keyup.enter="$emit('loc-set', location)"
  ></v-text-field>
</template>

<script>
export default {
    name:"Search",
    data() {
        return{
            location:''
        }
    },
    watch:{
        location(){
            console.log(this.location)
        }
    }
}
</script>
