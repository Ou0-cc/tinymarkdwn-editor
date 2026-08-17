<script lang="ts">
    import './app.css';
    import { onMount } from 'svelte';
    import { ModeWatcher } from 'mode-watcher';
    import { Toaster } from '$lib/components/ui/sonner/index.js';
    import { provideIsMobile } from '$lib/hooks/is-mobile.svelte';
    import { init } from '@plausible-analytics/tracker';

    onMount(() => {
        init({
            domain: 'ou0.cc',
            endpoint: 'https://plausible.canine.tools/api/event',
            captureOnLocalhost: false,
            outboundLinks: true
        });
    });

    provideIsMobile();

    let { children } = $props();
</script>

<ModeWatcher />
<Toaster richColors closeButton position="bottom-right" />
{@render children?.()}