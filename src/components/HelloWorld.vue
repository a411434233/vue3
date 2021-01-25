<template>
  <div class="hello">
    {{ msg }}
    <button @click="addreac">reac</button>
  </div>
</template>

<script>
import {computed, onMounted, reactive, ref, watch} from 'vue'

export default {
  name: 'HelloWorld',
  props: {
    msg: {
      type: Number,
      default: 1
    },
    setMsg: Function
  },
  setup(props, {emit}) {
    let num = ref(0);
    let reac = reactive({a: 1})
    let addNum = () => num.value++;

    function addreac() {
      reac.a += 1;
    }

    watch([reac, num, props], (([reac, num, props], [, , Oldprops]) => {
      console.log(props.msg, Oldprops)
    }))

    let num2 = computed(() => num.value + 1)

    onMounted(() => {
      console.log('onMounted')
    })
    return {num, addNum, num2, reac, addreac,}
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
