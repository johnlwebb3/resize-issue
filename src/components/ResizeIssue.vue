<template>
  <div>
      <v-app-bar v-resize="onResize">
          screenSize : {{screenSize}}
      </v-app-bar>
  </div>
</template>

<script>
export default {
 methods:{
        onResize(){
            console.log('screensize : '+ this.$vuetify.breakpoint.name)
            this.windowSize = { x: window.innerWidth, y: window.innerHeight };
            this.$data.screenSize=this.$vuetify.breakpoint.name;
        },
      },
    data: () => ({
      windowSize: {
        x: 0,
        y: 0,
      },
    screenSize:'',



    })
}
</script>

<style>

</style>