<script>
	import { Router, Link} from "svelte-routing";
	import Layout from "../Layout.svelte";

	document.body.className = "bg-gray-900 text-white"
	let imploreValue = "";
	let answerStream = false;
	let falseImplore = "now nao is getting my answer getting nao is my answer";
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
	<!-- <Router>
		<Link to="/instructions"><span class="w-10 h-10 absolute top-0 left-0"></span></Link>
	</Router> -->
	<!-- <img class="h-60 w-auto mt-5 rounded-3xl bg-gradient-to-b from-red to-black" src="https://t3.ftcdn.net/jpg/02/81/69/20/360_F_281692077_vntiPFFtvpENtzNUQH4nr4U48ydg5fPr.jpg" alt="AI">
	<div class="w-72 text-center relative bottom-12">
		<h1 class="w-64 mx-auto text-2xl font-light mt-3">Nao knows <span class="font-bold">EVERYTHING</span></h1>
		<p class="mt-3 font-light">Nao won't answer any questions and misbehave until you implore him! Try saying <span class="font-bold">`now nao is getting my answer`</span>.</p>
		<form on:submit={ask}>
			<input on:input={imploreInput} value={imploreValue} class="w-full mt-4 p-1 px-3 rounded-lg bg-black text-white focus:outline-none focus:outline-white" type="text" placeholder="Implore">
			<input class="w-full mt-1 p-1 px-3 rounded-lg bg-black text-white focus:outline-none" type="text" placeholder="Question">
			<div class="flex mt-4 overflow-hidden rounded-xl">
				<button type="submit" class="w-full font-light p-4 py-3 bg-red-800 text-white focus:outline-none">Ask</button>
				<button type="reset" on:click={reset} class="w-full font-light p-4 py-3 bg-black text-white focus:outline-none">Reset</button>
			</div>
		</form>
		{#if displayAnswer}
		<div class="my-5 border border-white py-5 px-5 rounded-lg font-medium text-xl">
			<p class="break-words">{displayAnswer}</p>
		</div>
		{/if} -->
		<p>Check back soon... it needs some debugging!</p>
</div>
</Layout>
