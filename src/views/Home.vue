<template>
  <div class="home">
    {{ msg }}
    <HelloWorld :msg.sync="msg" @seeked="setMsg"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import {ref} from "vue";

export default {
  name: 'Home',
  components: {
    HelloWorld
  },
  setup() {
    let msg = ref(1);

    function setMsg() {
      msg.value += 1
    }

    return {msg, setMsg}
  }

}
</script>
