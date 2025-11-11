<script setup>
import { ref, onMounted, onBeforeUnmount, nextTick, watch } from 'vue'

const faqs = [
    {
        question: 'What is $JELLU?',
        body: [
            {
                type: 'text',
                text: '$JELLU is a culture-first memecoin and community hub on the Somnia Network—built to reward creators, collectors, and the wider community while sparking new on-chain culture.',
            },
        ],
    },
    {
        question: 'What chain is $JELLU on?',
        body: [
            {
                type: 'text',
                text: '$JELLU is available exclusively on the Somnia Network (EVM-compatible).',
            },
        ],
    },
    {
        question: 'How do I bridge to Somnia to get $JELLU?',
        body: [
            {
                type: 'text',
                text: 'Use the official Somnia bridge on Stargate or through CEXs like Binance.',
            },
            {
                type: 'text',
                text: '[Insert your official bridge URL and any approved options here]',
                classes: 'italic text-white/70',
            },
        ],
    },
    {
        question: 'Can I buy $JELLU on decentralized exchanges?',
        body: [
            {
                type: 'text',
                text: 'Yes. $JELLU will be tradable on Somnia-native DEXes.',
            },
            {
                type: 'link',
                href: 'https://somnia.meme/coin/0xd5447af13a1df69add89e185155b20fb72d5e9a7',
                label: 'somnia.meme listing',
            },
            {
                type: 'link',
                href: 'https://somnex.xyz/#/swap/0x0000000000000000000000000000000000000000/0xd5447af13a1df69add89e185155b20fb72d5e9a7',
                label: 'Somnex DEX pair',
            },
        ],
    },
    {
        question: 'Can I buy $JELLU on centralized exchanges?',
        body: [
            {
                type: 'text',
                text: 'Available soon.',
            },
        ],
    },
    {
        question: 'What is the official $JELLU contract address?',
        body: [
            {
                type: 'link',
                href: 'https://explorer.somnia.network/token/0xd5447aF13A1DF69Add89E185155b20fB72d5e9a7',
                label: '0xd5447aF13A1DF69Add89E185155b20fB72d5e9a7',
            },
        ],
    },
    {
        question: 'What is the total token supply of $JELLU?',
        body: [
            {
                type: 'text',
                text: '10,000,000,000 $JELLU.',
            },
        ],
    },
]

const openIndex = ref(0)

const bodyRefs = ref([])
const bodyHeights = ref([])

const setBodyRef = (el, index) => {
    if (el) {
        bodyRefs.value[index] = el
        bodyHeights.value[index] = el.scrollHeight
    }
}

const measureBody = (index) => {
    const el = bodyRefs.value[index]
    if (!el) return
    bodyHeights.value[index] = el.scrollHeight
}

const measureAll = () => {
    nextTick(() => {
        faqs.forEach((_, idx) => measureBody(idx))
    })
}

const toggle = (index) => {
    openIndex.value = openIndex.value === index ? -1 : index
    measureAll()
}

watch(openIndex, () => {
    measureAll()
})

onMounted(() => {
    measureAll()
    window.addEventListener('resize', measureAll)
})

onBeforeUnmount(() => {
    window.removeEventListener('resize', measureAll)
})
</script>

<template>
    <section class="flex w-full flex-col gap-6 bg-[#0E181E] p-6 sm:pt-24 pt-12 text-white sm:p-10">
        <!-- Card -->
        <div class="flex flex-col gap-6 mx-auto max-w-4xl bg-[#0f1b22] p-6 rounded-[2.5rem]">
            <header class="flex flex-col gap-2 text-center">
                <p class="text-sm font-semibold uppercase tracking-[0.45em] text-white/40">
                    JELLU — FAQs
                </p>
                <h2 class="text-3xl font-black sm:text-4xl">Frequently Asked Questions</h2>
            </header>
            <div class="flex flex-col gap-4">
                <div
                    v-for="(faq, index) in faqs"
                    :key="faq.question"
                    class="rounded-3xl border border-white/5 bg-[#15242b]"
                >
                    <button
                        type="button"
                        class="flex w-full items-center justify-between gap-4 px-5 py-4 text-left sm:px-7 sm:py-5"
                        :aria-expanded="openIndex === index"
                        :aria-controls="`faq-panel-${index}`"
                        @click="toggle(index)"
                    >
                        <span class="text-lg font-semibold sm:text-xl">{{ faq.question }}</span>
                        <svg
                            class="h-5 w-5 flex-none transform transition-transform duration-200"
                            :class="openIndex === index ? 'rotate-180 text-white' : 'text-white/60'"
                            viewBox="0 0 20 20"
                            fill="currentColor"
                            aria-hidden="true"
                        >
                            <path
                                fill-rule="evenodd"
                                d="M10 12.75a.75.75 0 0 1-.53-.22l-4-4a.75.75 0 0 1 1.06-1.06L10 10.94l3.47-3.47a.75.75 0 0 1 1.06 1.06l-4 4a.75.75 0 0 1-.53.22Z"
                                clip-rule="evenodd"
                            />
                        </svg>
                    </button>
                    <div
                        :id="`faq-panel-${index}`"
                        :ref="(el) => setBodyRef(el, index)"
                        class="overflow-hidden px-5 transition-[height] duration-500 ease-[cubic-bezier(0.33,1,0.68,1)] sm:px-7"
                        :style="{
                            height: openIndex === index ? `${bodyHeights[index] ?? 0}px` : '0px',
                        }"
                        :aria-hidden="openIndex !== index"
                    >
                        <div
                            class="flex flex-col gap-3 py-5 text-base leading-relaxed text-white/80 transition duration-300 ease-out"
                            :class="
                                openIndex === index
                                    ? 'opacity-100 translate-y-0'
                                    : 'opacity-0 -translate-y-1'
                            "
                        >
                            <template v-for="(item, itemIndex) in faq.body" :key="itemIndex">
                                <p v-if="item.type === 'text'" :class="item.classes ?? ''">
                                    {{ item.text }}
                                </p>
                                <a
                                    v-else-if="item.type === 'link'"
                                    class="text-sm font-semibold uppercase tracking-[0.2em] text-white hover:text-white/70 break-all max-w-full"
                                    :href="item.href"
                                    target="_blank"
                                    rel="noopener"
                                >
                                    {{ item.label }}
                                </a>
                            </template>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>
