<script context="module" lang="ts">

import { ethers  } from "ethers"

const address = "https://mainnet.infura.io/v3/e1aade92033b42248602538528da8cce"
const provider = new ethers.providers.JsonRpcProvider(address)

const ABI = [
	{
		"inputs": [],
		"name": "getMood",
		"outputs": [
			{
				"internalType": "string",
				"name": "",
				"type": "string"
			}
		],
		"stateMutability": "view",
		"type": "function"
	},
	{
		"inputs": [
			{
				"internalType": "string",
				"name": "_mood",
				"type": "string"
			}
		],
		"name": "setMood",
		"outputs": [],
		"stateMutability": "nonpayable",
		"type": "function"
	}
]
const contractaddr = "0x27983fb9dd301714eA5025e90D01c1aDBceF01FF"

const contract = new ethers.Contract(contractaddr, ABI, provider)

let inputval = ""
let mood:string;

const setMood = () => {

}
const getMood = async () => {
    mood = await contract.getMood()
    console.log(mood)
}

    


</script>

<main class="h-screen w-screen bg-slate-700">
    <nav class="py-12 w-full flex flex-row justify-center items-center">
        <h1 class="p-2 text-6xl font-semibold text-transparent bg-clip-text bg-gradient-to-br from-blue-500 to-pink-500">Moodgetter</h1>
    </nav>
    <section class="flex flex-col items-center">
        <button on:click={() => getMood()} class="py-3 px-8 mb-16 w-40 bg-gradient-to-br from-purple-500 to-pink-500 rounded-xl text-xl font-semibold text-white transition ease-in-out duration-300 hover:-translate-y-1 hover:shadow-md hover:shadow-purple-500/50">Get Mood</button>
        <form class="flex flex-col " action="">
            <input bind:value={inputval} type="text" placeholder="Your mood" class="text-center outline-none border-b-2 border-white/25 bg-transparent text-slate-300 transition ease-in-out hover:scale-125 hover:border-white/50 focus:border-white/50 focus:scale-125">
            <button class="py-3 px-8 mt-16 mx-auto w-40 bg-gradient-to-tr from-orange-500 to-pink-500 rounded-xl text-xl font-semibold text-white transition ease-in-out duration-300 hover:-translate-y-1 hover:shadow-md hover:shadow-pink-500/50">Set Mood</button>

        </form>
        {#if mood}
        {mood}    
        {/if}
    </section>
</main>