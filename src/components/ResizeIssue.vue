<template>
  <div>
      <v-app-bar class="ma-15" v-resize="onResize">
          screenSize : {{screenSize}} windowSize.x : {{windowSize.x}} computedSize : {{computedScreenSize}}
      </v-app-bar>
  </div>
</template>

<script>
export default {
 mounted: function () {
    window.addEventListener("resize", this.doSomething); // ---------------------,
  },                                                     //                      | 
computed:{                                               //                      |  
  computedScreenSize:{                                   //                      |  
            // using this instead coupled with a "resize" event listener  <------'
             get(){
               if(this.$data.windowSize.x<600) return 'xs';
               else if(this.$data.windowSize.x<960) return 'sm';
               else if(this.$data.windowSize.x<1264) return 'md';
               else if(this.$data.windowSize.x<1904) return 'lg';
               else return 'xl';
             }
          
        },
},   
 methods:{
        onResize(){
          // this.$vuetify.breakpoint.name does not seem to be able to reliably calculate the breakpoint size of the screen
          // Maximizing and normalizing the window confuses it
          // also, making a significant screen size change, i.e. skip over a size in the middle and it gets confused
            console.log('screensize : '+ this.$vuetify.breakpoint.name) 
            this.windowSize = { x: window.innerWidth, y: window.innerHeight };
            this.$data.screenSize=this.$vuetify.breakpoint.name;
        },
        doSomething(){
          this.windowSize = { x: window.innerWidth, y: window.innerHeight }
          console.log(this.$vuetify.breakpoint.name);
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