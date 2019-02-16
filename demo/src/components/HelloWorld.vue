<template>
<div class="hello">
    <h1>点开图片2秒后自动关闭</h1>
    <img src="..//assets/logo.png" preview="0" preview-text="描述文字">
  </div>
</template>

<script>
import Vue from 'vue';
var options = {
    fullscreenEl: false //关闭全屏按钮
}

import preview from 'vue-photo-preview'
import 'vue-photo-preview/dist/skin.css'
Vue.use(preview)
Vue.use(vuePhotoPreview, options);

export default {
    name: 'HelloWorld',
    data() {
        return {
            msg: 'Welcome to Your Vue.js App'
        }
    },
    mounted() {
        this.$preview.on('imageLoadComplete', (e, item) => {
            console.log(this.$preview.self) //此时this.$preview.self拥有原插件photoswipe文档中的所有>方法和属性
            setTimeout(() => {
                this.$preview.self.close();
            }, 2000);
        });
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
h1,
h2 {
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
