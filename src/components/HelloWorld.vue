<template>
  <div class="hello">
    <h1>{{ currentCount }}</h1>
    <button v-on:click="incrementCount">Add</button>
    <h1>New current count: {{ currentCount2 }}</h1>
    <button v-on:click="incrementCount2">Add</button>
    <h1>Third new current count: {{ currentCount3 }}</h1>
    <button v-on:click="incrementCount3">Add</button>
  </div>
</template>

<script>
import { reactive, ref, toRefs } from 'vue'
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  data: () => ({
    currentCount: 0,
  }),
  methods: {
    incrementCount() {
      this.currentCount++
    },
  },
  setup() {
    const state = reactive({
      currentCount2: 12,
    })
    const incrementCount2 = () => {
      state.currentCount2++
    }
    const currentCount3 = ref(15)
    const incrementCount3 = () => {
      currentCount3.value++
    }
    return {
      ...toRefs(state),
      incrementCount2,
      currentCount3,
      incrementCount3,
    }
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
