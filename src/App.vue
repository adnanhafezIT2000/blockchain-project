<script lang="ts">
import '@/style/style.css';
import ShowLastBlockNumber from './components/ShowLastBlockNumber.vue';
import ShowUSDT from './components/ShowUSDT.vue';
export default {
    components:{
        ShowLastBlockNumber ,
        ShowUSDT
    }
}
</script>

<template>
    <div id="app">
        <h1> Welcome To My Ethereum Project ! </h1>

        <ShowLastBlockNumber />

        <ShowUSDT />
    </div>
    <router-view/>
</template>