<script lang="ts">
	import { browser } from '$app/env';
	import type { CssClassType } from '$lib/types/css-class.type';
	import { defineCustomElement } from '$lib/utils/utils';
	import { onMount } from 'svelte';

	let cssClass: CssClassType = undefined;

	export { cssClass as class };

	export let autoHide = true;
	export let DrawerId: 'end' | 'start' | string | undefined = undefined;

	if (browser) {
		onMount(async () => {
			const IonMenuToggle = (await import('@ionic/core/components/ion-menu-toggle')).IonMenuToggle;

			defineCustomElement('ion-menu-toggle', IonMenuToggle);
		});
	}
</script>

<ion-menu-toggle auto-hide="{autoHide}" class="{cssClass}" menu="{DrawerId}" on:click>
	<slot />
</ion-menu-toggle>

<style>
</style>
