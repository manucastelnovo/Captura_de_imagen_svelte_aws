<script>

	let files;
	let videoRef;
	let frame;
	let stream;
	let track;
	let screenList=[];
	let container;
	

	const constraints = {
		audio:true,
		video:{ height:200,width:200
  }
}
		
	

	async function init(){

		try {
			stream = await navigator.mediaDevices.getUserMedia(constraints);
			videoRef.srcObject = stream;
			
			
			// handleSuccess(stream);
			
			console.log(stream)
		} catch (error) {
			console.error(error)
		}
	}
	init()

	async function getFrame() {

		track = stream.getVideoTracks()[0]
		const imageCapture = new ImageCapture(track);
		const bitmap = await imageCapture.grabFrame();
		screenList.push(bitmap);

		container.innerHTML = '';
		screenList.forEach(element => {
			let child = document.createElement('canvas');
			child.width=element.width;
			child.height=element.height;
			child.classList.add('screen');
			let context = child.getContext('2d');
			context.drawImage(element,0,0);
			container.appendChild(child);
		});
		console.log(screenList)
	}
</script>



<style>
	:global(body){
		background-color: white;
		color: blue;
	}

	:global(:root){
		--theme-color:purple;
	}

	:global(body.dark-mode){
		background-color: #1d3040;
		color: #bfc2c7;
	}

	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	main img {
		width: 30%;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

	.screen{
		display: flex;
		flex-direction: row;
		gap:20px;
		justify-content: center;
		flex-wrap: wrap;
	}
</style>

<main>

	<input type="file" bind:files/>
	
	{#if files && files[0]}
    <p>
        {files[0]}
		
    </p>
	<img src={URL.createObjectURL(files[0])} alt="">
	{/if}


<video  bind:this={videoRef} autoplay={true}>
</video>

<button on:click={getFrame}>
	get frame
</button>


<div bind:this={container} class="screen">

	<!-- <canvas id={screen.id} width="200" height="100"/> -->

</div>









</main>