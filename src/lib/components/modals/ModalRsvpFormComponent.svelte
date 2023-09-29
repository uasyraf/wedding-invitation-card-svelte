<script>
	import { getModalStore } from '@skeletonlabs/skeleton';
	import googleMapsIcon from '$lib/images/icons8-google-maps-48.png'
	import wazeIcon from '$lib/images/icons8-waze-48.png'
	const modalStore = getModalStore();

	function oncloseButtonClicked() {
		modalStore.close();
	}

	function onGoogleMapsButtonClicked(event) {
		window.open('https://maps.app.goo.gl/1pjV4XiwuPcQ5VKa6');
	}
	
	function onWazeButtonClicked(event) {
		window.open('https://ul.waze.com/ul?preview_venue_id=66781211.667812108.22196514&navigate=yes&utm_campaign=default&utm_source=waze_website&utm_medium=lm_share_location');
	}

	// Base Classes
	const cBase = 'card p-4 shadow-xl space-y-4';
</script>

<!-- @component This example creates a simple form modal. -->


{#if $modalStore[0]}
	<div class="modal-example-form {cBase}">
		<div class="flex justify-center items-center mx-auto transition-[width] duration-200">
			<div class="btn-group-vertical">
				<button id="google-maps-button" type="button" on:click={onGoogleMapsButtonClicked}><img src="{googleMapsIcon}" alt="Open with Google Maps">&nbspGoogle Maps</button>
				<button id="waze-button" type="button" on:click={onWazeButtonClicked}><img src="{wazeIcon}" alt="Open with Waze">&nbsp&nbspWaze</button>
				<button id="close" type="button" on:click={oncloseButtonClicked}>
					<svg class="w-3 h-3" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 14 14">
						<path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="m1 1 6 6m0 0 6 6M7 7l6-6M7 7l-6 6"/>
					</svg>
				</button>
			</div>
		</div>
	</div>
{/if}

<style lang="postcss">
	.modal-example-form {
	}
</style>