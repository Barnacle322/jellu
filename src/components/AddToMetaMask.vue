<script setup>
import { ref } from 'vue'

const isAdding = ref(false)
const showSuccess = ref(false)
const errorMessage = ref('')

const addSomniaNetwork = async () => {
    // Check if MetaMask is installed
    if (!window.ethereum) {
        errorMessage.value = 'MetaMask is not installed!'
        setTimeout(() => {
            errorMessage.value = ''
        }, 3000)
        return
    }

    isAdding.value = true
    errorMessage.value = ''

    try {
        // Get MetaMask provider specifically
        let provider = window.ethereum

        // If multiple wallets are installed, find MetaMask
        if (window.ethereum.providers?.length) {
            provider = window.ethereum.providers.find((p) => p.isMetaMask)
            if (!provider) {
                throw new Error('MetaMask is not installed!')
            }
        } else if (!window.ethereum.isMetaMask) {
            // If only one provider and it's not MetaMask
            errorMessage.value = 'Please use MetaMask wallet'
            setTimeout(() => {
                errorMessage.value = ''
            }, 3000)
            isAdding.value = false
            return
        }

        await provider.request({
            method: 'wallet_addEthereumChain',
            params: [
                {
                    chainId: '0x13a7', // 5031 in decimal
                    chainName: 'Somnia Mainnet',
                    nativeCurrency: {
                        name: 'Somnia Token',
                        symbol: 'SOMI',
                        decimals: 18,
                    },
                    rpcUrls: ['https://api.infra.mainnet.somnia.network'],
                    blockExplorerUrls: ['https://explorer.somnia.network'],
                },
            ],
        })

        showSuccess.value = true
        setTimeout(() => {
            showSuccess.value = false
        }, 3000)
    } catch (error) {
        console.error('Error adding network:', error)
        errorMessage.value = error.message || 'Failed to add network'
        setTimeout(() => {
            errorMessage.value = ''
        }, 3000)
    } finally {
        isAdding.value = false
    }
}
</script>

