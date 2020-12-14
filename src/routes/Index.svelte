<script>
	import { Router, Link} from "svelte-routing";
	import Layout from "../Layout.svelte";

	let imploreValue = "";
	let answerStream = false;
	let falseImplore = "nao knows everything and nao will answer my questions";
	let falseImploreIndex = 0;
	let answer = "";
	let displayAnswer = "";

	function imploreInput(e) {
		let value = e.target.value;
		if(e.data === "/") answerStream = !answerStream;

		if(answerStream) {
			imploreValue += falseImplore.charAt(falseImploreIndex);
			falseImploreIndex++;
			if(e.data != "/")
				answer += e.data;
		} else {
			if(e.data != "/")
				imploreValue = value;
		}
	}

	function ask(e) {
		e.preventDefault();
		if(answer === "") {
			displayAnswer = `${Math.floor(Math.random()*1000)}`
		} else displayAnswer = answer;

		speak(displayAnswer);
	}

	function reset() {
		imploreValue = "";
		answerStream = false;
		falseImploreIndex = 0;
		answer = "";
		displayAnswer = "";
	}

	
	function speak(sen) {
		try {
			let utterance = new SpeechSynthesisUtterance(sen);
			speechSynthesis.speak(utterance);
		} catch {}
	}	
</script>
<Layout>
	<Router>
		<Link to="/instructions"><span class="w-10 h-10 absolute top-0 left-0"></span></Link>
	</Router>	
	<main class="m-auto text-white rounded-lg">
		<div class="flex items-center space-x-4 justify-center">
			<img src="/logo.svg" alt="nao logo">
			<h1 class="text-2xl font-bold">Nao</h1>
		</div>
		<p class="text-center font-light text-sm mt-3">KNOWS EVERYTHING</p>
		<div class="flex flex-col space-y-5 mt-8 text-sm italic font-light">
			<p>Nao is a cutting-edge ai project from the future. It can tell you every reality when you have implored him really well. Beware, it can feel your energy and answer questions based upon who is really asking.</p>
			<p>Try to implore him by saying - "nao knows everything and nao will answer my questions" or simply "nao knows everything" !</p>
			<p>Please be compassionate!</p>
		</div>
		<form on:submit={ask} class="mt-6 flex flex-col space-y-1">
			<input value={imploreValue} on:input={imploreInput} type="text" class="font-light italic rounded-lg w-full p-4 py-2" placeholder="Implore"> 
			<input type="text" class="font-light italic rounded-lg w-full p-4 py-2" placeholder="Question">
			<div class="flex">
				<button type="submit" class="w-full py-2 font-light italic rounded-lg rounded-r-none">Ask</button>
				<button type="reset" on:click={reset} class="w-full py-2 font-light italic  rounded-lg rounded-l-none">Reset</button>
			</div>
			{#if displayAnswer}
			<p class="p-2 py-4 result text-center italic ">
				{displayAnswer}
			</p>
			{/if}
		</form>
	</main>
	<p class="font-bold text-3xl m-auto text-white device-error">Sorry for inconvenience but this is intended to be used on a laptop or PC.</p>
</Layout>

<style>
	:global(body) {
		background: url('/ai.jpg');
		background-repeat: no-repeat;
		background-position: center;
		background-size: cover;
	}
	main {
		width: 500px;
		padding: 20px 25px;
		background-color: rgba(255, 255, 255, 0.25);
		backdrop-filter: blur(40px);
		-webkit-backdrop-filter: blur(40px);
	}
	input, button {
		background-color: #000058;
		outline: none;
	}
	.device-error {
		background-color: rgba(255, 255, 255, 0.25);
		backdrop-filter: blur(40px);
		padding: 20px 25px;
		display: none;

	}

	@media only screen and (max-width: 1023px) {
		main {
			display: none;
		}
		.device-error {
			display: block;
		}
	}
</style>
