<script setup>
// Simple hero component ready for your static background image
</script>

<template>
    <section class="featured-section relative w-full">
        <div
            class="max-w-[86rem] p-6 lg:py-24 not-odd:overflow-hidden mx-auto flex flex-col-reverse lg:grid lg:grid-cols-[3fr_4fr] grid-rows-[auto] auto-cols-[1fr] items-center gap-12"
        >
            <div class="flex flex-col gap-12 text-[16px] relative z-10">
                <h1 class="text-5xl font-black tracking-tight">JELLU TOKEN</h1>
                <p class="text-xl">
                    The wobble caught on. The memes got louder. The current grew stronger. Jelly
                    always best when shared.. What began as a playful side quest odyssey turned into
                    a full-on community.
                    <br />
                    <br />
                    Now, the JellyDevs are gave away their allocation: 69,999,995 $JELLU: back to
                    the community, within 69 days of a fair launch
                    <br />
                    <br />
                    And then the other 10% is to things that will help push $jellu to next level
                    through a newly formed DAO and fun things to increase expsoreu to the somnia
                    blockchain as the #1 somnia meme…
                </p>
                <div class="flex items-center gap-4">
                    <a
                        href="https://stargate.finance/?srcChain=base&srcToken=0x47636b3188774a3E7273D85A537b9bA4Ee7b2535&dstChain=somnia&dstToken=0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE
"
                        class="font-google-sans-code shadow-2xl w-fit rounded-full px-6 py-3 font-bold text-white text-lg mt-4 bg-cover bg-center bg-no-repeat border-0 hover:scale-105 transition-transform duration-300"
                        style="background-image: linear-gradient(225deg, #8e47ff 0%, #333aff 100%)"
                        >Bridge to Somnia</a
                    >
                    <a
                        href="https://somnex.xyz/#/swap/0x28bec7e30e6faee657a03e19bf1128aad7632a00/0xd5447af13a1df69add89e185155b20fb72d5e9a7"
                        class="font-google-sans-code shadow-2xl w-fit rounded-full px-6 py-3 font-bold text-white text-lg mt-4 bg-cover bg-center bg-no-repeat border-0 hover:scale-105 transition-transform duration-300"
                        style="background-image: linear-gradient(225deg, #00d4ff 0%, #0066ff 100%)"
                        >Buy $JELLU</a
                    >
                </div>
            </div>
            <div class="rounded-4xl overflow-hidden h-full w-full aspect-square relative z-10">
                <div class="h-full w-full relative overflow-hidden">
                    <img
                        class="h-full w-full object-cover bg-[50%] bg-cover m-auto absolute -inset-full"
                        src="/featured.jpg"
                    />
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped>
.featured-section {
    position: relative;
    isolation: isolate;
    background-image: url('/featured.jpg');
    background-position: center;
    background-size: cover;
}

.featured-section::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(225deg, rgba(142, 71, 255, 0.9), rgba(51, 58, 255, 0.9));
    pointer-events: none;
    z-index: 0;
}
</style>
