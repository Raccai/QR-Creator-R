<button on:click>
    <slot></slot>
</button>

<style>
	button {
		border-radius: 20px;
		border: none;
		padding: 7px 15px 7px 15px;
		background-image: linear-gradient(-60deg, #9448bc, #ffe250);
		color: white;
		font-weight: bold;
	}

	button:hover {
		transform: scale(1.05) perspective(1px);
	}

	button:active {
		background: white;
		border: 2px solid #9448bc;
		background: -webkit-linear-gradient(60deg, #9448bc, #ffe250);
  		-webkit-background-clip: text;
  		-webkit-text-fill-color: transparent;
	}
</style>