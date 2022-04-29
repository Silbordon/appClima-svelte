<script lang="ts">
import Weather from "./components/Weather.svelte";

</script>

<main class="text-center container">
	<h2 class="fs-1 mt-5 pt-4">Weather App!</h2>
	<hr>
	<Weather/>
</main>

<style>
.container{
	background-color: rgba(78, 172, 147, 0.338);
	height: 40vh;
	border-radius: 10px;
	box-shadow: 1px 6px 5px #2140475d;
}
</style>