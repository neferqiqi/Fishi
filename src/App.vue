<template>
  <div class="home">
    <NInput
      v-model:value="url"
      class="url-input"
      placeholder="请输入网址"
      @keydown.enter="load"
      ></NInput>
      <webview 
      v-if="showWebview"
      :src="webUrl" 
      class="main-frame"
      partition="persist:webview"
    ></webview>
  </div>
</template>
  
<script setup>
import { NInput } from 'naive-ui'
import { onMounted, ref } from 'vue';

const url = ref('https://')

const webUrl = ref('')
const showWebview = ref(false)

const load = () => {
  console.log('load', url.value)
  webUrl.value = url.value;
  showWebview.value = true; // 显示webview
}

onMounted(() => {
  console.log(url.value)
})

</script>
<style scoped>
.home {
  width: 100%;
}
  .url-input {
    width: 100%;
    margin-bottom: 10px;
  }
  .main-frame {
    width: 100%;
    height: calc(100vh - 50px); /* 减去顶部导航栏的高度 */
    border: none;
    overflow: auto;
  }
  </style>