<template>
    <div class="fixed top-6 left-1/2 -translate-x-1/2 z-50 flex flex-col items-center gap-3">
        <button
            @click="addSomniaNetwork"
            :disabled="isAdding"
            class="group bg-white/10 backdrop-blur-sm hover:bg-white/20 border border-white/20 text-white font-bold py-3 px-6 rounded-full transition-all duration-200 flex items-center gap-3 disabled:opacity-50 disabled:cursor-not-allowed hover:border-white/40"
        >
            <svg class="w-5 h-5" viewBox="0 0 212 189" xmlns="http://www.w3.org/2000/svg">
                <g fill="none" fill-rule="evenodd">
                    <polygon
                        fill="#CDBDB2"
                        points="60.75 173.25 88.313 180.563 88.313 171 90.563 168.75 106.313 168.75 106.313 180 106.313 187.875 89.438 179.438 68.625 176.625"
                    />
                    <polygon
                        fill="#CDBDB2"
                        points="105.75 173.25 132.75 180.563 132.75 171 135 168.75 150.75 168.75 150.75 180 150.75 187.875 133.875 179.438 113.063 176.625"
                        transform="matrix(-1 0 0 1 256.5 0)"
                    />
                    <polygon
                        fill="#393939"
                        points="90.563 152.438 88.313 171 91.125 168.75 120.375 168.75 123.75 171 121.5 152.438 117 149.625 94.5 149.625"
                    />
                    <polygon
                        fill="#F89C35"
                        points="75.375 27 88.875 58.5 95.063 150.188 117 150.188 123.75 58.5 136.125 27"
                    />
                    <polygon
                        fill="#F89D35"
                        points="16.313 96.188 .563 141.75 39.938 139.5 65.25 139.5 65.25 119.813 64.125 79.313 58.5 83.813"
                    />
                    <polygon
                        fill="#D87C30"
                        points="46.125 101.25 92.25 102.375 87.188 126 65.25 120.375"
                    />
                    <polygon fill="#EA8D3A" points="46.125 101.813 65.25 119.813 65.25 137.813" />
                    <polygon
                        fill="#F89D35"
                        points="65.25 120.375 87.75 126 95.063 150.188 90 153 65.25 138.375"
                    />
                    <polygon fill="#EB8F35" points="65.25 138.375 60.75 173.25 90.563 152.438" />
                    <polygon fill="#EA8E3A" points="92.25 102.375 95.063 150.188 86.625 125.719" />
                    <polygon fill="#D87C30" points="39.375 138.938 65.25 138.375 60.75 173.25" />
                    <polygon
                        fill="#EB8F35"
                        points="12.938 188.438 60.75 173.25 39.375 138.938 .563 141.75"
                    />
                    <polygon
                        fill="#E8821E"
                        points="88.875 58.5 64.688 78.75 46.125 101.25 92.25 102.938"
                    />
                    <polygon
                        fill="#DFCEC3"
                        points="60.75 173.25 90.563 152.438 88.313 170.438 88.313 180.563 68.063 176.625"
                    />
                    <polygon
                        fill="#DFCEC3"
                        points="121.5 173.25 150.75 152.438 148.5 170.438 148.5 180.563 128.25 176.625"
                        transform="matrix(-1 0 0 1 272.25 0)"
                    />
                    <polygon
                        fill="#393939"
                        points="70.313 112.5 64.125 125.438 86.063 119.813"
                        transform="matrix(-1 0 0 1 150.188 0)"
                    />
                    <polygon fill="#E88F35" points="12.375 .563 88.875 58.5 75.938 27" />
                    <path
                        fill="#8E5A30"
                        d="M12.3750002,0.562500008 L2.25000003,31.5000005 L7.87500012,65.250001 L3.93750006,67.500001 L9.56250014,72.5625 L5.06250008,76.5000011 L11.25,82.1250012 L7.31250011,85.5000013 L16.3125002,96.7500014 L58.5000009,83.8125012 C79.1250012,67.3125004 89.2500013,58.8750003 88.8750013,58.5000009 C88.5000013,58.1250009 63.0000009,38.8125006 12.3750002,0.562500008 Z"
                    />
                    <g transform="matrix(-1 0 0 1 211.5 0)">
                        <polygon
                            fill="#F89D35"
                            points="16.313 96.188 .563 141.75 39.938 139.5 65.25 139.5 65.25 119.813 64.125 79.313 58.5 83.813"
                        />
                        <polygon
                            fill="#D87C30"
                            points="46.125 101.25 92.25 102.375 87.188 126 65.25 120.375"
                        />
                        <polygon
                            fill="#EA8D3A"
                            points="46.125 101.813 65.25 119.813 65.25 137.813"
                        />
                        <polygon
                            fill="#F89D35"
                            points="65.25 120.375 87.75 126 95.063 150.188 90 153 65.25 138.375"
                        />
                        <polygon fill="#EB8F35" points="65.25 138.375 60.75 173.25 90 153" />
                        <polygon
                            fill="#EA8E3A"
                            points="92.25 102.375 95.063 150.188 86.625 125.719"
                        />
                        <polygon
                            fill="#D87C30"
                            points="39.375 138.938 65.25 138.375 60.75 173.25"
                        />
                        <polygon
                            fill="#EB8F35"
                            points="12.938 188.438 60.75 173.25 39.375 138.938 .563 141.75"
                        />
                        <polygon
                            fill="#E8821E"
                            points="88.875 58.5 64.688 78.75 46.125 101.25 92.25 102.938"
                        />
                        <polygon
                            fill="#393939"
                            points="70.313 112.5 64.125 125.438 86.063 119.813"
                            transform="matrix(-1 0 0 1 150.188 0)"
                        />
                        <polygon fill="#E88F35" points="12.375 .563 88.875 58.5 75.938 27" />
                        <path
                            fill="#8E5A30"
                            d="M12.3750002,0.562500008 L2.25000003,31.5000005 L7.87500012,65.250001 L3.93750006,67.500001 L9.56250014,72.5625 L5.06250008,76.5000011 L11.25,82.1250012 L7.31250011,85.5000013 L16.3125002,96.7500014 L58.5000009,83.8125012 C79.1250012,67.3125004 89.2500013,58.8750003 88.8750013,58.5000009 C88.5000013,58.1250009 63.0000009,38.8125006 12.3750002,0.562500008 Z"
                        />
                    </g>
                </g>
            </svg>
            <span class="text-sm lg:text-base">{{
                isAdding ? 'Adding...' : 'Add Somnia to MetaMask'
            }}</span>
        </button>

        <!-- Success notification -->
        <Transition
            enter-active-class="transition ease-out duration-200"
            enter-from-class="transform opacity-0 translate-y-2"
            enter-to-class="transform opacity-100 translate-y-0"
            leave-active-class="transition ease-in duration-150"
            leave-from-class="transform opacity-100 translate-y-0"
            leave-to-class="transform opacity-0 translate-y-2"
        >
            <div
                v-if="showSuccess"
                class="bg-white/10 backdrop-blur-sm border border-green-400/50 text-white font-semibold py-2 px-4 rounded-lg"
            >
                <span class="text-green-400">✓</span> Network added successfully!
            </div>
        </Transition>

        <!-- Error notification -->
        <Transition
            enter-active-class="transition ease-out duration-200"
            enter-from-class="transform opacity-0 translate-y-2"
            enter-to-class="transform opacity-100 translate-y-0"
            leave-active-class="transition ease-in duration-150"
            leave-from-class="transform opacity-100 translate-y-0"
            leave-to-class="transform opacity-0 translate-y-2"
        >
            <div
                v-if="errorMessage"
                class="bg-white/10 backdrop-blur-sm border border-red-400/50 text-white font-semibold py-2 px-4 rounded-lg max-w-xs text-center"
            >
                <span class="text-red-400">⚠</span> {{ errorMessage }}
            </div>
        </Transition>
    </div>
</template>

<style scoped>
/* Additional styles if needed */
</style>
