<script lang="ts">
	import { browser } from '$app/env';
	import type { CssClassType } from '$lib/types/css-class.type';
	import { defineCustomElement } from '$lib/utils/utils';
	import { onMount } from 'svelte';

	let cssClass: CssClassType = undefined;

	export { cssClass as class };

	if (browser) {
		onMount(async () => {
			const IonItemGroup = (await import('@ionic/core/components/ion-item-group')).IonItemGroup;

			defineCustomElement('ion-item-group', IonItemGroup);
		});
	}
</script>

<ion-item-group class="{cssClass}">
	<slot />
</ion-item-group>

<style>
</style>
