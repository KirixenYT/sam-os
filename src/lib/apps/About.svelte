<script>
    import Titlebar from "$lib/components/Titlebar.svelte";
    import App from "$lib/components/App.svelte";
    import Logo from "$lib/components/Logo.svelte";
    import IconSvelte from '$lib/icons/IconSvelte.svelte'

    let title = "About"
</script>

<App>
        <Titlebar {title}/>
        <div class="content flex flex-col items-center justify-center">
            <Logo/>

            <span class="text-3xl font-semibold">sam-os</span>
            <span class="text-center text-sm">(random logo hehe lmao)</span>

            <a class="px-3 py-1 rounded bg-blue-500 text-white"
                href="https://github.com/kirixenyt" target="_blank" noreferrer>
                source code
            </a>

            <span class="text-base flex items-center">Made with Svelte.
                <IconSvelte />
            </span>
        </div>
</App>