<template>
  <div class>
     <group title="用户登录">
      <x-input title="手机号" mask="999 9999 9999" v-model="phone" :max="13" is-type="china-mobile"></x-input>
     <x-input title="请输入密码" type="password"  v-model="password" :min="6" :max="6"></x-input>
    </group>
    <div class="btn" >
        <x-button @on-change="login">登录</x-button>
     </div>
  </div>
</template>
<script>
import { XInput, Group, XButton, Cell } from 'vux'
export default {
  components: {
    XInput,
    XButton,
    Group,
    Cell
  },
  data () {
    return {
      phone: '',
      password: ''
    }
  }
}
</script>

<style scoped>
h1, h2 {
  font-weight: normal;
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
