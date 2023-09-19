<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    <Test msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import Test from '@/views/TestView.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld,
    Test
  },
  data(){
    return{
      placeHolderStr:'请输入名字'
    }
  }
}
</script>
