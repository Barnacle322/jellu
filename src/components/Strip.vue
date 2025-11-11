<script setup>
// Simple hero component ready for your static background image
</script>

<template>
    <section
        class="relative flex gap-12 w-full overflow-hidden bg-[#182930] py-3 font-google-sans-code text-sm tracking-wider font-extralight"
        aria-label="JELLU THE MEME marquee"
    >
        <div
            v-for="i in 2"
            class="inline-flex items-center gap-12 whitespace-nowrap animate-[strip-marquee_24s_linear_infinite]"
            aria-hidden="true"
        >
            <span class="uppercase text-[#f2f7ff]">🪼 JELLU THE MEME</span>
            <span class="uppercase text-[#f2f7ff]">🪼 JELLU THE MEME</span>
            <span class="uppercase text-[#f2f7ff]">🪼 JELLU THE MEME</span>
            <span class="uppercase text-[#f2f7ff]">🪼 JELLU THE MEME</span>
            <span class="uppercase text-[#f2f7ff]">🪼 JELLU THE MEME</span>
            <span class="uppercase text-[#f2f7ff]">🪼 JELLU THE MEME</span>
            <span class="uppercase text-[#f2f7ff]">🪼 JELLU THE MEME</span>
            <span class="uppercase text-[#f2f7ff]">🪼 JELLU THE MEME</span>
        </div>
    </section>
</template>

<style>
@keyframes strip-marquee {
    from {
        transform: translateX(0);
    }
    to {
        transform: translateX(-100%);
    }
}
</style>
