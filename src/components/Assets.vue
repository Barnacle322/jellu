<template>
    <section
        class="relative isolate w-full overflow-hidden bg-[#0e181e]"
        aria-labelledby="assets-title"
    >
        <div
            class="absolute inset-0 -z-10 bg-cover bg-center opacity-80"
            style="background-image: url('/assetsbg.jpg')"
            aria-hidden="true"
        ></div>
        <div class="absolute inset-0 -z-10 bg-[#0e181e]/70"></div>
        <div
            class="mx-auto flex w-full max-w-6xl flex-col items-center gap-8 px-6 py-16 sm:flex-row sm:justify-between sm:gap-12 sm:py-24"
        >
            <div class="flex flex-1 justify-center">
                <img
                    class="size-64 object-contain drop-shadow-lg"
                    src="/assets.png"
                    alt="JELLU mascot"
                />
            </div>
            <div
                class="flex max-w-xl flex-1 flex-col items-center text-center sm:items-start sm:text-left"
            >
                <p class="text-sm font-semibold uppercase tracking-[0.45em] text-white/60">
                    Creator Kit
                </p>
                <h3 id="assets-title" class="mt-2 text-3xl font-black text-white sm:text-4xl">
                    JELLU Asset Vault
                </h3>
                <p class="mt-4 text-base leading-relaxed text-white/80 sm:text-lg">
                    Logos, motion packs, sticker sheets, and all the wobble-worthy visuals you need
                    to ship JELLU content fast.
                </p>
                <div class="mt-8 flex flex-col gap-3 sm:flex-row sm:gap-4">
                    <a
                        class="inline-flex items-center justify-center rounded-full border border-white/40 bg-white/10 px-6 py-3 text-sm font-semibold uppercase tracking-[0.2em] text-white backdrop-blur transition hover:border-white hover:bg-white hover:text-[#0e181e]"
                        href="https://giphy.com/channel/jellufun"
                        target="_blank"
                        rel="noopener"
                    >
                        Explore GIPHY
                    </a>
                    <a
                        class="inline-flex items-center justify-center rounded-full bg-white px-6 py-3 text-sm font-semibold uppercase tracking-[0.2em] text-[#0e181e] shadow-lg transition hover:shadow-xl"
                        href="https://drive.google.com/drive/folders/1DPpelGHBKTSn9gK5VYRaH6adB1jeWy4J"
                        target="_blank"
                        rel="noopener"
                    >
                        Download Assets
                    </a>
                </div>
            </div>
        </div>
    </section>
</template>
