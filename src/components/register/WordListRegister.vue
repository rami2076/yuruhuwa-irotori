<script setup lang="ts">

import {ref} from "vue";

// reactive 要素になった。
const isUseDefaultWordList = ref<boolean>(false);


</script>


<!--v3からはDOMを複数おけるようになった！-->
<template>

    <div>
        <p>デフォルト単語一覧を使用する</p>
        <input type="checkbox" v-model="isUseDefaultWordList">
        <p>テストパターン2</p>
        <input type="checkbox" :checked="isUseDefaultWordList" @change="isUseDefaultWordList=!isUseDefaultWordList">
        <p>テストパターン3</p>
        <input type="checkbox" checked="checked">
    </div>

</template>
