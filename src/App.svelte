<script>
	import Header from "./Header.svelte";
	import Card from "./Card.svelte";
	import Button from "./Button.svelte";

	let active = false;
	let qrInput = "";
	let qrImage = "";
	
	let cssValues = {
		opacity: 0,
	};

	$: cssVarStyles = Object.entries(cssValues)
		.map(([key, value]) => `--${key}:${value}`)
		.join(";");

	const turnActive = () => {
		active = 0;
		cssValues.opacity = 0;

		if (qrInput == ""){
			return
		}

		setTimeout(() => (
			cssValues.opacity = 1,
			active = 1
		), 400);

		qrImage = `https://api.qrserver.com/v1/create-qr-code/?size=276x276&data=${qrInput}`;
	};
</script>

<main style={cssVarStyles}>
	<Card {active}>
		<div class="subheader-container">
			<div class="subheader">
				<input type="text" class="input" required="required" bind:value={qrInput}>
				<span class="label">Input URL or Text</span>
			</div>
		</div>
		<Button on:click = {turnActive}>Generate QR Code</Button>
		<div class="qr-display">
			<img src={qrImage} alt="" class="qr">
		</div>
	</Card>
	<Header />
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: auto;
	}

	.qr-display {
		opacity: var(--opacity);
		transition: opacity 0.2s 0.0001s ease;
	}

	.qr {
		width: 278px;
	}

	.subheader {
		position: relative;
		width: 280px;
		text-align: left;
	}

	.subheader .input {
		width: 100%;
		padding: 10px;
		border: 1px solid #9448bc;
		background-color: white;
		color: #9448bc;
	}

	.subheader .label {
		position: absolute;
		left: 0;
		padding: 10px;
		transition: all 0.3s ease;
		color: #9448bc;
	}

	.subheader .input:valid ~ span,
	.subheader .input:focus ~ span {
		transform: translateX(10px) translateY(-9px);
		font-size: 10px;
		padding: 3px;
		background-color: white;
		border-right: 1px solid #9448bc;
		border-left: 1px solid #9448bc;
	}

	.subheader .input:valid,
	.subheader .input:focus {
		outline: 1px solid #9448bc;
	}
</style>