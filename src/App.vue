<!--
 * @Descripttion: 
 * @version: 
 * @Author: wrh
 * @Date: 2020-10-31 12:27:34
 * @LastEditors: wrh
 * @LastEditTime: 2020-10-31 15:11:33
-->
<template>
<div v-for="(item,index) in products" :key="item" @click="selectProductFun(index)">{{item}}</div>
<div>{{product}}</div>
</template>

<script lang="ts">
import {
  ref,
  reactive,
  toRefs
} from 'vue'
import {
  createLogger
} from 'vuex'

interface DataProps {
  products: string[];
  product: string;
  selectProductFun: (index: number) => void
}
export default {
  name: 'App',
  setup() {
    // const products = ref([
    //   '瓜子',
    //   '矿泉水',
    //   '八宝粥',
    //   '脚收一下'
    // ])

    // const product = ref('未选择')

    // const selectProductFun = (index) => {
    //   product.value = products.value[index]
    // }
    let data: DataProps = reactive({
      products: [
        '可乐',
        '瓜子',
        '矿泉水',
        '八宝粥',
        '脚收一下'
      ],
      product: '未选择',
      selectProductFun(index: number) {
        console.log(index)
        data.product = data.products[index]
      }
    })
    const refData = toRefs(data)

    return {
      // products,
      // product,
      // selectProductFun
      ...refData
    }
  },

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
