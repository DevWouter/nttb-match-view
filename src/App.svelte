<script lang="ts">
	import CaptureWebcam from "./CaptureWebcam.svelte";
	import ViewScore from "./ViewScore.svelte";
</script>

<style>
	.background{
		z-index: 10;
		position: absolute;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
	}
	.foreground{
		z-index: 100;
		position: absolute;
		left: min(10vh, 10vw, 30px); 
		bottom:  min(10vh, 10vw, 30px);
		width: 400px;
		max-width: 80vw;
	}
</style>

<main>
	<div class="background">
		<CaptureWebcam />
	</div>

	<div class="foreground">
		<div class="score">
			<ViewScore />
		</div>
	</div>
</main>
