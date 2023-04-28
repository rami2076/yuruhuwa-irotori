<script setup lang="ts">

import {ref} from "vue";

// reactive 要素になった。
const isUseDefaultWordList = ref<boolean>(false);
const wordListFile = ref<any>();

async function submit() {
    const file = wordListFile.value.files[0];

    const headers = new Headers({})

    const sampleObject = { //JSONにするオブジェクト
        isUseDefaultWordList: isUseDefaultWordList.value
    }

    const body = new FormData()
    body.append('file', file)
    body.append('jsonValue', new Blob([JSON.stringify(sampleObject)], {type: 'application/json'}))

    const data: RequestInit = {
        method: 'POST',
        body,
        headers
    }
    await fetch('http://localhost:8080/upload', data)

}

</script>


<!--v3からはDOMを複数おけるようになった！-->
<template>

    <div>
        <p>デフォルト単語一覧を使用する</p>
        <input type="checkbox" v-model="isUseDefaultWordList">
        <p>単語一覧ファイル </p>
        <input type="file" ref="wordListFile">

        <button @click="submit">送信</button>

    </div>

</template>
