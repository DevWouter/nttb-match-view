<script lang="ts">
    var mode: "instructions" | "display" = "instructions";
    var stream: MediaStream;
    var lastError = undefined;

    async function startScreenCapture() {
        mode = "display";
        lastError = undefined;
        if ((navigator.mediaDevices as any).getDisplayMedia) {
            try {
                stream = await (navigator.mediaDevices as any).getDisplayMedia({
                    video: true,
                    audio: true,
                });
                const videoEL = document.querySelector(
                    "video"
                ) as HTMLVideoElement;

                videoEL.srcObject = stream;
            } catch (err) {
                mode = "instructions";
                lastError = err;
            }
        } else {
            mode = "instructions";
            lastError = new Error("Browser ondersteunt getDisplayMedia niet");
        }
    }

    async function startWebcamCapture() {
        mode = "display";
        lastError = undefined;
        if (navigator.mediaDevices.getUserMedia) {
            try {
                stream = await navigator.mediaDevices.getUserMedia({
                    video: true,
                });
                const videoEL = document.querySelector(
                    "video"
                ) as HTMLVideoElement;
                videoEL.srcObject = stream;
            } catch (err) {
                mode = "instructions";
                lastError = err;
            }
        } else {
            mode = "instructions";
            lastError = new Error("Browser ondersteunt getUserMedia niet");
        }
    }
</script>

<style>
    .container {
        width: 100%;
        height: 100%;
        display: grid;
        overflow: clip;
        place-items: center;
    }

    video {
        min-width: 100%;
        min-height: 100%;
        align-self: center;
    }
    .instructions {
        border: 1px solid silver;
        padding: 12px;
        border-radius: 6px;
        box-shadow: 0 0 5px silver;
        max-width: 500px;
    }
    .capture-buttons{
        display: grid;
        margin: auto;
        grid-template-columns: 1fr 1fr;
        gap: 8px;
    }
</style>

<div class="container">
    {#if mode == 'display'}
        <video autoplay id="videoElement">
            <track kind="captions" />
            <p>Hello</p>
        </video>
    {:else if mode == 'instructions'}
        <div class="instructions">
            <h1>NTTB Wedstrijd overlay</h1>
            <p>
                Met deze site kan jij op jouw club een wedstrijd tonen op een TV
                terwijl onderin de stand via de NTTB app live wordt ingevuld.
            </p>

            <p>
                Maak je gebruik van een aangesloten webcam of gebruik je
                software?
            </p>
            <div class="capture-buttons">
                <button on:click={startWebcamCapture}>Webcam</button>
                <button on:click={startScreenCapture}>Software</button>
            </div>

            {#if lastError}
                <div class="error">
                    <p>Helaas, er trad een fout op. Probeer het opnieuw.</p>
                    <code>{lastError}</code>
                </div>
            {/if}
        </div>
    {/if}
</div>
