<template>
  <h1>{{ message }}</h1>
  <HelloWorld />
  만약 error가 발생한다면 vuejs의 2버전에 해당하는 error인데 3버전인데 이 error가 발생하는 이유는 eslint가 연결이 되어 있지 않아서 발생함.
  terminal에서 npm i -D eslint eslint-plugin-vue babel-eslint 입력
</template>

<script>
import HelloWorld from '~/components/HelloWorld.vue'
export default {
    components: {
        HelloWorld
    },
    data() {
        return {
            message: 'Hello Vue!!!'
        }
    }
}
</script>