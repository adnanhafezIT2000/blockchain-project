<script lang="ts">
import { ref , Ref } from 'vue';
export default {
    setup(){
        const URL = 'https://mainnet.infura.io/v3/abb35a920100470aab875b663b86ee0a';
        const ethers = require('ethers');
        const provider = new ethers.JsonRpcProvider(URL);

        let blockNumber: Ref<string|number> = ref('please, click the button to show last block number');

        const getLastBlockNumber = async () =>{
            
            const number = await provider.getBlockNumber();
            blockNumber.value = `last block number is ${number}`; 
        }

        return{
            getLastBlockNumber ,
            blockNumber
        }
    }
}
</script>

<template>
    <div class="show-block-number">
        <button @click="getLastBlockNumber()"> get last block number </button>
        <div class="show-content">
            <span> {{blockNumber}} </span>
        </div>
    </div>
</template>