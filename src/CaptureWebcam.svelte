<script lang="ts">
    import { onMount } from "svelte";

    onMount(() => {
        var video = document.querySelector("#videoElement") as HTMLVideoElement;

        if (navigator.mediaDevices.getUserMedia) {
            navigator.mediaDevices
                .getUserMedia({ video: true })
                .then(function (stream) {
                    video.srcObject = stream;
                })
                .catch(function (err) {
                    console.error(err);
                });
        }
    });
</script>

<style>
    .container {
        background-color: red;
        width: 100%;
        height: 100%;
        display: grid;
        overflow: clip;
    }

    video {
        min-width: 100%;
        min-height: 100%;
        align-self: center;
    }
</style>

<div class="container">
    <video autoplay="true" id="videoElement">
        <track kind="captions" />
        <!-- Some comment-->
    </video>
</div>
