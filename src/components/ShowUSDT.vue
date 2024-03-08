<script lang="ts">
import { ref } from 'vue';

export default {
    setup(){
        const URL = 'https://mainnet.infura.io/v3/abb35a920100470aab875b663b86ee0a';
        const ethers = require('ethers');
        const provider = new ethers.JsonRpcProvider(URL);

        let address = ref('');
        let result = ref('');
        let resultformatted = ref('');

        const getUSDT = async () =>{

            const balance = await provider.getBalance(address.value);
            const formattedBalance = ethers.formatEther(balance);
            
            result.value = `Ether Balance Is (${balance})`;
            resultformatted.value = `Ether Formatted Balance Is (${formattedBalance})`;

        }

        return{
            address ,
            getUSDT ,
            result ,
            resultformatted
        }
    }
}
</script>

<template>
    <div class="show-USDT">
        <h4> Show (USDT) balance to any address </h4>
        <form @submit.prevent="getUSDT">
            <input type="text" v-model="address" placeholder="Enter address" required>
            <button type="submit">get USDT</button>
        </form>
        <div class="USDT-result">
            <p> {{result}} </p> 
            <br>
            <p> {{resultformatted}} </p>
        </div>
    </div>
</template>