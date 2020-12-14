<script>
    import Layout from "../Layout.svelte";
    import { Link } from "svelte-routing";
</script>
<Layout>
    <Link to="/"><span class="w-10 h-10 absolute top-0 left-0"></span></Link>
    <main class="m-auto text-white rounded-lg font-light text-sm">
        <img src="/minions.gif" alt="minions" class="rounded-lg">
        <p class="mt-2">You just discovered a secret page, you'll now know about the trick involved in project.</p>
        <div class="mt-5 flex flex-col space-y-5">
            <div>
                <p>Q. What is NaoAI ?</p>
                <p>-- NaoAI is a project which you can use to trick your frineds into thinking that they are talking to a super brilliant ai.</p>
            </div>
            <div>
                <p>Q. Origin of this project ?</p>
                <p>-- This project is not mine but a redesigned version of <a href="http://samsayssweetsounds.com/" target="_blank" class="underline">Sam Says Sweet Sounds</a>. I redesigned his project so that it can seem much more brilliant.</p>
            </div>
            <div>
                <p>Q. How to use it ?</p>
                <p>-- <a class="underline" href="https://www.youtube.com/watch?v=hvoXQkmFf30&t=265s" target="__blank">Here</a> is the video demonstration of his project.</p>
            </div>
        </div>
        <a class="text-center block mt-5 underline" href="https://github.com/41y08h/naoai" target="_blank">View on Github</a>
    </main>
</Layout>



<style>
    main {
		width: 500px;
		padding: 20px 25px;
		background-color: rgba(255, 255, 255, 0.25);
		backdrop-filter: blur(40px);
        -webkit-backdrop-filter: blur(40px);
	}
</style>