<script>
    import Titlebar from "$lib/components/Titlebar.svelte";
    import App from "$lib/components/App.svelte";

    import IconPlay from '$lib/icons/IconPlay.svelte'
    import IconPause from '$lib/icons/IconPause.svelte'
    import IconOpen from '$lib/icons/IconOpen.svelte'

    let title = "Music";

    let paused = true;
    let currentTime = 0;
    let duration = 0;

    function format(time) {
        if (isNaN(time)) return "...";

        const minutes = Math.floor(time / 60);
        const seconds = Math.floor(time % 60);

        return `${minutes}:${seconds < 10 ? `0${seconds}` : seconds}`;
    }

    const AppDetails = {
        // height: "27rem",
        width: "21rem",
    };
</script>

<App {...AppDetails}>
    <Titlebar {title} />

    <div class="content flex flex-col mt-8 gap-2 p-2 h-fit">
        <img src="/hqdefault.avif" alt="artwork" class="rounded-lg">
        <audio
            src="/regression.mp3"
            bind:currentTime
            bind:paused
            bind:duration
        />

        <div class="flex items-center flex-col w-full">
            <div class="info flex justify-between items-center w-full">
                <span class="title font-semibold text-base">Regression</span>
                <span class="artist text-sm">Honkai Impact 3rd</span>
            </div>

            <div class="progress_time flex items-center w-full gap-2">
                <span class="text-sm">{format(currentTime)}</span>

                <div class="progress flex items-center w-full bg-[gainsboro] rounded h-1">
                    <div
                        class="progessbar rounded bg-blue-500 h-full"
                        style="--progress: {currentTime / duration}%"
                    />
                </div>

                <span class="text-sm">{format(duration)}</span>
            </div>

            <div class="buttons flex gap-2 mt-3">
                <button class="text-blue-500"
                    on:click={() => paused = !paused } >
                    {#if paused}
                        <IconPlay />
                    {:else}
                        <IconPause />
                    {/if}
                </button>

                <a class="text-blue-500"
                    href="https://www.youtube.com/watch?v=VrcB9PJ22F0"
                    target="_blank"
                >
                <IconOpen />
                </a>
            </div>
        </div>
    </div>
</App>

<style>
    .progessbar { width: calc(100 * var(--progress)); }
</style>